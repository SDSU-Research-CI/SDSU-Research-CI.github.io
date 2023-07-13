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
- [Understand containers and kubernetes at a high-level](/softwarefactory/gettingstarted#containers-and-kubernetes)
- [Start a Jupyter Notebook with the Kube Notebook image](/softwarefactory/gettingstarted#starting-a-kube-notebook)
- [Configure your Kube Notebook to be able to interact with the Instructional Cluster](/softwarefactory/gettingstarted#configuring-the-kube-notebook)
- [Launch a containerized job on the Instructional Cluster](/softwarefactory/gettingstarted#launching-containers-on-the-instructional-cluster)

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

[Kubernetes](https://kubernetes.io/), often shortened to 'k8s', is a container orchestration platform for "automating deployment, scaling and management of containerized applications." If you are familiar with more traditional HPC systems, you can think of Kubernetes like a workload manager (i.e. Slurm). Similar to workload managers, Kubernetes allows us to make requests for resources like CPUs, GPUs and memory to run our programs. Kubernetes wraps a container in a [pod](https://kubernetes.io/docs/concepts/workloads/pods/), the smallest compute unit, which is then scheduled and run on the cluster.  It is important to note that pods are ephemeral and once a pod is deleted everything inside the pod is deleted -- meaning any data downloaded, content generated or files modified. Make sure to transfer data that you want to save out of the pod before deleting it.

## Starting a Kube Notebook
Research and Cyberinfrastructure has created a [Kube Notebook](https://github.com/SDSU-Research-CI/kube-notebook/pkgs/container/kube-notebook) image to simplify access to Kubernetes. This container image will launch a Jupyter Lab instance that you can access from your web browser. From inside Jupyter Lab you can launch a terminal with the kubectl software pre-installed. [Kubectl](https://kubernetes.io/docs/reference/kubectl/kubectl/) is a commandline tool for communicating and interacting with the Kubernetes cluster.

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
Now that your notebook is configured, let's run your first container on the instructional cluster. For the following example, we will be using the simple [Hello SDSU repository](https://github.com/SDSU-Research-CI/hello-sdsu/tree/main) and its associated [container image](https://github.com/SDSU-Research-CI/hello-sdsu/pkgs/container/hello-sdsu).

### Checking Out the Example Repository
Follow these steps to get a copy of the repo cloned to your kube notebook and then examine the files to get familiar with them.

1. From your kube notebook pull up a terminal window and run this command to get a copy of the repository:
    - `git clone https://github.com/SDSU-Research-CI/hello-sdsu.git`
        - ![output from git clone hello-sdsu repo](/images/softwarefactory/gettingstarted12.png)
1. Change directory into the hello-sdsu directory and then list the files:
    - `cd hello-sdsu`
    - `ls -la`
        - ![file listing in hello-sdsu](/images/softwarefactory/gettingstarted13.png)
1. Notice that the Jupyter Lab file explorer is still viewing the previous directory. Double click the hello-sdsu directory in the file explorer to open it
    - ![open hello-sdsu in file explorer](/images/softwarefactory/gettingstarted14.png)
    - ![hello-sdsu files in file explorer](/images/softwarefactory/gettingstarted15.png)
1. Open the `hello.py` program; you should see the following:
    ```python
    sdsu = """
      _______    _______      _______    __     __
     (   ____)  |   __  \    (   ____)  |  |   |  |
      \  \      |  |  \  \    \  \      |  |   |  |
       \  \     |  |   |  )    \  \     |  |   |  |
     ___\  \    |  |__/  /   ___\  \    |  |___|  |
    (_______)   |_______/   (_______)   \_________/
    """

    print(f"Hello there,\n{sdsu}")
    ```
    - This program is a simple variation on the typical Hello, World program with a bit of ascii art
1. Open the `Dockerfile`; you should see the following:
    ```Dockerfile
    FROM python:3

    WORKDIR /usr/src/app

    COPY hello.py /usr/src/app/hello.py

    CMD ["python3", "hello.py"]
    ```
    - This is a [Dockerfile](https://docs.docker.com/engine/reference/builder/) which defines a container image
    - This container image is based on the Python 3 image and it copies our hello.py program into the container and then runs it
1. Open the Kubernetes manifest file `hello-pod.yaml`; you should see the following:
    ```YAML
    apiVersion: v1
    kind: Pod
    metadata:
      name: hello-pod
    spec:
      containers:
      - name: hellopod
        image: ghcr.io/sdsu-research-ci/hello-sdsu:main
        resources:
          limits:
            memory: 100Mi
            cpu: 100m
          requests:
            memory: 100Mi
            cpu: 100m
        command: ["sh", "-c", "sleep infinity"]
      affinity:
        nodeAffinity:
          requiredDuringSchedulingIgnoredDuringExecution:
            nodeSelectorTerms:
            - matchExpressions:
              - 'key': 'nautilus.io/sdsuinstruction'
                'operator': 'In'
                'values': ["true"]
    ```
    - Kubernetes manifests are defined in the [YAML file format](https://en.wikipedia.org/wiki/YAML)
    - At first glance there is a lot going on in this file, but for now we will focus on these three things:
        1. `kind: Pod`
            - This specifies the kind of Kubernetes object, in this case a pod but we could also specify other [Workload Resources](https://kubernetes.io/docs/concepts/workloads/controllers/) like jobs or deployments
        1. `image: ghcr.io/sdsu-research-ci/hello-sdsu:main`
            - This is the container image which the container will be based on
            - The container image defines things like the OS, file structures, environment variables, packages, libraries etc.
        1. `command: ["sh", "-c", "sleep infinity"]`
            - This is the linux command to be run once the container is running inside the pod

### Deploying the Pod
1. 

### Deleting the Pod

## Next Steps
Now that you have run your first container on the Instructional Cluster feel free to choose from some of these more advanced topics:
1. Explore templates for pods, batch jobs and deployments
1. Interacting with Kubernetes from local commandline
