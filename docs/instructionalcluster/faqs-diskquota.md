---
layout: default
title: Check Disk Quota
parent: Frequently Asked Questions
grand_parent: Instructional Cluster
nav_order: 1
description: ""
permalink: /instructionalcluster/faqs/diskquota
---

# Check Disk Quota

Each user is provided 20 GB (gigabytes) of storage accessible from within JupyterHub. This storage is provisioned the first time you access JupyterHub and will be deleted one semester after your last active course. If you wish to retain your data, it's highly recommended that you make regular [backups](/instructionalcluster/faqs/spacemanagement#back-up-to-a-zip-archive).

To check how much of your 20 GB you are consuming:

1. From the **Launcher** page select **Terminal**.
![Launch Terminal](/images/instructionalcluster/faq-space1.png)
1. The Terminal lets you enter commands and interact with the underlying container executing your code. Enter the following command to view details about container disk usage:
```
df -h
```
![Terminal Details](/images/instructionalcluster/faq-space2.png)
1. Look for the **/home/jovyan** file filesystem. This is where your *home* directory resides. In the example above, you'll see its size is 20 GB (gigabyte), 177 MB (megabyte) is used, and 20 GB (gigabyte) is free/available. This file system is the same one you see in the left-hand side of JupyterHub.

{: .note }
If you need to clean up or back up files, please take a look at [disk space management](/instructionalcluster/faqs/spacemanagement).