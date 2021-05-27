---
layout: default
title: The Runtime Spec
nav_order: 3
has_children: true
parent: OCI Specs and Projects
---


# The Runtime Spec
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Overview

The [runtime specification](https://github.com/opencontainers/runtime-spec/blob/master/spec.md) is another description of an interaction, but this time it's with a container binary.  Specifically, this means the execution environment, configuration, and lifecycle of a container.

**What do you mean by execution environment?**

What is the host operating system of your computer, Windows? Linux? 
These are different execution environments that come with different rules and standards for generating (what feels like) the same running container. 
If you look at the [runtime specification](https://github.com/opencontainers/runtime-spec/blob/master/spec.md) entry page, you'll actually find that there is a different specification file for each base operating system.

**Why do we need runtime specifications?**

As a user, you expect a container run on a Windows machine to generally feel like and act the same as a container run on a Linux host. 
The runtime specifications are catered toward this goal, with different configuration files (called config.json) to drive the creation, execution enviroinment, and actions for the container.

**How might I contribute?**

You might have an entirely different operating system or technology that you want to explore running containers on, in which case you would want to contribute a new specification. 
You might find that there is an ambiguity or bug for one runtime, and ask a question about how to work on it.

