---
title: Layer Annotation
---

---

{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## What are the challenges that we are trying to solve?

 - There isn't enough information about individual layers to understand disk space needs 
 - There isn't enough information (or registry support) to assemble and pull custom image mainfests.

When we decompress blobs and plop them into a new container (typically Singularity on HPC) it’s a little bit of a “let’s wait and see” scenario to see if we will have enough space on the filesystem. The sizes on Docker Hub reported the compressed layer sizes, and not the actual contents. Would it be possible to calculate the size of a layer when it’s being created, and then keep it alongside the .tar.gz, or even in a header somewhere? It would be handy to be able to run a script that tells us:

 - The total size of the image when it will be decompressed
 - The additional size of compressed layers that needs to be downloaded (I might already have layers locally)

## What ideas do we have for how to address these challenges?

If individual layers could have annotations, we could explore ideas of assembling a custom
set of layers on demand. For example, a user could build a custom container with software inside
(assuming layer compatibility) without needing to build the image. 


## How do these ideas break down into...

### Already existing OCI specs?


### A new project (CNCF or OCI)


## Questions?


## What pre-existing work or software can support these ideas?

## Relevant OCI Issues

 - [#235](https://github.com/opencontainers/distribution-spec/issues/235)

