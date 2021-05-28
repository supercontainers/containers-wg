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

Native OCI support in Singularity was one of the primary motivations for the rewrite in GoLang which was released in version 3.0.0.

Today, Singularity supports full OCI completely both in the runtime (via OCI command group) and the container image format (including push/pull support with all standard OCI registeries). This is done by leveraging the native OpenContainers GoLang libraries directly and thus we can guarantee absolute compatibility when running with the OCI command group.

For large HPC system effeciency, Singularity can squash and transform all OCI containers into single file SIF contianer images which has performance and usability benefits when running at scale over large parallel file systems.

Additionally, Singularity also supports unpriviledged OCI compatibility using the user kernel namespace but this would be limited as some aspects of CNI (Container Network Interface) would be limited without root (e.g. firewalls), but this is not generally needed for traditional HPC use-cases.
