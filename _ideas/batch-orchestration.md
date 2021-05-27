---
title: Batch Orchestration
---

---

{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## What are the challenges that we are trying to solve?

 - There is no standard or tools for orchestrating a pull and container deployment to HPC nodes.
 - We would like to have a scalable launch mechanism.

Right now, if you were to pull a container on an HPC system, something like docker (or more realistically, podman) would be running the command on every single node. This is obviously a bad idea! So we would want a single orchestrator to pull (once) an image, and then distribute to nodes. 

## What ideas do we have for how to address these challenges?

We would probably want a design that would be supported as a plugin for the most popular batch
schedulers, and one that would be able to then link into some kind of
[hook](https://github.com/opencontainers/runtime-spec/blob/master/config.md#posix-platform-hooks)
for a pull, to either retrieve the container from a cache, or (before the job script
is run) to distribute the container to the node, and then still have some kind of hook
that knows how to look for the container locally first. It should be possible for
containers to be supported natively in these schedulers.

## How do these ideas break down into...

### Already existing OCI specs?

Likely we would need to take advantage of some kind of hook that is defined by an existing spec.

### A new project (CNCF or OCI)

It would be fabulous to have a spec that defines this container orchestration for HPC as a part of OCI.
It could be relevant to other kinds of schedulers that generally need to do similar scaling.

## Questions?

 - We currently use tricks like flattening/squashing images so that we can have a more scalable launch.  What aspects of this should be a part of the image space or dealt with in the runtime is unclear to me.

## What pre-existing work or software can support these ideas?

## Relevant OCI Issues

