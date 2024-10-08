---
layout: default
title: Available Container Images
parent: Instructional Cluster
nav_order: 6
has_children: false
description: ""
permalink: /instructionalcluster/images
---

# Available Container Images

JupyerHub makes use of a container image to execute your code/commands. 
You must use a container image that contains the software you wish to use. 
We provide container images from [Jupyter Docker Stacks](https://jupyter-docker-stacks.readthedocs.io/en/latest/using/selecting.html#core-stacks) and [NRP Scientific Images](https://gitlab.nrp-nautilus.io/nrp/scientific-images). 
Additional container images can be created for specific needs.

All images include NVIDIA GPU support and will provide access to GPU resources if requested during [container launch](/instructionalcluster/students/launchcontainer).

## General Container Images

The following general purpose containers are available for use.

| Name                  | Image Repo          | Container Image Tag  | Software            |
|:----------------------|:--------------------|:---------------------|:--------------------|
| Jupyter Stack Minimal Notebook     | [minimal-notebook](https://github.com/jupyter/docker-stacks/tree/main/images/minimal-notebook) | quay.io/jupyter/minimal-notebook:2024-07-29 | Ubuntu 22.04.4 <br/> JupyterLab 4.2.4 <br/> Python 3.11.9 <br/> Git 2.34.1 <br/> vi <br/> nano <br/> wget <br/> curl <br/> unzip <br/> tzdata |
| Jupyter Stack R Notebook           | [r-notebook](https://github.com/jupyter/docker-stacks/tree/main/images/r-notebook) | quay.io/jupyter/r-notebook:2024-07-29 | Everything in minimal-notebook <br/><br/>  The R interpreter and base environment <br/><br/>  IRKernel to support R code in Jupyter notebooks <br/><br/>  tidyverse packages from conda-forge <br/><br/>  caret, crayon, devtools, forecast, hexbin, htmltools, htmlwidgets, nycflights13, randomforest, rcurl, rmarkdown, rodbc, rsqlite, shiny, tidymodels, unixodbc packages from conda-forge |
| Jupyter Stack SciPy Notebook       | [scipy-notebook](https://github.com/jupyter/docker-stacks/tree/main/images/scipy-notebook) | quay.io/jupyter/scipy-notebook:2024-07-29 | Everything in minimal-notebook <br/><br/>  altair, beautifulsoup4, bokeh, bottleneck, cloudpickle, conda-forge::blas=*=openblas, cython, dask, dill, h5py, jupyterlab-git, matplotlib-base, numba, numexpr, openpyxl, pandas, patsy, protobuf, pytables, scikit-image, scikit-learn, scipy, seaborn, sqlalchemy, statsmodel, sympy, widgetsnbextension, xlrd packages <br/><br/>  ipympl and ipywidgets for interactive visualizations and plots in Python notebooks <br/><br/>  Facets for visualizing machine learning datasets |
| Jupyter Stack Tensorflow Notebook  | [tensorflow-notebook](https://github.com/jupyter/docker-stacks/tree/main/images/tensorflow-notebook) | quay.io/jupyter/tensorflow-notebook:cuda-2024-07-29 | Everything in scipy-notebook and its ancestor images <br/><br/>  TensorFlow machine learning library <br/><br/>  Jupyter Server Proxy to support TensorBoard |
| Jupyter Stack PyTorch Notebook     | [pytorch-notebook](https://github.com/jupyter/docker-stacks/tree/main/images/pytorch-notebook) | quay.io/jupyter/pytorch-notebook:cuda12-2024-07-29 | Everything in scipy-notebook and its ancestor images <br/><br/> pytorch machine learning library (torch, torchaudio and torchvision) |
| Jupyter Stack Julia Notebook       | [julia-notebook](https://github.com/jupyter/docker-stacks/tree/main/images/julia-notebook) | quay.io/jupyter/julia-notebook:2024-07-29 | Everything in minimal-notebook <br/><br/>  The Julia compiler and base environment <br/><br/>  IJulia to support Julia code in Jupyter notebook <br/><br/>  Pluto.jl reactive Julia notebook interface, made accessible with jupyter-pluto-proxy <br/><br/>  HDF5 package |
| Jupyter Stack Datascience Notebook | [datascience-notebook](https://github.com/jupyter/docker-stacks/tree/main/images/datascience-notebook) | quay.io/jupyter/datascience-notebook:2024-07-29 | Everything in the scipy-notebook, r-notebook, and julia-notebook images and their ancestor images <br/><br/>  rpy2 package |
| NRP R Studio Notebook              | [r-studio](https://gitlab.nrp-nautilus.io/nrp/scientific-images/rstudio) | gitlab-registry.nrp-nautilus.io/nrp/scientific-images/rstudio:cuda-v1.4.1 | Everything in r-notebook <br/><br/>R studio |

The following diagram shows the relationships of the above container images.

```mermaid
graph LR;
    A[minimal-notebook]
    B[r-notebook]
    C[scipy-notebook]
    D[tensorflow-notebook]
    E[datascience-notebook]
    F[pytorch-notebook]
    G[julia-notebook]
    H[r-studio]

    A --> B
    A --> C
    A --> G
    B --> H
    B --> E
    C --> E
    C --> D
    C --> F
    G --> E
```

## Custom Container Images

| Name                  | Image Repo          | Container Image Tag | Software             |
|:----------------------|:--------------------|:--------------------|:---------------------|
| Eclipse C/C++ Desktop       | [eclipse-notebook](https://github.com/SDSU-Research-CI/eclipse-notebook) | ghcr.io/sdsu-research-ci/eclipse-notebook:v1.0 | Everything in minimal-notebook <br/><br/> Eclipse IDE for C/C++ Developers 2024-06 release for Linux x86_64 <br/><br/> build-essential <br/><br/> Jupyter Desktop Proxy <br/><br/> xfce desktop |
| Kube Notebook               | [kube-notebook](https://github.com/SDSU-Research-CI/kube-notebook) | ghcr.io/sdsu-research-ci/kube-notebook:v1.0 | Everything in minimal-notebook  <br/><br/> rclone  <br/><br/> kubectl  <br/><br/> Jupyter Desktop Proxy  <br/><br/> xfce desktop |
| SageMath Notebook           | [sagemath-notebook](https://github.com/SDSU-Research-CI/sagemath-notebook) | ghcr.io/sdsu-research-ci/sagemath-notebook:v1.0 | Everything in scipy-notebook <br/><br/> SageMath Kernel |
| GIS Notebook                | [gis-notebook](https://github.com/SDSU-Research-CI/gis-notebook) | ghcr.io/sdsu-research-ci/gis-notebook:v1.0 | Everything in pytorch-notebook <br/><br/> beautifulsou, boto3, eo-learn, geopandas, geoplot, laspy, lightgbm, natsort, netcdf4, networkx, psycopg2, pysal, rasterio, rclone, selenium, sentinelhub, xeus-python |
| Health Informatics Notebook | [health-informatics-notebook](https://github.com/SDSU-Research-CI/health-informatics-notebook) | ghcr.io/sdsu-research-ci/health-informatics-notebook:v1.0 | Everything in scipy-notebook <br/><br/> biopython, pytest, fastp, samtools, bwa, varscan, bcftools, mummer, ensembl-vep, goalign, gotree, modeltest-ng, raxml-ng, spades, mafft |
| Astro Notebook              | [astro-notebook](https://github.com/SDSU-Research-CI/astro-notebook) | ghcr.io/sdsu-research-ci/astro-notebook:v1.5 | Everything in scipy-notebook <br/><br/> astropy, astroquery, photutils, emcee, corner, fsps, lxml, reportlab <br/><br/> SKIRT <br/><br/> PTS |
| LLM Notebook                | [llm-notebook](https://github.com/SDSU-Research-CI/LLM-Notebook) | ghcr.io/sdsu-research-ci/llm-notebook:v1.7 | Everything in pytorch-notebook <br/><br/> bitsandbytes, transformers, peft, accelerate, trl,  openai, PyAudio, portaudio <br/><br/> FastChat <br/><br/> Ollama |

The following diagram shows the relationships between the general and custom container images.

```mermaid
graph LR;
    A[minimal-notebook]
    B[scipy-notebook]
    C[pytorch-notebook]
    D[eclipse-notebook]
    E[kube-notebook]
    F[sagemath-notebook]
    G[gis-notebook]
    H[health-informatics-notebook]
    I[astro-notebook]
    J[llm-notebook]

    A-->B
    A-->D
    A-->E
    B-->C
    B-->F
    B-->H
    B-->I
    C-->G
    C-->J
```