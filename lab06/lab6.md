# Lab 6 Create a Release pipeline

In this lab we will create a Release pipeline

## Table of Contents

- [Pre](#pre)
- [Task 1 Create ansible playbook](#task-1-create-ansible-playbook)
- [Task 2 Create a Release pipeline](#task-2-create-a-release-pipeline)
- [Task 3 Create a Release](#task-3-create-a-release)

## Pre

VSCode, Git and windows Terminal must be installed

## Task 1 Create ansible playbook

Lets create a playbook for container deployment with ansible

The playbook will create a resource group in Azure and create an Azure Container Instance with our Image in

We will do this as we learned from the previous labs

- Create a task
- Assign task to your self
- Create a new Branch **Ansible**
- git pull on your workstation
- Change branch in VSCode
- Add a new file call it "container.yml"
- Stage
- Commit
- Approve merge
- Complete merge

```ansible

---
- hosts: localhost
  connection: local
  vars:

  tasks:
    - name: Create Resource Group
      azure_rm_resourcegroup:
        name: "webserver_{{ containername }}"
        location: northeurope

    - name: Create Container Instance
      azure_rm_containerinstance:
        resource_group: "webserver_{{ containername }}"
        name: myContainer
        os_type: linux
        ip_address: public
        registry_login_server: "teamredhatarrow.azurecr.io"
        registry_username: "teamredhatarrow"
        registry_password: "{{ password }}"
        containers:
          - name: "{{ containername }}"
            image: "teamredhatarrow.azurecr.io/{{ containername }}:latest"
            memory: 1.5
            ports:
              - 80
      register: container

    - name: Get container public ip
      debug:
        msg: "{{ container.ip_address }}"

```

![Alt text](pics/001_vscode_playbook.png?raw=true "vscode playbook")

When done you should have a **container.yml** in the repository

![Alt text](pics/002_repo_playbook.png?raw=true "repo playbook")

## Task 2 Create a Release pipeline

Lets create the release pipeline

In Azure DevOps portal go to **Pipelines** click **Releases**

Click **New Release**

![Alt text](pics/003_new_release.png?raw=true "new release")

Select **Empty job**

![Alt text](pics/004_empty_job.png?raw=true "empty job")

Change the Stage name to **Deploy** click the **X** to close

![Alt text](pics/005_stage_name.png?raw=true "Stage Name")

Click on **Add an Artifact**

![Alt text](pics/006_add_artifact.png?raw=true "Add artifact")

Select Source type **Build**

Select your Build Pipeline in the Source

Click **Add**

![Alt text](pics/007_select_source.png?raw=true "Select source artifact")

Change the name of the Pipeline to something with your project in

![Alt text](pics/008_change_pipelinename.png?raw=true "change pipeline name")

Click the small link in the **Deploy Stage** with 1 job, 0 task

![Alt text](pics/009_create_task.png?raw=true "create task")

Click on **Agent Job**

Change **Agent Pool** to **Selfhosted**

![Alt text](pics/010_change_pool.png?raw=true "change pool")

Click **+** to add a task

![Alt text](pics/011_add_task.png?raw=true "add task")

Click on **Add** in the **Ansible** box, if ansible isnt there do a search for it

![Alt text](pics/012_add_ansible.png?raw=true "add ansible task")

Click on **Run playbook** click the **...** after the **File path**

Click through until you have the **container.yml** file

Click **OK**

![Alt text](pics/013_add_ansible_path.png?raw=true "add ansible path to task")

Now we need to add some extra vars for the playbook

The **password** will be given by the teacher

The **containername** is the one you sat in the Build Pipeline as **imageName**

--extra-vars "password=+7n+CGLFZhrVeB3y0MhdOlHC/wWAINe9 containername=jesbe"

Remove the checkmark in **Fail on STDERR**

Click **Save** en the top right corner

![Alt text](pics/014_add_ansible_extravar.png?raw=true "add ansible extravar to task")

## Task 3 Create a Release

Now lets create a release to run our pipeline

Click **Create Release**

![Alt text](pics/015_create_release.png?raw=true "create release")

In the Create a new release window

Click the **Deploy** Pipeline so i turns from blue to gray, now it will be a manual run click **Create**

![Alt text](pics/016_gray_create_release.png?raw=true "create release")

Click on **Release-xx**

![Alt text](pics/017_start_release.png?raw=true "start release")

Hover over the **Deploy** Stage and a **Deploy** button appears click **Deploy**

![Alt text](pics/018_Deploy_release.png?raw=true "Deploy release")

Click **Deploy** Again

![Alt text](pics/019_Deploy_release_again.png?raw=true "Deploy release")

The Release Pipeline is now running if you click on **Deploy in progress** you can follow along

![Alt text](pics/020_Deploy_running.png?raw=true "Deploy running")

You can click on the tasks that are failed, its a minor error but still marked as failed

![Alt text](pics/021_Deploy_result.png?raw=true "Deploy result")

The container is running in Azure

![Alt text](pics/022_container.png?raw=true "Container running")

Lab done
