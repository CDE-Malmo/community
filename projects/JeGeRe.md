# Jenkins & Gerrit & Repo Project

## What's this project about?

We have noticed that Jenkins, Gerrit and Repo tool isn't an unlikely tool set at companies, but there are some challenges to make it play well together.

This project is about describing how to setup a test environment for this.

## How to set up docker host

```
sudo -iu ubuntu
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo apt-key fingerprint 0EBFCD88
sudo add-apt-repository    "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) \
  stable"
sudo apt-get update
sudo apt-get install docker-ce
sudo curl -L "https://github.com/docker/compose/releases/download/1.25.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
sudo systemctl enable docker
sudo systemctl start docker
sudo usermod -aG docker $USER
exit
sudo -iu ubuntu
```

## How to setup Gerrit

We are using https://github.com/GerritCodeReview/docker-gerrit.

- `sudo -iu ubuntu`
- Create `docker-compose.yml` file, change external port from 8080 to 80.
- `docker-compose up -d`
- Generate ssh key pair, add public key to user
- Create new repo
- Open port 29418
- scp -i [private key for repo] -p -P 29418 [user]@[gerritserver]:hooks/commit-msg .git/hooks/


## How to setup Jenkins

We are using https://github.com/CDE-Malmo/praqma-jenkins-casc.
Follow instructions from [README.md](https://github.com/CDE-Malmo/praqma-jenkins-casc/blob/master/README.md)

## Installing Repo tool

From: [installing-repo](https://source.android.com/setup/build/downloading#installing-repo)
- Make sure that you have a bin/ directory in your home directory and that it's included in your path:
```
mkdir ~/bin
PATH=~/bin:$PATH
```
- Download the Repo Launcher and ensure that it's executable:
```
curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
chmod a+x ~/bin/repo
```
- [ssl problems](https://stackoverflow.com/questions/26646741/cannot-get-https-gerrit-googlesource-com-git-repo-clone-bundle)

### Setting work environment

**Creating repos**

- Create 1 manifest repo and 2 source repos
- In the manifest repo, create a `default.xml` file pointing to the other two repos.

```
<?xml version="1.0" encoding="UTF-8"?>
<manifest>
  <remote name="origin" fetch="http://35.228.235.101/" revision="master" />
  <default revision="master" remote="origin" />
  <project path="sub/one" name="jegere-sub1" />
  <project path="sub/two" name="jegere-sub2" />
</manifest>
```

- `repo init -u http://35.228.235.101/jegere`
- `repo sync`


