---
layout: default
title: Getting Started
parent: Software Factory
nav_order: 2
description: ""
permalink: /softwarefactory/gettingstarted
---

# Getting Started
This documentation will guide you through your first steps to running containers on the Instructional Cluster. This is intended for SDSU instructors and researchers who are interested in taking advantage of HPC resources for Data Science and Machine Learning workloads.

## Learning Outcomes
After reading and following this documentation you should be able to:
- Understand containers and kubernetes at a high-level
- Start a Jupyter Notebook with the [Kube Notebook](https://github.com/SDSU-Research-CI/kube-notebook/pkgs/container/kube-notebook) image
- Configure your Kube Notebook to be able to interact with the Instructional Cluster
- Launch a containerized job on the Instructional Cluster

### Prerequisites
This documentation assumes that you have:
- Followed the [Getting Access documentation](./gettingaccess)
- Some familiarity with the Linux terminal

## Containers and Kubernetes
At a high-level, containers are packaged software applications containing all of their dependencies like the operating system (OS), file structures, configuration and other code libraries.

Containers offer many benefits but here we list a few of the most impactful ones:
1. Isolated Runtime Environments
    - Two or more containers running on the same system do not affect one another.
1. Portability
    - The same container can be run on a laptop, on the cloud, or on the Instructional Cluster without being modified.
1. Consistency
    - The same container given the same input will produce the same output.

[Kubernetes](https://kubernetes.io/) is a container orchestration platform for "automating deployment, scaling and management of containerized applications." If you are familiar with more traditional HPC systems, you can think of Kubernetes like a workload manager (i.e. Slurm). Kubernetes allows us to wrap containers in "pods" which are then scheduled and run on the cluster. Similar to workload managers, Kubernetes allows us to make requests for resources needed to run containerized workloads like CPUs, GPUs and memory.

## Starting a Kube Notebook
Research and Cyberinfrastructure has created a [Kube Notebook](https://github.com/SDSU-Research-CI/kube-notebook/pkgs/container/kube-notebook) image to simplify access to Kubernetes. This container image will launch a Jupyter Lab instance that you can access from you web browser. From inside Jupyter Lab you can launch a terminal with the kubectl software pre-installed for communicating with the kubernetes cluster.

Follow these instructions to spin up and connect to your kube notebook:
1. Sign into [jupyterhub.sdsu.edu](jupyterhub.sdsu.edu)
    - Here is a video for [signing into the Instructional Cluster JupyterHub](/instructionalcluster/videos/access)
1. Complete the Server Options form with the following settings:
    - GPUs = 0
    - CPU Cores = 2
    - Memory GB = 4
    - ![server options](/images/softwarefactory/gettingstarted1.png)
1. Select the "Kube Notebook" image
    - ![kube notebook selected](/images/softwarefactory/gettingstarted2.png)
1. Click Start
1. You will see a progress bar while your notebook is starting
    - ![notebook starting](/images/softwarefactory/gettingstarted3.png)
1. Once the notebook has loaded, you should see the Jupyter Lab UI
    - ![jupyter lab UI](/images/softwarefactory/gettingstarted4.png)

You now have a notebook running that has the kubectl command pre-installed which will allow you to interact with the kubernetes cluster.

## Configuring the Kube Notebook
With the Kube Notebook running, lets configure it to talk to the National Research Platform kubernetes cluster. You will need the kube config from [step 2 of the NRP tasks](/softwarefactory/gettingaccess#nrp-portal-tasks) from the Getting Access guide.

Follow these steps to configure the notebook:
1. Upload your config file by clicking the upload files icon and then selecting your config:
    - ![upload files](/images/softwarefactory/gettingstarted5.png)
    - ![select config](/images/softwarefactory/gettingstarted6.png)
1. Verify that your config file has been uploaded in the file browser of Jupyter Lab
    - ![file browser](/images/softwarefactory/gettingstarted7.png)
1. Click the "+" button
    - ![click the plus button](/images/softwarefactory/gettingstarted8.png)
1. Open the Terminal
    - ![click the terminal icon](/images/softwarefactory/gettingstarted9.png)
1. Run the following commands: 
    - Make the .kube folder:
        - `mkdir ~/.kube`
    - Move your config file into the .kube folder:
        - `mv ~/config ~/.kube/config`
    - Check to make sure your config file copied successfully:
        - `ls ~/.kube`
    - You should see the config file listed:
        - ![config file in kube folder](/images/softwarefactory/gettingstarted10.png)
1. Verify that your notebook can communicate with the cluster with this command (replace the namespace):
    - `kubectl get pods -n [your-namespace]`
    - ![pods in namespace](/images/softwarefactory/gettingstarted11.png)
        - Note: output may vary

Congratulations! Your Kube Notebook is now configured to talk to the National Research Platform.

## Launching Containers on the Instructional Cluster
Now that your notebook is configured, let's run your first containerized machine learning job on the instructional cluster. For the following example, we will be using the dataset... [TO-DO]

## Next Steps
Now that you have run your first container on the Instructional Cluster feel free to choose from some of these more advanced topics:
1. Running pods, batch jobs and deployments
1. Interacting with Kubernetes from local commandline
