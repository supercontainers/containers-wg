---
layout: default
title: Charliecloud
nav_order: 4
parent: HPC Projects
---

# Charliecloud
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


The Charliecloud team considered OCI in the process of implementing a shim to support
Buildah builds. Notes are here:

 - https://hpc.github.io/charliecloud/command-usage.html#ch-run-oci
 - https://hpc.github.io/charliecloud/dev.html#oci-technical-notes

In summary, the philosophy and goals of OCI differ significantly from those of Charliecloud. Key differences include:

• OCI is designed to run services, while Charliecloud is designed to run scientific applications.
• OCI containers are persistent things with a complex lifecycle, while Charliecloud containers are simply UNIX processes.
• OCI expects support for a variety of namespaces, while Charliecloud supports user and mount, no more and no less.
• OCI expects runtimes to maintain a supervisor process in addition to user processes; Charliecloud has no need for this.
• OCI expects runtimes to maintain state throughout the container lifecycle in a location independent from the caller.

The group was also concerned that OCI had bad docs. The team had to do a lot of reverse engineering when the OCI specification was not clear. It's hard to critique something when it’s hard to understand what it is, especially in this case where details matter at lot.
