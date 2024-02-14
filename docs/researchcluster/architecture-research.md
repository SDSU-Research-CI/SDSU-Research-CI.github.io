---
layout: default
title: Achitecture Details
parent: Research Cluster
nav_order: 5
has_children: false
description: ""
permalink: /researchcluster/Achitecture
---

{: .note }
This page is currently under construction. Information will be updated soon

# Architecture

[TIDE](https://tide.sdsu.edu/), is an NSF-backed resource (award #2346701) and is part of the [National Research Platform](https://nationalresearchplatform.org/) Nautilus platform. The aware was given for SDSU to invest in hardware to support instructional use-cases and hosts the hardware in its campus data center. It is a distributed Kubernetes-based compute environment supporting CPU and GPU workloads. The resources are available to researchers to use for free for both funded and unfunded researcher projects. SDSU is given priority before being available for other users of Nautilus. 

## Compute

SDSU hosts 27 Dell PowerEdge servers supporting TIDE.

| Node Type    | Quantity | Specifications for each Node |
|:-------------|:---------|:------|
| GPU          | 17       | PowerEdge R760<br/> (2x) Intel Xeon SIlver 4410Y 2G, 12C/24T <br/> (4x) Nvidia L40, 48 GB RAM<br/> 512 GB System RAM |
| GPU          | 1        | PowerEdge R750XA<br />(2x) Intel Xeon Gold 6338 2G CPU, 32C/64T<br/>(4x) Nvidia A100 GPU, 80 GB RAM<br/>512 GB System RAM |
| CPU          | 6        | PowerEdge R760<br/>(2x) Intel Xeon Gold 6430 2.1G, 32C/64T <br/> 768 GB System RAM |
| Storage      | 3        | PowerEdge R760<br/> (3x) Intel Xeon Gold 6442Y 2.6G, 24C/48T <br/> 240 TB Storage<br/>256 GB System RAM |


## Storage

Each user of TIDE is provided up to 50 GB of storage space accessible from JupyterHub but more storage can be granted upon request. The space is provided by a [LINSTOR](https://linbit.com/linstor/) filesystem hosted on three storage nodes. It is recommended that persistent storage should be mantained elsewhere, ideally on the cloud.

## Networking

Nautilus requires a Science DMZ network architecture to integrate into the fabric. SDSU has implemented an instructional and enterprise Science DMZ architecture to isolate research traffic using 2×10 Gb CENIC CalREN-HPR uplinks. Therefore, TIDE nodes make use of SDSU's [Science DMZ](https://iotlab.sdsu.edu/index.php/science-dmz/) providing 100G connectivity to [CENIC's](https://cenic.org/network/operations/maps) HPR network and 10G connectivity to its DC network. 

Note that for traffic not destined for CalREN-HPR, a 20 Gb interconnect is used to direct traffic over SDSU’s 100 Gb CENIC CalREN-DC connection.