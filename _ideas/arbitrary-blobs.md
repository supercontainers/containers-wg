---
title: Pushing Arbitrary Blobs
---

---

{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## What are the challenges that we are trying to solve?

 - Any OCI registry should be able to support custom content types.

Artifacts and custom content types for image manifests are already under discussion.

## What ideas do we have for how to address these challenges?

[This issue here](https://github.com/opencontainers/distribution-spec/issues/252) shows 
the idea of just uploading a blob with a descriptor without a manifest, and arguably
this could be done for a container binary like Singularity.

A comment from Steve Lasker:

> When pushing a collection of blobs, the question around what's the context or packaging of that collection. The idea that you can create one or more blobs, (with or without a config), and add blobs (or a collection of blobs) to existing content is the premise around [https://github.com/opencontainers/artifacts/pull/29](https://github.com/opencontainers/artifacts/pull/29) as the prelude to what we'd like to do with [https://github.com/opencontainers/artifacts/pull/37](https://github.com/opencontainers/artifacts/pull/37) as a superset of the capabilities.


## How do these ideas break down into...

### Already existing OCI specs?


### A new project (CNCF or OCI)

 - Given that we have support for pushing arbitrary blobs, we could easy create an OCI compliant Singularity Registry.
 - Given that we have support for pushing arbitrary blobs, we can imagine registries of other types that might support HPC. I could imagine a registry of environments, where the requester would be able to download and activate said environment (spack environments are an example, and we would want a "spack environment hub" - so there would be some config files and a few tarballs) and it would be specific to their architecture and host needs.

## Questions?


## What pre-existing work or software can support these ideas?

