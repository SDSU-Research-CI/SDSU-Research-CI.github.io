---
layout: default
title: Launch a Container
parent: Student Resources
grand_parent: Instructional Cluster
nav_order: 2
description: ""
permalink: /instructionalcluster/students/launchcontainer
---

# Launch a Container

After [logging in](/instructionalcluster/students/loggingin) to JupyterHub you must launch a container in order to begin using JupyterHub by selectin an appropriate image. Your instructor will provide the correct [container image](/instructionalcluster/images) to use for the course.

![Container Prompt](/images/instructionalcluster/cilogon4.png)

Depending on your needs, you may need to adjust values for GPU, CPU Cores, Memory, and Image. Your instructor should provide you with the necessary settings - if not, the defaults can be used.

| Option               | Description               |
|:---------------------|:--------------------------|
| GPU                  | The Instructional Cluster has both CPU and GPU (graphical processing unit) nodes. The GPU nodes contain NVIDIA A100 GPUs. These can be used for specialized tasks that are not possible with strictly CPU nodes. Your instructor will let you know if you require GPUs. |
| CPU Cores            | Number of CPU cores assigned to your container. |
| Memory               | Gigabytes (GB) of memory assigned to your container.

Next, select an appropraite [container image](/instructionalcluster/images) that contains the required software. Your instructor will inform you which image to use. 

Finally, click **Start** to launch your container. You will receive a progress bar and progress messages as your container is created. It can take several minutes for some images to launch. 

Once the container launches, you'll be presented with the JupyterLab interface.