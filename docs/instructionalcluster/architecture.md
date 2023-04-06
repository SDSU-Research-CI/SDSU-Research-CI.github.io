---
layout: default
title: Architecture Details
parent: Instructional Cluster
nav_order: 7
has_children: false
description: ""
permalink: /instructionalcluster/architecture
---

# Architecture

The instructional cluster is part of the [National Research Platform](https://nationalresearchplatform.org/) Nautilus platform, a distributed Kubernetes-based compute environment supporting CPU and GPU workloads. SDSU invested in hardware to support instructional use-cases and hosts the hardware in its campus data center. The resources are given first priority to instructional use and then made available to other users of Nautilus.

## Compute

SDSU hosts 15 Dell PowerEdge servers supporting the instructional cluster.

| Node Type    | Quantity | Specifications |
|:-------------|:---------|:------|
| GPU          | 8        | PowerEdge R750XA<br />(2x) Intel Xeon Gold 6338 2G CPU, 32C/64T<br/>(4x) Nvidia A100 GPU, 80 GB RAM<br/>512 GB System RAM |
| CPU          | 4        | PowerEdge R750<br/>(2x) Intel Xeon Gold 6338 2G CPU, 32C/64T<br/>512 GB System RAM |
| Storage      | 3        | PowerEdge R750<br/>(2x) Intel Xeon Gold 6336Y 2.4G, 24C/48T<br/>160 TB Storage<br/>256 GB System RAM |

![Server Rack](/images/instructionalcluster/serverrack.png)

## Storage

Each user of the instructional cluster is provided 5GB of storage space accessible from JupyterHub. The space is provided by a [LINSTOR](https://linbit.com/linstor/) filesystem hosted on three storage nodes.

## Networking

Instructional cluster nodes make use of SDSU's [Science DMZ](https://iotlab.sdsu.edu/index.php/science-dmz/) providing 100G connectivity to [CENIC's](https://cenic.org/network/operations/maps) HPR network and 10G connectivity to its DC network.