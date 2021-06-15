---
title: Container Metadata
discussion: https://github.com/supercontainers/containers-wg/discussions/6
---

---

{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## What are the challenges that we are trying to solve?

 - Containers are not able to provide enough metadata about binaries / libraries inside to assess compatibility with a host.
 - Existing container metadata does not come in any standard format that can be easily parsed.  HPC developers often must parse build files, scripts, image layers, etc. (when available) to determine the contents.
 - Configuration of software and environment variables can affect reproducibility but are rarely captured in metadata. 

Containers can seem like black boxes. But for running a container on HPC, we need to know about:

1. attributes of the applications and binaries that are contained inside
2. what requirements might be for running (e.g. hardware, memory, disk space)
3. potentially other information that could be used by a resource manager or scheduler to know if it can run a container using this image.

## What ideas do we have for how to address these challenges?

**TODO** add ideas from papers below?

## How do these ideas break down into...

### Already existing OCI specs?


### A new project (CNCF or OCI)


## Questions?


## What pre-existing work or software can support these ideas?

Existing technologies that address parts of these ideas (incompletely):
 - Docker provides [Object labels](https://docs.docker.com/config/labels-custom-metadata/) that are optional for images, containers, volumes, and more (such as the `LABEL` command within the Dockerfile).
 - Singularity definition files provide a few relevant environments

The following works are relevant:

 - [ArchSpec](https://tgamblin.github.io/pubs/archspec-canopie-hpc-2020.pdf)
 - [A Case for Portability and Reproduibility of HPC Containers](https://www.canopie-hpc.org/wp-content/uploads/2019/12/ajy-sc19_canopie-PRCHPC.pdf)

## Relevant OCI Issues

