---
title: Containers Working Group for HPC Survey
discussion: https://github.com/supercontainers/containers-wg/discussions/39
---

# Container Technologies Survey Plan

## Objectives
Purpose of survey: To assess the community's opinion about container technologies for HPC specifically, and scientific computing generally.

### Main
1. Determine the makeup of the community of people using container technologies for scientific computing
2. Determine the popularity of different container technologies for scientific computing
3. Assess the opinions about current container technologies for scientific computing
4. Assess who consumes containers vs. who develops containers vs. who configures container runtimes, registries, and other container technologies

### Optional
5. Assess the opinions about current OCI specification implementations
6. Collect opinions on requested improvements to the OCI specification

## Population and Sampling

## Population

Our **target population** is all people developing, maintaining, or in any way using container technologies for HPC and/or scientific applications in
any setting.  This includes:
* Research Software Engineers (RSEs)
* Computational Scientists
* Sysadmins (variety of industries)
* Researchers (variety of disciplines)
* Students (variety of disciplines)
* Software Engineers (variety of industries)
* Data Scientists (variety of industries)
* and possibly others

It is important to note that the entire population of folks using container technologies is much broader than the target population because of the
broad use of container technologies in a wide variety of industries, academia, and government applications.  Ultimately we desire our **sample population**
to consist of the larger group of diverse people using container technologies internationally.  Our ultimate target population may contain individuals who
are not aware of OCI.

## Sampling

### Sampling Method
For the initial run of this survey, we will use convenience sampling.  In potential future iterations of the survey, we may consider random sampling options.

