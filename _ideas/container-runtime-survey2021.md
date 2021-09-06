# Containers Working Group for HPC Survey

A survey to get some data on container runtime would be nice. Not only which ones are used, but also what images are used (OCI) and how hardened the feelings are (use of multiple runtimes).
## Introduction

Welcome to the Containers Working Group for High Performance Computing Survey! This survey is provided by the [Containers Working Group](https://supercontainers.github.io/containers-wg/) as a community effort to better understand your use of container technologies. This survey is completely optional, and you are free to stop at any time. 
## Questions (early draft)

The `.5` questions are just asking about potential `other` answers we missed.

### About yourself

Just so that we can get a sense

| #  | Question | Type | Answers |
|:--:|:---------:|:----:|:---------------------:|
| A1 | What is your primary environment? | single | National Lab, academia, commercial, private research institution, other |
| A2 | What is your primary job? | single | Scientist, Linux Administrator, Research Software Engineer, Manager, other |
| A2.5 | Which function is not listed in A2? | text | |
| A3 | How do you rate your experience with **non-HPC containers**? | single | no experience, beginner, intermediate, expert |
| A4 | How do you rate your experience with **HPC containers**? | single | beginner, intermediate, expert |

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
| I1 | What is the method you are using to build a container image from scratch? | multi | Dockerfile, SIF recipe, other |
| I1.5 | What method did we miss to list in I1? | text | |
| I2 | Do you use higher-level abstractions on-top of the methods in I1? | multi | hpc-container-maker, repo2docker, spack, other |
| I2.5 | What method did we miss to list in I2? | text | |
| I3 | Once build, do you push the image to a central repository? | single | yes / no |
| I4 | What container repositories are you pushing builds to? | multi | dockerhub, gcr, ecr, quay, github, azure |

### Potentials

Without making the survey too long, we could also ask the following questions.

1. do you deal with different target architectures in your build process?
2. Do you use CI/CD for automated build and deploy?

