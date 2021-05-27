---
layout: default
title: Project runc
nav_order: 3
has_children: true
parent: OCI Specs and Projects
---

# Runc
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Overview

The project [opencontainers/runc](https://www.github.com/opencontainers/runc) is perhaps one of the most important of all the OCI projects. 

**Why do we need runc?**

This project includes code used by container runtimes to implement the OCI specification. 
You can think of the runtime specification as a set of rules, and runc the actual implementation of those rules that you will find in code bases for popular container software.

**How might I contribute?**

It could be the case that you find a security hole in a container runtime that is possibly related to, or might be addressed by runc.
Realistically, if you want to change runc, the first step would be to start discussion around the runtime specification itself.
