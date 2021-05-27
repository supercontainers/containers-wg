---
title: A Building Service
---

---

{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## What are the challenges that we are trying to solve?

 - There is no standard way to build and provision images for HPC. Registries do not natively include a builder service.

We gripe a lot about not being able to build without root. The OCI distribution spec doesn't say anything about building, but notably, Docker Hub (and others) provide a build service. Is this within scope of OCI? Or could something generalized be designed that allows for it?

## What ideas do we have for how to address these challenges?

 - We could supplement a current distribution spec with additional endpoints to support building, or requesting builds. This could be considered an extension to the distribution spec. The endpoints would consider architecture and other metadata for the build, and the user would be delivered a container upon completion.
 - In the second case, perhaps there could be push enabled for a recipe type (e.g., Singularity or Dockerfile) and then support for a callback function that a registry implementer could add - an HPC center would have that callback hit some build node to handle the build. I suppose that there is nothing from stopping anyone from adding more functionality to an OCI registry, but if there were a standard way of describing it, it could be good for the community. If not a building service, can OCI say anything about building?

## How do these ideas break down into...

### Already existing OCI specs?

 - An extension to a distribution spec could define (optional) endpoints for building. Of course the implementation is up to the implementer.
 - The distribution spec that supports pushing build recipes could then also support a push callback that would take the recipe and request a build for it. The implementation could choose how to trigger a build.

### A new project (CNCF or OCI)

I resolved an addition to our notes with this comment (and this should be expanded upon):

> We have a paper around this topic that is still under review.  We had some ideas around additional metadata for an image that would give some additional hints.  For example, can the permissions for the files in the image effectively be flattened (from a user perspective).


## Questions?


## What pre-existing work or software can support these ideas?

## Relevant OCI Issues

