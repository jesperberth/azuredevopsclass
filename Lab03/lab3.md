# Lab 3 Create and assign tasks in Agile Board

In this lab we will create and assign a task in the Board section of Azure DevOps and create a new branch

## Table of Contents

- [Pre](#pre)
- [Task 1 Create a task in Azure DevOps](#task-1-create-a-task-in-azure-devops)
- [Task 2 Create a new branch](#task-2-create-a-new-branch)
- [Task 3 Open new branch](#task-3-open-new-branch)
- [Task 4 Create html](#task-3-create-html)

## Pre

VSCode, Git and windows Terminal must be installed

## Task 1 Create a task in Azure DevOps

In the Azure DevOps Portal click Boards and click Boards again

You should be in the Board section where there are four panes

New, Active, Resolved and Closed

![Alt text](pics/001_devops_boards.png?raw=true "Boards")

Click New and give the new task a name

![Alt text](pics/002_add_task.png?raw=true "add task")

Now lets assign the task to our self

You can do it directly on the Board just extend the task on the arrow and click assign

![Alt text](pics/003_assign_user1.png?raw=true "assign user")

or

you can click the title to open the User Story and assign a user in here click **Save and Close** when you are done

![Alt text](pics/004_assign_user2.png?raw=true "assign user")

In the User Story you can enter a Description invite other users in the Discussion, add Planning, Priority and Classification

You can also add Deployment and Development here, we will do that later

![Alt text](pics/005_board_done.png?raw=true "boards")

## Task 2 Create a new branch

Lets create a new branch

On the board click the three dots ( ... ) on the task

Select "New Branch..."

![Alt text](pics/006_create_branch.png?raw=true "create branch")

Give the branch a name

Make sure you select the correct repository

Click **Create Branch**

![Alt text](pics/007_new_branch.png?raw=true "new branch")

In the Repository you are now looking at the new branch

Click the branch button in the top to see all you branches

![Alt text](pics/008_look_at_branch.png?raw=true "look at branch")

## Task 3 Open new branch

Lets see the branch in VSCode

Go to Windows Terminal and do a git pull

You should get a [new branch] if not wait a minute and try again

![Alt text](pics/009_git_pull.png?raw=true "git pull")

In VSCode change to the new branch

In the bottom status line click **main**

In the top select the new branch

![Alt text](pics/010_vscode_change_branch.png?raw=true "change branch")

You can now see the branch you created in the bottom status line

![Alt text](pics/011_vscode_change_branch_name.png?raw=true "change branch")

## Task 4 Create html

Lets add a html page for our website

In VSCode

In the file section add a new folder **Website**

In the new folder create a file **index.html**

And add below to the file, you can modify it to fit your project

```html

<html>
<head><title>Website</title></head>
<body>
    <h1>Welcome to the Launch Complex 39 Website</h1>
    <h2>Maintained by: Jesper Berth</h2>
    <p>
        Launch Complex 39 (LC-39) is a rocket launch site
        at the John F. Kennedy Space Center on Merritt Island
        in Florida, United States.
        The site and its collection of facilities were originally built as the Apollo program's "Moonport"
        and later modified for the Space Shuttle program.
    </p>
</body>
</html>

```

![Alt text](pics/012_new_index_html.png?raw=true "new index.html")

Now lets Stage the file and commit and sync back to our repository

First go to **Source Control** right click the index.html file and select **Stage Changes**

![Alt text](pics/013_stage_index_html.png?raw=true "stage index.html")

Add your commit message at the top hit **( Ctrl + Enter)**

and click **Sync Changes**

![Alt text](pics/014_commit_index_html.png?raw=true "commit index.html")

![Alt text](pics/015_sync_index_html.png?raw=true "sync index.html")

Go to Repos in Azure DevOps

The website branch should now show the changes we made

![Alt text](pics/016_repo_index_html.png?raw=true "repo index.html")

Lab Done

[Pull Request – Accept PR](../lab04/lab4.md)
