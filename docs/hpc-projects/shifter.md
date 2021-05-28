---
layout: default
title: Shifter
nav_order: 4
parent: HPC Projects
---

# Sarus
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Overview

[Shifter](https://github.com/nersc/shifter) is an HPC Runtime that leverages parts of the Docker/OCI ecosystem but impelements
a runtime that is optimized for HPC systems. It is primarily maintained by NERSC at LBNL.
Shifter was the first HPC Container Runtime (as far as we are aware). It uses the standard Docker/OCI image 
format and uses a gateway service to pull and convert those images into an internal squash file that is used
by the runtime.  The gateway now uses stock CNCF/OCI tools for all of the image handling (e.g. skopeo, umoci,
oci-image-tool).  So assuming those tools are compliant, Shifter should be able to handle changes in the Spec.
While Shifter is compatible with the Image spec it pretty much ignores the runtime spec and does its own thing.

## Project Ideas

Some ideas we have discussed that are relevant to the OCI spec...

* Embedding more information in the metadata about the contents of the image and its system or other requirements (e.g. GPU capabilties, CPU requirements, MPI ABI comptability).
* Embedding more information about whether the image is designed to run as a single unpriveleged user.  Those could allow the image build process to apply additional tricks to ensure consistency (e.g. flatten permissions).

We have some papers that touch on thse topics.
