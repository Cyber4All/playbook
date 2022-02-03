# CircleCI

# Dates: January 28, 2022

# Instructor: Christopher Wagner

## What is CircleCI?

## CircleCI Console

*Include Picture*

## CircleCI Concepts

### Projects

### Configuration

### User Types

### Pipelines

## Config.yml

### YAML Syntax

*Include Diagram*

### Orbs

### Commands

### Executors

### Jobs

### Workflows

## Demo Example

```YAML
version: 2.1

executors:
  go-exec:
    docker:
      - image: cimg/base:2022.01
    working_directory: ~/test-app

  test-exec:
    docker:
      - image: cimg/node:17.0.1
    working_directory: ~/test-app

orbs:
  node: circleci/node@5.0.0
  docker: circleci/docker@2.0.1
  aws-cli: circleci/aws-cli@2.0.3

commands:
  docker-setup:
    description: "Installs and logs into docker"
    parameters:
      job: 
        default: ""
        description: |
          "Job command is being run from"
        type: string
    steps:
      - setup_remote_docker
      - docker/install-docker
      - run: 
          command: | # verifying and using parameters
            if [ "<<parameters.job" = "" ]; then
              echo "Param not set"
              circleci-agent step halt
            fi
            echo "Command run from <<parameters.job>>"
      - run:
        name: Docker login 
        command: docker login -u "${DOCKER_USERNAME}" -p "${DOCKER_PASSWORD}" # using context variables

jobs:
  endpoint-testing:
    executor: test-exec
    steps:
      - checkout # checks out source code to path (working_directory)
      - node/install-packages # using an orb's command
      - run:
          command: npm run test # run endpoints with npm

  app-build:
    executor: go-exec
    steps:
      - checkout
      - docker-setup # using a command
      - docker/build: 
          image: "cyber4all/test-app" # default tag is $CIRCLE_SHA1
      - run:
          name: Save docker build
          command: docker save -o "dockerbuild" "cyber4all/test-app:$CIRCLE_SHA1" # saves build image as a .tar
      - persist_to_workspace: # workspaces are created for each workflow where data can be saved and loaded
          root: . # relative path to workspace
          paths:
            - dockerbuild # files being attached

  deploy-app:
    executor: go-exec
    steps: 
      - checkout
      - docker-setup
      - aws-cli/install
      - aws-cli/setup:
          aws-access-key-id: AWS_ECS_AccessKey # passing context variables as parameters for orb command
          aws-region: AWS_REGION_N_VA
          aws-secret-access-key: AWS_ECS_SecretKey
          version: "1"
      - attach_workspace: # loads workspace data (.tar file from app-build)
          at: ~/test-app/
      - run:
          name: Load docker build
          command: docker load -i "dockerbuild"
      - run:
          name: Check unique tag
          command: | # verify using curl request
            if curl --silent -f -lSL "https://index.docker.io/v1/repositories/cyber4all/test-app/tags/$(./version.sh -r)" > /dev/null; then
              echo "$(./version.sh -r) already exists in dockerhub"
              circleci-agent step halt
              exit 1
            fi
      - run: docker tag "cyber4all/test-app:$CIRCLE_SHA1" "cyber4all/test-app:$(./version.sh -r)"
      - docker/push:
          image: "cyber4all/test-app"
          tag: "$(version.sh -r)"
      - run:
          name: "Deploy to ECS"
          command: |
            NEW_TASK=$(aws ecs describe-task-definition --region us-east-1 --task-definition 'test-app' --output json | jq --arg IMG "cyber4all/test-app:$(version.sh -r)" '.taskDefinition.containerDefinitions[0].image=$IMG')
            aws ecs register-task-definition \
                --family 'test-app' \
                --task-role-arn ecsTaskExecutionRole \
                --execution-role-arn ecsTaskExecutionRole \
                --network-mode 'awsvpc' \
                --cli-input-json "$(echo $NEW_TASK)"

workflows:
  testing:
    - docker/hadolint:
        dockerfiles: Dockerfile:Dockerfile.dev
        executor-class: medium
        filters:
          branches:
            ignore:
              - /main/
              - /hotfix/
              - /releases/
    - endpoint-testing:
        filters:
          branches:
            ignore:
              - /releases/

  deploying:
    - app-build:
        context:
          - DockerHub
        requires:
          - docker/hadolint
          - endpoint-testing
        filters:
          branches:
            only:
              - /releases/
    - deploy-app:
        context:
          - AWS
          - DockerHub
        requires:
          - app-build
        filters:
          branches:
            only:
              - /releases/
```