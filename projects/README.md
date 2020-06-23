# CDE-Malmö projects

## Completed projects

- [Dockerize Repo Tool](https://github.com/CDE-Malmo/repo-dockerized) - So that anyone can start using Repo on their machine without messing around.

- [JeGeRe](JeGeRe.md) - How to setup a test environment for Jenkins, Gerrit and the Repo tool.

## Project ideas

### Demo tool chain dockerized on your machine
Test environment on your machine.

### Jenkins multibranch pipelines for Repo and Gerrit
Take care of a multi git repository product (using the repo tool) in a good way using Jenkins.
Building each repo separately or the actual product (manifest repo) is trivial (build trigger on changes on that repo). The challenge is how to trigger the manifest repo build whenever a change in any sub-repo is made.
And, at the same time, the actual change needs to be pulled from the ready/for branches in Gerrit.

The challenges:
- Trigger product build on a change to any subrepo, and how do we know what repos?
- When building the product, pull down the change set from Gerrit for that subrepo.

### Eiffel
Setup a demo environment using Eiffel; Maybe Jenkins, Gerrit, RabbitMQ and/or something else. 
