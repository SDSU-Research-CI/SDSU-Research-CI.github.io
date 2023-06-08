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

After reading and following this documentation you should be able to:
- Understand containers and kubernetes at a high-level
- Start a Jupyter Notebook with the [Kube Notebook](https://github.com/SDSU-Research-CI/kube-notebook/pkgs/container/kube-notebook) image
- Configure your Kube Notebook to be able to interact with the Instructional Cluster
- Launch a containerized job on the Instructional Cluster

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
    - Here is a video for [signing into the Instructional Cluster JupyterHub](/instructionalcluster/videos/access) for your convenience
1. Complete the Server Options form with the following settings:
    - GPUs = 0
    - CPU Cores = 2
    - Memory GB = 4
    - ![server options](/images/softwarefactory/)
1. Select the "Kube Notebook" image
1. Click Start
1. You will see a progress bar while your notebook is starting

## Configuring the Kube Notebook


## Launching Containers on the Instructional Cluster


## Next Steps
Now that you have run your first container on the Instructional Cluster feel free to choose from some of these more advanced topics:
1. Running pods, batch jobs and deployments
1. Interacting with Kubernetes from local commandline
