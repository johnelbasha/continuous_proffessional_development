# Intro

I decided to document my learning journey in different areas of tech. Sharing this repository will give you insights to learning goals that working towards. It will also let you see what things I've completed and review my learning notes.

# Outline

My learning areas are shown in the section `Prioritised Learning Areas`. `Detailed Learing Goals` contains goals I am currently working towards. Files within `/learning_notes` document my learning as I progress through my plan. `backlog.md` is used to capture questions and ideas as they immerge for review and consideration at a later stage.

# Prioritised Learning Areas

Area                    Priority
-----------------------------------------
Docker                  1
Kubernetes              2
Database Querying       3
Rake tasks              4
React                   5
Node                    6

# Detailed Learning Goals

Learning Area: Docker

Timeline: By 13th May 2022

Actions:

1. Read through `Dockerfile` definitions for several of EdgePetrol's rails microservices.
2. Read through`docker-compose.yml` in `edgepetrol-rest-proxy` codebase, as this explains how multiple docker containers should be run alongside each other, as well as the dependencies between those containers, any ports that are forwarded from docker to localhost and potentially any volumes that need to be mounted from localhost into the docker container.
3. Get comfortable with mounting volumes inside docker containers so that your code is being run, rather than the code that was compiled into a docker image .
```
admin-service:
    # image: 770537037907.dkr.ecr.eu-west-1.amazonaws.com/admin-service:latest
    build:
      context: ../admin-service
      args:
        GITHUB_API_TOKEN: <your-github-token-goes-here>
    volumes:
      - ../admin-service/:/admin-service
```
4. Make a minimal rails application (even just hello world). Make your rails app dependent on a postgresql database and an instance of redis. Create a Dockerfile that will bundle your rails app into a docker image. Write a docker-compose.yml file that defines 3 services; your dockerised rails app, a postgresql container and a redis container. Start the composition locally (docker-compose up) and verify that your app can be reached on your localhost and that it can successfully communicate with the postgresql and redis containers.