Convenience sampling is simplest (and thus most common for online surveys) because anyone who lands on the website can take the survey, and the survey can be widely shared unreservedly.  The major downside is that the results cannot reliably generalize about the larger population (relevant to Objectives 1 and 2), and thus limits the statistical methods that can be used to analyze the data [\[1, 2, 3\]](#references).  Since we will be using this method, we will just acknowledge the limitation when presenting results.

In the future, if we were to select a random sampling method, simple random sampling or cluster sampling might be beneficial to be able to reliably generalize about the population [\[1, 2\]](#references).

### Sampling Error
* We will need to measure nonresponse error and the numbers of people who do not complete the survey once started
* See the [Decreasing Error](#decreasing-error) section for reducing these types of error

## Data Analysis Plan

### Expected Data Collection Based On Objectives

| **[Main Objectives](#main)** | **Data Type** | **Data To Collect** |
| ----------- | ----------- | ----------- |
| 1. Determine the makeup of the community of people using container technologies scientific computing | Nominal | personal demographic categories (gender, ethnicity, etc.) and professional categories (industry, job title, and/or student status) |
| 2. Determine the popularity of different container technologies for scientific computing | Nominal | list of container technologies and locations container technologies are used (see [Focus of Questions](#focus-of-questions)), what type of applications are being run (science, HPC, other, etc.)|
|  | Ratio | total number of users of each container technology within sample, breakdown of container technology used by application and/or industry |
| 3. Assess the opinions about current container technologies for HPC | Ordinal | level of experience with HPC, level of experience with specific container technologies used, level of satisfaction with container technologies used |
|   | Ratio | total number of people in sample who are using container technologies for HPC (including breakdown for various levels of experience), total numbers of people in sample at various levels of experience with container technologies, total number of people at various satisfaction levels for container technologies |
| 4. Assess who consumes containers vs. who develops containers vs. who configures container runtimes, registries, and other container technologies | Nominal | purpose for using container technologies: usage of container images built by someone else, developer of containers and related technologies for others to use, and/or sysadmin or similar who configures container runtimes, registries, and/or other container technologies on systems for users to access |
|   | Ratio | total number of people in sample who fit each category, breakdown of technology usage purpose by application and/or industry |


| **[Optional Objectives](#optional)** | **Data Type** | **Data To Collect** |
| ----------- | ----------- | ----------- |
| 5. Assess the opinions about current OCI specification implementations | Nominal | short answer about what is liked/disliked about the container technologies used |
|   | Ordinal | level of familiarity with the OCI specification, level of satisfaction with the OCI specification (if familiar), short answer about what is liked/disliked about OCI spec (if familiar)? |
|   | Ratio | total number of people in sample who are both experienced with HPC and familiar with OCI spec, total number of people at various levels of satisfaction with OCI spec |
| 6. Collect opinions on requested improvements to the OCI specification for HPC containers | Nominal | short answer about what is liked/disliked about OCI spec (if familiar) and suggestions for improvement |

### Analysis
All of the above collected data, whether collected with convenience sampling or random sampling, will be aggregated to get a sense of the sample population first, with nonresponses and dropouts calculated.  Nominal and ordinal data will be used to create categorical breakdowns of ratio data, and ratio data will have summary statistics calculated.  Further breakdowns and analyses can be determined based on sampling methods used and features of the data.

## Survey Design

### Focus of Questions
The types of container technologies we are interested in asking about include (but are not limited to):
* Container runtimes
* Container build tools & processes
    * What artifact(s) and images (Dockerfile, Docker image, Singularity Definition file, SIF, etc.)
    * Where built (CI/CD, local machine, cloud builder, etc.)?
    * What tools used to build (docker build, compose, buildah, singularity build, etc.)?
* Container registries
    * CVMFS (like biocontainers)
* Container orchestration software & tools

Types of applications of container technologies we are interested in asking about include (but are not limited to):
* Cloud computing for science
* Supercomputing
* Machine Learning applications
* Science runs on smaller/institution clusters

### Decreasing Error
To decrease nonresponse error and dropout, we can [\[1, 2\]](#references):
* Minimize the number of questions we ask by encapsulating the objectives well in the phrasing of fewer questions
* Simplify the effort of responding to questions (i.e. do not make people fill out excessive or tedious formats)
* Ask questions based on whether participants do certain tasks (i.e. developers could get different questions than those maintaining their own registries)
* Cater questions towards expertise and knowledge (i.e. don't ask questions about Shifter if they've never used it)
* Allow “decline to answer” or “not applicable” options (also follows good informed consent practices) - this could be especially important for the optional objectives, and perhaps default answers for these should be "not applicable" and the repsondent must change this to answer the question
* Do not allow multiple responses, or delete multiples from the same respondent

### Other Notes
* Include optional demographics collection at the end of the survey, including personal and professional
* We can use the survey tool (TBD) to implement some of the features desired in the Decreasing Error section, such as hiding questions that do not pertain
* Furthermore, we should design the questions with Diversity, Equity, and Inclusion (DEI) in mind, and have the questions reviewed by folks with expertise on phrasing questions appropriately to minimize bias against marginalized groups.

## Testing the Survey
The final survey implementation and questions can be tested by the Containers Working Group participants to ensure functionality, simplicity, and clarity.  All correctly recorded results from the tests can be kept as part of the dataset - if using convenience sampling - with the caveat that we must note this and that those directly involved in this survey design should likely not be included in final results due to confilict of interest.

## How we will Conduct the Survey

* We will need to submit an application for an IRB expemption/approval - Vanessa has this ready and just needs the final questions
* The survey will be hosted on the [Supercontainers site](https://supercontainers.github.io/) with an about section with something like:

> This survey is being conducted by the [Containers Working Group](https://supercontainers.github.io/containers-wg/) hosted in the [#containers-wg](https://hpc-containers.slack.com/archives/C023C51T8SG) channel of the hpc-containers Slack workspace.  We are a community of researchers interested in containers for High Performance Computing (HPC).  Feel free to [join the Slack](https://join.slack.com/t/hpc-containers/shared_invite/zt-ak9q6jw7-UZgpv7IJua5jCtJ_db_yAQ) and say hello!

* Depending on [Sampling Method](#sampling-method) chosen above, the site will be open access (convenience sampling)..
* The survey will begin with information on informed consent (necessary)
* Respondents will submit responses via a survey tool (TBD) form, data will be automatically stored for each response, multiple responses should be accounted for, and results will be retrieved after the survey has closed so analysis can begin.

***Remaining Question:*** Do we plan to do any recruitment for the survey?  Will we partner with HPC/Research related marketing orgs like insideHPC, HPC wire, and related to help us expand our reach?  This will likely be necessary if we plan to reach a worldwide audience.

***Remaining Question:*** How long do we expect to keep the survey open for?  As in, what is our minimum sample size (and then we wait until we get this before considering closing the survey)?

## References

[1] https://study.sagepub.com/sites/default/files/Fricker.pdf

[2] https://www.researchgate.net/publication/275104401_Exploring_ethical_issues_associated_with_using_online_surveys_in_educational_research

[3] https://www.dataquest.io/blog/how-to-conduct-a-survey-and-collect-data-for-a-data-science-project/
