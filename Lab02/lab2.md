# Lab 1 Create Repo and Clone

In this lab we will create a new repo and clone the repo to our workstation

## Table of Contents

- [Pre](#pre)
- [Task 1 Create a repo in Azure DevOps](#task-1-create-a-repo-in-azure-devops)
- [Task 2 Clone Repository](#task-2-clone-repository)
- [Task 3 Push to Repo](#task-2-push-to-repo)

## Pre

VSCode, Git and windows Terminal must be installed

## Task 1 Create a repo in Azure DevOps

We need to create a new repository to work in

You can choose what to call it, avoid using spaces and underscore

Azure DevOps allow spaces and underscores, but other Repositories dosn't as it can make scripting troublesome

In Azure DevOps go to "Repos" in the left menu

On the top click the "down" button on the repository name and select "New repository"

![Alt text](pics/001_new_repo.png?raw=true "New Repo")

Stay with the default Git as Repository Type

Give the repository a name __The name has to be uniq__

Make sure there is a check in add a README

Click "Create"

![Alt text](pics/002_create_repo.png?raw=true "Create Repo")

The repository is now ready with a README.md

![Alt text](pics/003_repo_done.png?raw=true "Repo Done")

## Task 2 Clone Repository

Lets clone our new repo to our workstation

Click the Clone button in the right top corner

![Alt text](pics/004_click_clone.png?raw=true "Click clone")

There are two connection methods

__HTTPS__ which requires a set of credentials

__SSH__ which requires a ssh key, we did this in the first lab so we will use SSH as our connection method

And there is a button to connect directly to VSCode, but we will use the cli this time

Clich "SSH" and copy the string

![Alt text](pics/005_ssh_clone.png?raw=true "ssh clone")

Open Windows Terminal

change to you preferred directory

and run git clone git@ssh.dev.azure.com:v3/teamredhatarrow/ApolloWebsite/launchcomplex39

**Type:**

```bash

git clone <your git url>

```

![Alt text](pics/006_git_clone.png?raw=true "git clone")

## Task 3 Push to Repo

In this task we will update the README.md file and push it back to our repo "Origin"

In the Windows terminal open VSCode

cd launchcomplex39

code . **will open VSCode in current dir**

**Type:**

```bash

cd <your repo name>

code .

```

![Alt text](pics/007_open_vscode.png?raw=true "Open VSCode")

In VSCode click the file README.md

![Alt text](pics/008_vscode_README.png?raw=true "VSCode README")

Change the text in the README.md file to match your project

Git is Integrated into VSCode, so everything we do will be monitored by git

- 1: For every file in our working dir, git will show a status **M** is modified
- 2: On the tab for any open file a . shows that the file has not been saved
- 3: Will show which Branch we are working on, a * will show that we have changes not pushed to the repository
- 4: Is the Source Control button, a blue circle with a numer tells us that there a **xx** changes not commited

![Alt text](pics/009_vscode_README_git.png?raw=true "VSCode README Git")

Save the changes to the README.md (Ctrl + S)

add a new file call it CHANGELOG.md

Either click the +File on top of the folder or right click in the file list and select new file

![Alt text](pics/010_add_changelog.png?raw=true "Add Changelog")

CHANGELOG.md is green and has a U for Untracked

Add a line to the CHANGELOG.md file

Save the file

Change to the Source Control View **Click the Source Control Button** or use **( Ctrl + Shift +G )**

**Type:**

```bash

# CHANGELOG

```

![Alt text](pics/011_change_changelog.png?raw=true "change Changelog")

To stage the new file you can either click the little + sign or right click on the file and select **Stage Changes**

![Alt text](pics/012_stage_change_changelog.png?raw=true "stage change Changelog")

Now the files are staged and we can do a commit

To do a commit we can simply type our Commit message in the top text box and type **( Ctrl + Enter)**

![Alt text](pics/013_commit_vscode.png?raw=true "commit vscode")

Now we just need to push to the repo

You can click the blue button **Sync Changes** or on the lower menu click on the status to start sync

![Alt text](pics/014_commit_vscode_sync.png?raw=true "commit vscode sync")

Take a look in Azure DevOps changes should be visible here

![Alt text](pics/015_devops_after_sync.png?raw=true "DevOps after sync")

Lab Done

[.....](../lab02/lab2.md)