# Github Actions

![GithubActions](/images/logo.png)

## What is Github Actions

GitHub Actions is a powerful automation tool provided by GitHub, a web-based hosting service for version control using Git. It allows you to define custom workflows and automate various tasks within your software development lifecycle. With GitHub Actions, you can build, test, and deploy your code directly from your GitHub repositories.

![whatisgithub](/images/Git-Hub-Actions.jpg)

## Overview of Github Actions

GitHub Actions is a continuous integration and continuous delivery (CI/CD) platform that allows you to automate your build, test, and deployment pipeline. You can create workflows that build and test every pull request to your repository, or deploy merged pull requests to production.

GitHub Actions goes beyond just DevOps and lets you run workflows when other events happen in your repository.

For example, you can run a workflow to automatically add the appropriate labels whenever someone creates a new issue in your repository.

GitHub provides Linux, Windows, and macOS virtual machines to run your workflows, or you can host your own self-hosted runners in your own data center or cloud infrastructure.

## Components of Github Actions

GitHub Actions consists of several key components that work together to enable automation and workflow execution. These components include:

* **Workflows**: Workflows are the core component of GitHub Actions. They are defined using YAML files and represent a set of steps and actions that execute in response to specific events or triggers. Workflows define the automation logic for your software development processes.

* **Events and Triggers**: Workflows are triggered by specific events that occur within a GitHub repository. Events can include actions such as pushing to a branch, creating or closing a pull request, or scheduling a specific time interval. Triggers determine when a workflow should start.

* **Jobs**: Workflows can contain one or more jobs. Jobs represent a set of steps that execute on the same runner, which is the execution environment for the workflow. Jobs can run concurrently or sequentially, depending on the configuration.

* **Steps**: Steps are individual units of work within a job. Each step performs a specific action or task, such as running a shell command, invoking an action, or interacting with external services. Steps define the order in which actions are executed.

* **Actions**: Actions are standalone units of work that can be reused across different workflows. They are defined in YAML files or Docker containers and encapsulate a specific task or set of operations. Actions can be created by the community or provided by third-party vendors, and they can be used directly within workflows.

* **Runners**: Runners are the compute resources on which jobs and steps in workflows are executed. GitHub provides hosted runners that run workflows on virtual machines in the GitHub Actions infrastructure. You can also set up your own self-hosted runners on your own infrastructure.

* **Environment Variables**: GitHub Actions allows you to define and use environment variables within your workflows. These variables can store information such as access tokens, API keys, or custom configuration values. They can be set at the workflow, job, or step level.

* **Secrets**: Secrets are encrypted variables that can be used to store sensitive information, such as credentials or private keys. Secrets are securely stored and can be accessed by workflows during execution. They are typically used to authenticate with external services or protect sensitive data.

![components](/images/githubconcept.png)

## How GitHub Actions work?

* Github Actions is fully integrated into the Github. 

* As described in the above concepts, it mainly consists of workflows that are stored in the git repository (.github/workflows/). 

* Workflows are typically triggered by events such as PR, Issues, Commits in the repository or it can also be triggered from the external events using repository webhooks. 

* When the workflow is triggered, the runner picks up the job and executes one by one. The job consists of steps (with an action) that perform a unit of work in the workflow.

## Create a Workflow in the Github Repository

* To get started using GitHub Actions, we need to add a folder to the root of the GitHub repository.

.github/workflows  , Manually or you can follow the steps to create using action button.

