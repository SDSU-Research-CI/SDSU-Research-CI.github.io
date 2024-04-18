---
layout: default
title: Server Options
parent: Frequently Asked Questions
grand_parent: Instructional Cluster
nav_order: 1
description: ""
permalink: /instructionalcluster/faqs/serveroptions
---

# Server Options Page
When starting a new notebook from the Server Options page, there are many options to consider. What do these options mean and how does one select them appropriately? <br>

![Server Options Page](/images/instructionalcluster/faq-serveroptions1.png)

{: .note }
Unless training deep neural networks, running large models (e.g. AlphaFold), data mining, or performing similar research that warrants the need for GPU accelerated computing, **do not request a GPU**.

# GPUs, CPU Cores, and RAM
Let's explain what GPUs, CPU Cores, and RAM are and how they can be useful in the context of research and instruction. 

A **GPU (Graphical Processing Unit)** is a specialized processor designed to perform many simple calculations in parallel. *Requesting a GPU is often not necessary*, so research whether your use-case requires a GPU prior to launching a notebook. Here are some contexts where requesting a GPU can be appropriate:

- AI/ML *(e.g. training a deep neural network)*
- Scientific Computing *(e.g. weather modeling)*
- Data Science and Big Data Analytics *(e.g. data mining)*
- Medical Imaging *(e.g. 3D reconstructions)*

A **CPU core** is one of many small, yet powerful workers within a **CPU (Central Processing Unit)** designed for diverse and complex processing tasks in a sequential manner. Here are some contexts where requesting 2+ CPU cores is advantageous:

- Genomics and Bioinformatics *(e.g. protein-protein interactions)*
- Numerical Simulations *(e.g. combinatorial optimization)*
- Parallel Programming *(e.g. multithreading)*

**RAM (Random Access Memory)** is the short-term memory of a computer. RAM is designed to store data and program instructions that are currently being used by the computer's CPU. Persistent forms of memory like hard drives and SSDs retain data even when the power is turned off, whereas RAM gets wiped. Here are some contexts where requesting 8+ GB of RAM is advantageous:

- AI/ML *(e.g. natural language processing)*
- Big Data Analytics *(e.g. data mining)*
- Geospatial Analysis and Remote Sensing *(e.g. land cover classification)*

