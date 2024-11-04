# DevOps Assigment 2 - GitHub Actions & DockerHub

## Description of Workflow

  The workflow defined in build.yaml starts with defining when it is run, which is whenever anything is pushed to the 'main' branch of the repository. The workflow has read permissions only, as it is not editing the repo itself. It then builds the application, running on the latest version of ubuntu. It pulls down the checkout@v3 code from it's own repo to be utilized in the workflow and sets up a JDK for java. 
  
  Gradle is then run, first editing the ./gradlew file to have execute permissions and then building it. The Jar file located in the repo is then copied and moved to the ./app folder to be run alongside the Dockerfile. The docker image created from the Dockerfile is then built, running on ubuntu as well. It uses a predefined Docker Buildx application, accessed from a repo. In order to log in and push to the specified container on dockerhub.
  
  The username and access token are accessed via repository secrets, to keep them secure and hidden from public view. This logs into the specified Docker account and then pushes to the container defined on the very last line. In my case, it is pushing to the wsudwoolard/woolard-wopro-service container, using my personal username and access token. The end result is a new docker image being pushed to my docker container, each time a change is made to the main branch of the repository.

## Link to DockerHub Repository
[DockerHub - `WOOLARD-WOPro-Service`](https://hub.docker.com/repository/docker/wsudwoolard/woolard-wopro-service/general)

## Link to GitHub Actions Run Results Summary
[Link to **working** workflow run results](https://github.com/WSU-kduncan/devops-assignment-2-3-Ciriden/actions/runs/11655497836)
