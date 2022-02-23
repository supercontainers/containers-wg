---
title: Containers Technologies for HPC Survey
discussion: https://github.com/supercontainers/containers-wg/discussions/39
---

# Containers Technologies for HPC Survey

## Welcome to the Container Technologies for High Performance Computing Survey!

### Purpose
This survey is being conducted by the [Containers Working Group](https://supercontainers.github.io/containers-wg/) with the goal of assessing the community's opinion about container technologies for scientific computing.  For more information, see the [Survey Plan](https://github.com/sk8forether/containers-wg/blob/main/_ideas/container-technology-survey-plan.md).

### About Us
The Containers Working Group is hosted in the [#containers-wg](https://hpc-containers.slack.com/archives/C023C51T8SG) channel of the hpc-containers Slack workspace.  We are a community of researchers interested in containers for High Performance Computing (HPC).  Feel free to [join the Slack](https://join.slack.com/t/hpc-containers/shared_invite/zt-ak9q6jw7-UZgpv7IJua5jCtJ_db_yAQ) and say hello!

### Informed Consent
This survey is completely optional, and you are free to stop at any time.

(This section needs more)

## Questions

### About Yourself (Demographics)

| #  | Question | Type | Answers |
|:--:|:---------:|:----:|:---------------------:|
| A1 | What is your primary environment? | single | National Lab, academia, commercial, private research institution, other |
| A2 | What is your primary job? | single | Scientist, Linux Administrator, Research Software Engineer, Manager, other |
| A2.5 | Which function is not listed in A2? | text | |
| A3 | How do you rate your experience with **non-HPC containers**? | single | no experience, beginner, intermediate, expert |
| A4 | How do you rate your experience with **HPC containers**? | single | no experience, beginner, intermediate, expert |

### Container Runtimes

This section is focused to ask about HPC workloads running on HPC container runtimes. While some might use docker to run a single-node container on their workstation, we do not consider it in this set because it is not traditionally used in HPC environment.


| #  | Question | Type | Answers |
|:--:|:---------:|:----:|:---------------------:|
| R1 | Which HPC container runtimes are supported on the system(s) you are working on? | multiple | Charliecloud, Shifter, Singularity, Sarus, Podman, other |
| R1.5 | Which HPC container runtimes are supported on the system(s) and not listed in R1? | text | |
| R2 | Which HPC container runtimes are you using for your daily workloads? | multiple | Charliecloud, Shifter, Singularity, Sarus, Podman, other |
| R2.5 | Which HPC container runtimes are you using for your daily workloads which are not listed in R2? | text | |
| R3 | Which HPC container runtimes are on your radar but not yet used? | multiple | Charliecloud, Shifter, Singularity, Sarus, Podman, other |
| R3.5 | Which HPC container runtimes are on your radar but not yet used and not listed in R3? | text | |
| R4 | Are you aware of the OCI runtime spec? | single choice | yes / no |
| R5 | Do you care about the OCI runtime spec? | single choice | yes / no |

### Images

The image section aims to get an overview of how users are interacting with container images (building, sharing, Storing)

| #  | Question | Type | Answers |
|:--:|:---------:|:----:|:---------------------:|
| I1 | What is the method you are using to build a container image? | multi | Dockerfile, SIF recipe, From scratch, other |
| I1.5 | What method did we miss to list in I1? | text | |
| I2 | Do you use higher-level abstractions on-top of the methods in I1? | multi | hpc-container-maker, repo2docker, spack, other |
| I2.5 | What method did we miss to list in I2? | text | |
| I3 | Once build, do you push the image to a central registry? | single | yes / no |
| I4 | What container registries are you pushing builds to? | multi | Docker Hub, Google Container Registry (gcr), Elastic Container Registry (ecr), Quay.io, GitHub Packages (ghcr,io), Azure |

### Potentials

Without making the survey too long, we could also ask the following questions.

1. Do you have to build your container image for different CPU architectures? 
2. Do you care about available accelerators(GPU, FPGA, specialized network hardware) when building your container image?
3. Do you use CI/CD for automated build and deploy?
4. What are you biggest challenges or pain points when using containers, or reasons that you don't use them (fill in the blank)
5. What do containers not do that you wish they could? What would be an ideal future?

