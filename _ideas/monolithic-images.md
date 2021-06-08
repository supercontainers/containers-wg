---
title: Monolithic Image Layer
discussion: https://github.com/supercontainers/containers-wg/discussions/12
---

---

{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## What are the challenges that we are trying to solve?

It's difficult to utilize layered OCI images directly on HPC systems.

Singularity currently supports the ability to push/pull Singularity Image Format (SIF) images to/from OCI registries implementing the [OCI Distribution Specification](https://github.com/opencontainers/distribution-spec/blob/main/spec.md). This was developed and implemented in accordance with the [OCI Artifact Authors Guidance](https://github.com/opencontainers/artifacts/blob/master/artifact-authors.md) document. This document acknowledges that there is a desire to store artifacts that are not OCI container images and uses Helm and Singularity as examples.

Although Helm and Singularity have protocols that were purpose-built for storing and retrieving their respective artifacts, many users would prefer to have a single solution for the storage of artifacts. As a result, both Helm and Singularity have implemented the ability to store artifacts (Helm Charts, SIF images) within OCI registries.

It’s interesting to note that, unlike Helm, Singularity is storing container images, which is the very thing that OCI Registries were purposely built for in the first place. So why doesn’t Singularity simply use an OCI format as its native image format? And more broadly, why is it that HPC systems don’t use OCI images directly?

## What ideas do we have for how to address these challenges?

OCI images were optimized for the environment they operate in. By using layers, OCI images allow for efficient storage of container images when multiple images share the same base image. Container runtimes can minimize the amount of network bandwidth they consume by caching frequently used layers on the node they are installed on. Like anything, these benefits come with compromises. If local storage is not available, all layers of an image must be retrieved on each container startup. Layers must be extracted to a writable filesystem that is available to the node, increasing startup time and complexity in an HPC environment

In HPC, the layered image format used by OCI images can be difficult to work with. HPC workloads often leverage multiple compute nodes concurrently, and because of this local storage is sometimes eschewed in favor of parallel storage systems that are connected to multiple nodes. While OCI layers may be cached on parallel storage and extracted onto the same parallel storage, this does not scale well when hundreds or thousands of compute nodes are attempting to start containers at the same time.

For HPC computing environments, an extra step must be added to the workflow process. OCI images are converted into monolithic images before the runtime attempts to start a container. When a container image is built from an OCI image source, Singularity converts the layers of the image to a SIF image which includes a monolithic root filesystem compressed with SquashFS. Shifter’s Image Gateway utilizes a similar approach.

To look at this another way, there is little benefit from OCI layers in HPC. But clearly, OCI Registries are useful and it’s worth asking the question of what the least amount of change we could introduce to existing specifications to get the largest amount of benefit. Given the arguments above, I suggest that we, as an HPC community, might advocate for monolithic image support in OCI registries.

## How do these ideas break down into...

The OCI image spec currently defines several layer types which are all .tar files with or without compression [here](https://github.com/opencontainers/image-spec/blob/master/layer.md)). If a type such as `application/vnd.XXX.image.layer.v1.squashfs` was added, we could leverage the existing manifest/config scaffolding that make up OCI images, with the added ability that the filesystem blob retrieved from the OCI registry would be immediately useful on HPC systems.

### Already existing OCI specs?

- [OCI Image Format Specification](https://github.com/opencontainers/image-spec/blob/master/spec.md), in particular the [Image Layer Filesystem Changeset](https://github.com/opencontainers/image-spec/blob/master/layer.md) section.

### A new project (CNCF or OCI)

## Questions?

## What pre-existing work or software can support these ideas?

## Relevant OCI Issues
