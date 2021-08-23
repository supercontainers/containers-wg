# Container Runtime Survey 2021

A survey to get some data on container runtime would be nice. Not only which ones are used, but also what images are used (OCI) and how hardened the feelings are (use of multiple runtimes).

## Questions (early draft)

### Container Runtimes

| #  | Question | Type | Answers |
|:--:|:---------:|:----:|:---------------------:|
| R1 | Which HPC container runtimes are supported on the system(s) you are working on? | multiple-choice | Charliecloud, Shifter, Singularity, Sarus, Podman, other |
| R1.5 | Which HPC container runtimes are supported on the system(s) and not listed in R1? | text | |
| R2 | Which HPC container runtimes are you using for your daily workloads? | multiple-choice | Charliecloud, Shifter, Singularity, Sarus, Podman, other |
| R2.5 | Which HPC container runtimes are you using for your daily workloads which are not listed in R2? | text | |
| R3 | Which HPC container runtimes are on your radar but not yet used? | multiple-choice | Charliecloud, Shifter, Singularity, Sarus, Podman, other |
| R3.5 | Which HPC container runtimes are on your radar but not yet used and not listed in R3? | text | |

### Images

| #  | Question | Type | Answers |
|:--:|:---------:|:----:|:---------------------:|
| I1 | What is the method you are using to build a container image from scratch? | multi | Dockerfile, SIF recipe, other |
| I1.5 | What method did we miss to list in I1? | text | |
| I2 | Do you use higher-level abstractions on-top of the methods in I1? | multi | hpc-container-maker, repo2docker, spack, other |
| I2.5 | What method did we miss to list in I2? | text | |
