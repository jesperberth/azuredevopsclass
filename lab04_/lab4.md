# Lab 4 Create and accept a Pull request

In this lab we will create and accept a pull request

## Table of Contents

- [Pre](#pre)
- [Task 1 Create a pull request](#task-1-create-a-pull-request)
- [Task 2 Accept a pull request](#task-2-accept-a-pull-request)
- [Task 3 Update VSCode](#task-3-update-vscode)

## Pre

VSCode, Git and windows Terminal must be installed

## Task 1 Create a pull request

Lets create a new Pull request so that our new website can be verified by someone and the code can be merged with the main branch

In Azure DevOps go to Repos

You should be in your own Repo and the branch we created should be selected

Click **Create a pull request**

![Alt text](pics/001_repo.png?raw=true "repo")

Add a description

Select your self as a reviewer

![Alt text](pics/002_create_pullrq.png?raw=true "create pull request")

Before you click create go through the to tabs **Files** and **Commits**

![Alt text](pics/003_files_pullrq.png?raw=true "files pull request")

![Alt text](pics/004_commits_pullrq.png?raw=true "commits pull request")

Now go back and click **Create**

![Alt text](pics/005_create_pullrq.png?raw=true "create pull request")

## Task 2 Accept a pull request

Now lets go and accept the pull request

You should be redirected to the pull request if not then its in the Repos section under Pull Requests

![Alt text](pics/006_pullrq.png?raw=true "pull request")

Before we Accept the Pull Request lets go though the changes

If there is a Merge Conflict we need to address that before we can continue

Go through Files, Updates and Commits

You can add a comment to tell the committer what you think

![Alt text](pics/007_pullrq_check.png?raw=true "pull request check")

Files

![Alt text](pics/008_pullrq_check_files.png?raw=true "pull request check files")

Updates

![Alt text](pics/009_pullrq_check_updates.png?raw=true "pull request check updates")

Commits

![Alt text](pics/010_pullrq_check_commits.png?raw=true "pull request check commits")

Now if everything is OK you can approve the Pull Request

Click approve in the top right corner

**Note:** If you click on the down arrow you will get additional options

![Alt text](pics/011_approve_pullrq.png?raw=true "approve pull request")

When the Pull Request is approved we can complete the merge

Click the **Complete** button in the top right corner

Default setting is:

- merge (no fast forward)
- Complete Associated work items after merging (Our task)
- Delete the branch

Click **Complete merge**

![Alt text](pics/012_complete_pullrq.png?raw=true "complete pull request")

Now the branch is merged, our website branch is deleted and our Task is marked as done

![Alt text](pics/013_merge_complete.png?raw=true "merge complete")

Go check the files in Repos

The website folder and index.html is now in the **main** branch and the website branch is gone

![Alt text](pics/014_merge_complete_files.png?raw=true "merge complete files")

Go to Boards and click the Board

![Alt text](pics/015_merge_complete_boards.png?raw=true "merge complete boards")

## Task 3 Update VSCode

Lets update VSCode so it we are in the right branch

In VSCode click on the old branch name in the bottom status line and select main in the top dialog

![Alt text](pics/016_update_vscode.png?raw=true "update vscode")

Then do a sync, you should now be on **main** and have the website\index.html

![Alt text](pics/017_update_vscode_sync.png?raw=true "update vscode sync")

Lab Done

[Build Pipeline](../lab05/lab5.md)
