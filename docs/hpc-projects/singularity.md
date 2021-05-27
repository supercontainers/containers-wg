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

The Singularity Project was not developed with OCI in mind, but eventually
added an [oci command group](https://sylabs.io/guides/3.7/user-guide/oci_runtime.html) to
give some support for the run time spec. There is a project called [Singularity CRI](https://sylabs.io/guides/cri/1.0/user-guide/index.html)
that according to Hpcng, likely won't be revived based on feedback. Finally,
the company Sylabs that supports Singularity created their own [library API](https://cloud.sylabs.io/library)
that is not related to the distribution spec, and the original [Singularity Registry](https://singularityhub.github.io/sregistry/)
followed suit to implement it so that the singularity client could push directly to it.

## Project Ideas

Ideally, there would be a registry implementation for Singularity that conforms
to the OCI spec, which could be accomplished by way of using an existing registry base with
custom artifacts (SIF blobs) or a custom implementation. For example, @vsoch made
[Django OCI](https://vsoch.github.io/django-oci/) to support this use case, and 
implemented in the Python Django framework so it could be worked on by researchers
and anyone familiar with scientific programming.
