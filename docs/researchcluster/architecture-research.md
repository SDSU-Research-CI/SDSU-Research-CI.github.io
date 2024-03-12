---
layout: default
title: Architecture Details
parent: Research Cluster
nav_order: 5
has_children: false
description: ""
permalink: /researchcluster/Architecture
---

{: .note }
This page is currently under construction. Information will be updated soon

# Architecture

TIDE (https://tide.sdsu.edu/), is an NSF-backed resource (award #2346701) and is part of the [National Research Platform](https://nationalresearchplatform.org/) Nautilus platform. The award was given for SDSU to invest in hardware to support instructional use-cases and hosts the hardware in its campus data center. It is a distributed Kubernetes-based compute environment supporting CPU and GPU workloads. The resources are available to researchers to use for free for both funded and unfunded researcher projects. SDSU is given priority before being available for other users of Nautilus. 

## Compute

SDSU hosts X Dell PowerEdge servers supporting TIDE.

| Node Type    | Quantity | Specifications |
|:-------------|:---------|:------|
| GPU          | 44       | PowerEdge R750XA<br />(2x) Intel Xeon Gold 6338 2G CPU, (40x) Nvidia L40, 48 GB RAM<br/>(4x) Nvidia A100 GPU, 80 GB RAM<br/>512 GB System RAM |
| Storage      | X        | PowerEdge R750<br/>(2x) Intel Xeon Gold 6336Y 2.4G, 24C/48T<br/>160 TB Storage<br/>256 GB System RAM |
| CPU          | X        | PowerEdge R750<br/>(2x) Intel Xeon Gold 6338 2G CPU, 32C/64T<br/>512 GB System RAM |


## Storage

Each user of TIDE is provided up to XXX GB of storage space accessible from JupyterHub. The space is provided by a [LINSTOR](https://linbit.com/linstor/) filesystem hosted on three storage nodes. It is recommended that persistent storage should be mantained elsewhere, ideally on the cloud.

## Networking

TIDE nodes make use of SDSU's [Science DMZ](https://iotlab.sdsu.edu/index.php/science-dmz/) providing 100G connectivity to [CENIC's](https://cenic.org/network/operations/maps) HPR network and 10G connectivity to its DC network.