# Jenkins & Gerrit & Repo Project

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

## How to setup Jenkins

We are using https://github.com/CDE-Malmo/praqma-jenkins-casc. 
Follow instructions from [README.md](https://github.com/CDE-Malmo/praqma-jenkins-casc/blob/master/README.md)
