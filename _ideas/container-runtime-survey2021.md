# Containers Working Group for HPC Survey 2021

A survey to get some data on container runtime would be nice. Not only which ones are used, but also what images are used (OCI) and how hardened the feelings are (use of multiple runtimes).

## Questions (early draft)

The `.5` questions are just asking about potential `other` answers we missed.

### About yourself

Just so that we can get a sense

| #  | Question | Type | Answers |
|:--:|:---------:|:----:|:---------------------:|
| A1 | What is your primary environment? | single | National Lab, academia, commercial, other |
| A2 | What is your function? | single | Scientist, Admin, RSE, other |
| A2.5 | Which functionis not listed in A2? | text | |
| A3 | How do you rate your experience with **non-HPC containers**? | single | beginner, intermediate, expert |
| A4 | How do you rate your experience with **HPC containers**? | single | beginner, intermediate, expert |

### Container Runtimes

This section is focused to ask about HPC workloads running on HPC container runtimes. Some might use docker to run a single-node container on their workstation - we consider that out of scope because it is hard to differentiate between a service workloads and a HPC workload.


| #  | Question | Type | Answers |
|:--:|:---------:|:----:|:---------------------:|
| R1 | Which HPC container runtimes are supported on the system(s) you are working on? | multiple | Charliecloud, Shifter, Singularity, Sarus, Podman, other |
| R1.5 | Which HPC container runtimes are supported on the system(s) and not listed in R1? | text | |
| R2 | Which HPC container runtimes are you using for your daily workloads? | multiple | Charliecloud, Shifter, Singularity, Sarus, Podman, other |
| R2.5 | Which HPC container runtimes are you using for your daily workloads which are not listed in R2? | text | |
| R3 | Which HPC container runtimes are on your radar but not yet used? | multiple | Charliecloud, Shifter, Singularity, Sarus, Podman, other |
| R3.5 | Which HPC container runtimes are on your radar but not yet used and not listed in R3? | text | |
| R4 | Do you aware of the OCI runtime spec? | single choice | yes / no |
| R5 | Do you care about the OCI runtime spec? | single choice | yes / no |

### Images

The image section aims to get an overview of how folks are dealing with images

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

