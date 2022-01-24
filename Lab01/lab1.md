# Lab 1 Access DevOps

In this lab we connect to Azure DevOps and add our SSH Public key so we can push and pull to the repo

## Table of Contents

- [Pre](#pre)
- [Task 1 Logon to Azure DevOps](#task-1-logon-to-azure-devops)
- [Task 2 Take a look in the git folder](#task-2-take-a-look-in-the-git-folder)

## Pre

Git and windows Terminal must be installed

## Task 1 Logon to Azure DevOps

Open your browser in Incognito mode (or equivilent)

Supported browsers

- Microsoft Edge
- Mozilla Firefox
- Apple Safari
- Google Chrome

Go to [https://dev.azure.com/teamredhatarrow](https://dev.azure.com/teamredhatarrow)

![Alt text](pics/001_devops_login.png?raw=true "DevOps Login")

You will need to change your password

![Alt text](pics/002_devops_changepw.png?raw=true "DevOps Login change password")

Once logged in you need to click the ApolloWebsite Project

![Alt text](pics/003_devops_apolloProject.png?raw=true "DevOps ApolloWebsite")

![Alt text](pics/004_apolloproject.png?raw=true "DevOps ApolloWebsite")

## Task 2 Add Public SSH Key

We need to add our public SSH key to pull and push code to Azure DevOps

Open Windows Terminal, you should be in your home directory

![Alt text](pics/005_terminal.png?raw=true "Windows Terminal")

**Type:**

```bash

 cat .ssh\id_rsa.pub

```

![Alt text](pics/006_ssh_pub.png?raw=true "ssh pub key")

Copy the key

![Alt text](pics/007_ssh_pub_copy.png?raw=true "ssh pub key copy")

In the DevOps portal click the user icon in the top right corner and select "SSH Public keys"

![Alt text](pics/008_add_key_to_devops.png?raw=true "add ssh pub key")

Click the Add button

![Alt text](pics/009_click_add.png?raw=true "click add")

Give the key a description

Paste the key data in

Click Save

![Alt text](pics/010_key_added.png?raw=true "Key added")

The key from your workstation is now added, you can add aditional keys from other workstations you use

![Alt text](pics/011_list_of_keys.png?raw=true "list of keys")

Lab Done

[Create repo and clone](../lab02/lab2.md)
