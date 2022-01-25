# Lab 5 Create a build pipeline

In this lab we will create a Build pipeline

## Table of Contents

- [Pre](#pre)
- [Task 1 Check Agent is running](#task-1-check-agent-is-running)
- [Task 2 Create a Build pipeline](#task-2-create-a-build-pipeline)
- [Task 3 Add Docker file](#task-3-add-docker-file)
- [Task 4 Run Build Pipeline](#task-3-run-build-pipeline)

## Pre

VSCode, Git and windows Terminal must be installed

## Task 1 Check Agent is running

Check that the Selfhosted Agent is running, we will use this agent to process our Build Pipeline

In Azure DevOps go to Project Settings

![Alt text](pics/001_project_settings.png?raw=true "project settings")

In **Project Settings** go to **Pipelines** click **Agent pools**

Select **Agents** select **Selfhosted**

Check that at least one agent is online

![Alt text](pics/002_agent_online.png?raw=true "agent online")

## Task 2 Create Build Pipeline

Lets create a Build Pipeline we can configure this to run everytime a change is made in the **main** branch

In our case we will comment out the two lines in the beginning of the yaml file and run the pipeline manualy

In the Azure DevOps portal

Click **Pipelines**

Click the Blue **New Pipeline**

![Alt text](pics/003_new_pipeline.png?raw=true "new pipeline")

Select **Azure Repos Git**

![Alt text](pics/004_select_azure_repo_git.png?raw=true "Azure Repos Git")

Select you own Repository

![Alt text](pics/005_select_repo.png?raw=true "Select Repo")

Delete all lines and add below

**IMPORTANT:** Change the variable **imageName** to your name or initials

```yaml
# Starter pipeline
# Start with a minimal pipeline that you can customize to build and deploy your code.
# Add steps that build, run tests, deploy, and more:
# https://aka.ms/yaml

#trigger:
#- main

pool:
  name: Selfhosted

variables:
    imageName: 'jesbe'

steps:
- task: CopyFiles@2
  inputs:
    SourceFolder: '$(agent.builddirectory)'
    Contents: '**'
    TargetFolder: '$(build.artifactstagingdirectory)'
    CleanTargetFolder: true
    OverWrite: true

- task: PublishBuildArtifacts@1
  inputs:
    PathtoPublish: '$(Build.ArtifactStagingDirectory)'
    ArtifactName: 'drop'
    publishLocation: 'Container'

- task: Docker@2
  displayName: Build and push image
  inputs:
    containerRegistry: 'teamredhatarrow'
    repository: '$(imageName)'
    command: 'buildAndPush'
    Dockerfile: 'Dockerfile'
    tags: 'latest'
```

Click on the down arrow on the **Save and run** select **Save**

![Alt text](pics/006_add_yaml.png?raw=true "add yaml")

In the save dialog keep the default settings and click **save**

![Alt text](pics/007_commit_pipeline.png?raw=true "commit pipeline")

## Task 3 Add Docker file

We need to add a docker file to our repository

We will do this as we learned from the previous labs

- Create a task
- Assign task to your self
- Create a new Branch **Docker**
- git pull on your workstation
- Change branch in VSCode
- Add a new file call it "Dockerfile" **Its case sensitive - Capital D rest is lower case**
- Stage
- Commit
- Approve merge
- Complete merge

```Dockerfile
FROM ubuntu
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update
RUN apt-get install apache2 -y
RUN apt-get install apache2-utils -y
RUN apt-get clean
COPY Website/index.html /var/www/html/index.html
EXPOSE 80
CMD ["apache2ctl","-D","FOREGROUND"]
```

![Alt text](pics/003_vscode_dockerfile.png?raw=true "vscode dockerfile")

When done you should have the Dockerfile in the **main** branch

![Alt text](pics/004_main_branch_dockerfile.png?raw=true "vscode dockerfile")

## Task 4 Run Build Pipeline

Now lets run the build pipeline

In the Azure DevOps portal go to **Pipelines**

Select **All**

Select your Build pipeline

![Alt text](pics/005_select_pipeline.png?raw=true "select pipeline")

Now click **Run pipeline**

![Alt text](pics/006_run_pipeline.png?raw=true "run pipeline")

Leave the Defaults

Click **Run**

![Alt text](pics/007_run_pipeline2.png?raw=true "run pipeline")

Click on the Queued **Job**

![Alt text](pics/008_running_pipeline1.png?raw=true "running pipeline")

Wait for it to finish you can click on each step to see what it did

![Alt text](pics/009_running_pipeline_done.png?raw=true "running pipeline done")

Lab Done

[Release Pipeline](../lab06/lab6.md)
