---
title: Dynamic Manifests
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

We might want to be able to assemble custom images on demand, meaning that
we can request a specific set of packages, and instead of building from source,
combine layers into a new manifest to pull dynamically.


## What ideas do we have for how to address these challenges?

We would likely need to start with a simple approach that attempts to create layers
with one software package installed per layer, and then have a method to be able
to assess a set of layers for compatibility. This gets challenging because the model
for a container is not amenable to a tree-like architecture (e.g., packages have dependencies)
but it might be possible.

## How do these ideas break down into...

### Already existing OCI specs?

### A new project (CNCF or OCI)

We would likely need a way to associate metadata with layers for the compatibility
assessment, and then a registry implementation that can accept (or build) layers
and then take requests for custom manifests.

## Questions?


## What pre-existing work or software can support these ideas?

The following works are relevant:

 - [ArchSpec](https://tgamblin.github.io/pubs/archspec-canopie-hpc-2020.pdf)

## Relevant OCI Issues

