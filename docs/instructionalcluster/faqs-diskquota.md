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

Each user is provided 5 GB (gigabytes) of storage accessible from JupyterHub. This storage is provisioned the first time you access JupyterHub and will be deleted one semester after your last active course. If you wish to retain your data, it's highly recommended that you make regular [backups](/instructionalcluster/faqs/backup).

To check how much if your 5 GB you are consuming:

1. From the **Launcher** page select **Terminal**.
![Launch Terminal](/images/instructionalcluster/faq-space1.png)
1. The Terminal lets you enter commands and interact with the underlying container executing your code. Enter the following command to view details about container disk usage:
```
df -h
```
![Terminal Details](/images/instructionalcluster/faq-space2.png)
1. Look for the **/home/jovyan** file filesystem. In the example above, you'll see its size is 5 GB (gigabyte), 228 MB (megabyte) is used, and 4.8 GB (gigabyte) is free/available. This file system is the same one you see in the left-hand side of JupyterHub.

{: .note }
If you need to clean up or back up files, please take a look at the [space management](/instructionalcluster/faqs/spacemanagement).