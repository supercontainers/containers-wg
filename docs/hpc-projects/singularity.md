---
layout: default
title: Singularity
nav_order: 2
parent: HPC Projects
---

# Singularity
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Overview

The Singularity Project was not originally developed with OCI in mind, but 
with the migration to GoLang for versions 3.0.0 and up, using the same libraries as 
other container and orchestration tools provided an opportunity to do so, as it would be easier
to use the OCI community developed libraries in GoLang.
This first meant that the project added an [oci command group](https://sylabs.io/guides/3.7/user-guide/oci_runtime.html) to
give some support for the runtime spec. Support for pulling from a Docker registry was already
implemented in the 2.x series, and this was done by way of the Docker API (e.g., using
image manifests from an OCI registry that conforms to the distribution spec). It's not
clear if this could be called OCI compatibility, but having this ability to pull
from Docker Hub and other oci registries with the `docker://` unique resource identifier
is likely one of the features that made Singularity quickly adopted and easy to use -
users did not have to always re-write their recipes, but could get a Singularity container
and a Docker container from a Dockerfile.

Singularity in the 3.x series was able to add an `oras://` [endpoint](https://sylabs.io/guides/3.7/user-guide/cli/singularity_push.html), 
which allowed for upload (push) of a Singularity container to an OCI registry, and then subsequent pull.
From a maintainer of the Singularity software:

> With 3.7 it is known to work with Azure Container Registry, and the docker registry:2 registry server. It will also work with all other registries that correctly implement the distribution-spec and accept arbitrary mediaTypes or whitelist SIF mediaTypes specifically.
> With 3.8 it is known to also work with Harbor and GitLab Container Registry (as a workaround is added for them not accepting a null config).

Docker Hub is not supported as it only accepts docker/OCI containers, and Quay.io would need to add SIF to the whitelist of mediaTypes they accept.
So, although Singularity is not compatible with every OCI compliant registry, the fact that it is compatible with some
is an indicator that it could be compatible with more in the future. The company Sylabs that supports Singularity created their own [library API](https://cloud.sylabs.io/library) that is not related to the distribution spec, and the original [Singularity Registry](https://singularityhub.github.io/sregistry/) followed suit to implement it so that the singularity client could push directly to it.
It would be interesting or perhaps useful if all of these registries could conform to the OCI
distribution specification.

There is a project called [Singularity CRI](https://sylabs.io/guides/cri/1.0/user-guide/index.html)
that aimed to "explore interaction between the Kubernetes and HPC worlds," but funding ran out and there
was not enough interest to keep the project going. It was hugely challenging because there are
some mismatches between Singularity concepts and Kubernetes concepts that make it arduous to maintain through new K8s versions.
However, if you look at the archived repository [README](https://github.com/sylabs/singularity-cri) you
will see that the project is open to new maintaienrs and picking up again if there is community interest. 


## Project Ideas

Ideally, in the future it will be possible to push Singularity containers to more OCI compliant registries,
and perhaps this would eliminate the need for a custom library endpoint. But it also could
be useful for the traditional Singularity registries to be able to implement OCI and then
add additional useful features specific to Singularity on top of that. The library API is not
public so this cannot be a project for this community, but Singularity Registry server is public,
and @vsoch made [Django OCI](https://vsoch.github.io/django-oci/) to support this use case. It is
implemented in the Python Django framework so it could be worked on by researchers
and anyone familiar with scientific programming. Thus, if there is interest in creating an OCI
distribution spec registry for Singularity containers (with some extra features for HPC) either
an existing ORAS compatible registry could be used as a starting point, or any of these existing
projects in Python.