* We can create a workflow using Actions button in the Github.(If you dont have an Github account create one by clicking on the following link. https://github.com/ )

* Create an new repository in the account by clicking the **NEW** button in the left-side menu bar

![create](/images/create.png)

* Give the Repository name and keep the repo public and click on create repository.

![create1](/images/create1.png)

* Click on the **Actions** in the repository.As a next page appears click on **set up a workflow yourself**

![create2](/images/create2.png)

![create3](/images/create3.png)

* You can give the name of the workflow what ever you want but the file should be in the format of .yml/yaml.

![create4](/images/create4.png)

### Example Workflow

* 1.Lets run a simple hello-world workflow and see the results.

Paste the above yaml syntax in the demo.yml

```

name: hello-world
on: push
jobs:
  my-job:
    runs-on: ubuntu-latest
    steps:
      - name: my-step
        run: echo "Hello World!"

```

* **name**: hello-world: This line sets the name of the workflow as "hello-world". It is used to identify the workflow in the GitHub Actions dashboard.

* **on**: push: This line specifies that the workflow will be triggered when a push event occurs in the repository. In other words, whenever code changes are pushed to any branch of the repository, this workflow will be executed.

* **jobs**: This keyword starts the definition of the jobs section, which contains one or more jobs that will be executed as part of the workflow.

* **my-job**: This line defines the name of the job as "my-job". A job is a unit of work that can consist of multiple steps.

* **runs-on**: ubuntu-latest: This line specifies that the job will run on a GitHub-hosted runner with the latest version of the Ubuntu operating system. The runner provides the execution environment for the job.

* **steps**:: This keyword starts the definition of the steps section within the job. Steps define the individual tasks or actions to be performed.

* **-name**: my-step: This line defines the name of the step as "my-step". It helps identify the step in the workflow execution log.

* **run**: echo "Hello World!": This line specifies the command to be executed in the step. In this case, the echo command is used to print the message "Hello World!" to the console.

So, when a push event occurs in the repository, this workflow will be triggered. It will run a single job named "my-job" on an Ubuntu runner. Within the job, there is a single step named "my-step" that executes the command echo "Hello World!". As a result, the workflow will print the "Hello World!" message in the workflow execution log

![work](/images/work1.png)

* 2.Once u have pasted the code click on the commit changes and give the Description.

![work](/images/work2.png)

* This Process has started Github Action workflow

### Check Results

* One can check the results by clicking the Action tab.

![result](/images/result.png)

* In this page you can see the workflow and runs of the workflow.

* You can check the logs and result of workflow by clicking the workflow run from right side bar(Create demo.yml) .

![result](/images/result1.png)

![result](/images/result2.png)

## CI/CD Pipeline using Git Actions

**Continuous Integration (CI):**

Continuous Integration is a software development practice where developers frequently integrate their code changes into a shared repository. After each integration, an automated build and test process is triggered to verify that the changes haven't introduced any bugs or conflicts. The goal of CI is to detect and fix integration issues early in the development cycle.

**Continuous Deployment (CD):**

Continuous Deployment is an extension of Continuous Integration where code changes that pass automated tests are automatically and continuously deployed to production or a live environment without manual intervention. The aim of CD is to streamline the release process and ensure that new features and bug fixes are delivered to end-users rapidly and reliably.

**CI/CD Pipeline:**

A CI/CD Pipeline is an automated sequence of steps that code changes go through, from version control to production deployment. It typically includes building the code, running tests, packaging, and deploying to various environments. The pipeline ensures consistency and efficiency in the software development and deployment process.

### Build CI/CD Pipeline Using GitHub Actions

Let's create a CI/CD Pipeline using GitHub Actions and using that workflow how we can automate process
of build and push docker image to docker hub.

* Here we build an Project in Springboot and Push the code to Github.

* Using Github Action tab we will create a workflow for CI/CD.

* Using CI/CD actions we Perform Build and Test the code , Create Docker image of my Application and Push the Docker image to DockerHub.

**Step 1:** Create a new Springboot Starter project with maven and having an java version 8.Add Spring web dependencies.

![java](/images/java1.png)

![java](/images/java2.png)

**Step 2:** Go to main class and write an endpoint like shown in a image.

![java](/images/java3.png)

### Pushing Code to Github Repository

* You can create an new repository and push the code to the Github.

* Go to the terminal (make sure you are in the correct directory) in STS an execute the commands.

* Intialize the github 

```

git init

```

![push](/images/push.png)

* Check the status 

```

git status

```

* Add src and pom.xml file

```

git add src

git add pom.xml

```

![push](/images/push1.png)

![push](/images/push2.png)

* Commit the code with some message to branch master and add origin using the repository link.
  execute the command one by one

```

git commit -m "code"

```

```

git branch -M master

```

```

git remote add origin "Repositorylink"

```

![push](/images/push3.png)

* Finally Push the code to the master

```

git push -u origin master

```

![push](/images/push4.png)

* You can check the code has been pushed to master 

![push](/images/push5.png)

### Create Workflow

* Now go to Action button and create a workflow,and paste the code in the .yaml file and commit changes.

```

# This workflow will build a Java project with Maven, and cache/restore any dependencies to improve the workflow execution time
# For more information see: https://help.github.com/actions/language-and-framework-guides/building-and-testing-java-with-maven

name: project cicd flow

on:
  push:
    branches: [ master ]
  pull_request:
    branches: [ master ]

jobs:
  build:

    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v2
    - name: Set up JDK 1.8
      uses: actions/setup-java@v1
      with:
        java-version: '1.8'
        distribution: 'adopt'
        cache: maven
    - name: Build with Maven
      run: mvn clean install

    - name: Build & push Docker image
      uses: mr-smithers-excellent/docker-build-push@v5
      with:
        image: sharan7898/github-action
        tags: latest
        registry: docker.io
        dockerfile: Dockerfile
        username: ${{ secrets.DOCKER_USERNAME }}
        password: ${{ secrets.DOCKER_PASSWORD }}


```

### Explainantion

This GitHub Actions workflow is a Continuous Integration/Continuous Deployment (CI/CD) pipeline for a Java project that includes building and pushing a Docker image to Docker Hub. Here's a step-by-step explanation of the workflow:

```

name: project cicd flow


```

* The name of the GitHub Actions workflow is "project cicd flow."

```

on:
  push:
    branches: [ master ]
  pull_request:
    branches: [ master ]


```

* The workflow is triggered on both pushes and pull requests to the master branch. This means that whenever code changes are pushed or a pull request is made to the master branch, the workflow will run.

```

jobs:
  build:


```

* The workflow defines one job named build. This job is responsible for the entire CI/CD process.

```

runs-on: ubuntu-latest

```

The job will run on a virtual machine with the latest version of Ubuntu.

```

steps:
- uses: actions/checkout@v2
- name: Set up JDK 1.8
  uses: actions/setup-java@v1
  with:
    java-version: '1.8'
    distribution: 'adopt'
    cache: maven
- name: Build with Maven
  run: mvn clean install
- name: Build & push Docker image
  uses: mr-smithers-excellent/docker-build-push@v5
  with:
    image: sharan7898/github-action
    tags: latest
    registry: docker.io
    dockerfile: Dockerfile
    username: ${{ secrets.DOCKER_USERNAME }}
    password: ${{ secrets.DOCKER_PASSWORD }}


```

* The steps section contains the individual steps that will be executed as part of the job.

* The first step uses the actions/checkout action to clone the repository and check out the latest code from the default branch (in this case, master).

* The second step sets up JDK 1.8 using the actions/setup-java action. It configures the Java version to 1.8 and uses the AdoptOpenJDK distribution. Additionally, it caches Maven dependencies to speed up subsequent builds.

* The third step runs the mvn clean install command, which uses Maven to build the Java project. The clean goal removes any previous build artifacts, and the install goal compiles the code, runs tests, and packages the application.

* The last step uses the mr-smithers-excellent/docker-build-push action to build the Docker image and push it to Docker Hub. It specifies the Docker image name (sharan7898/github-action) and the latest tag. The image is pushed to Docker Hub (docker.io) using the provided Dockerfile. The Docker Hub username and password are read from GitHub Secrets, allowing secure authentication during the push process.