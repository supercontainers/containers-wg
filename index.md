---
layout: default
title: Containers Working Group
nav_order: 1
permalink: /
---

# The Containers Working Group

This working group is organized to discuss the needs of the HPC community, and how
they can be integrated into existing or new Open Container Initiative (OCI) projects.
You can browse ideas here, and contribute to them directly at the [repository]({{ site.repo }}).
In this site you will find:

 - *ideas*: What ideas do we have for updating or extending OCI?
 - *discussion*: Each idea is linked to a discussion thread.
 - *review*: of existing specs and the issues they have in an HPC context.
 - *share*: your current HPC projects and how OCI works (or does not work) for you.

Please [see the repository]({{ site.repo }}) for details on how to contribute.

## Finished

1. To start with an effort to improve the overall interface to read OCI documentation, ([this issue](https://github.com/supercontainers/containers-wg/issues/9)) we created the [rfc-jekyll](https://vsoch.github.io/rfc-jekyll/) template, and it is now deployed at [specs.opencontainers.org](https://specs.opencontainers.org/) so the OCI specs are easier to read.


## In Progress

1. Discussion of a survey is underway! The survey (and IRB papers) were ready in early September, but moving forward was stopped by working group members that have not followed up yet.
2. To tackle [clarification of dealing with symbolic and hardlinks](https://supercontainers.github.io/containers-wg/ideas/links_B6/) in the image spec we've opened [an issue](https://github.com/opencontainers/image-spec/issues/857) for discussion and started working on an update to the image-spec to address it.

Please feel free to jump in to provide feedback or help with these efforts!

## Content

 - [Ideas]({{ site.baseurl }}/ideas/): for how we can contribute a spec or project.
 - [OCI Specs and Projects]({{ site.baseurl }}/oci/): review (and comments) on current OCI specs and projects.
 - [HPC projects]({{ site.baseurl }}/hpc-projects/): notes about why OCI works (or not) for our projects.
 - [Contributing]({{ site.repo }}): instructions are in the repository README.

## Ideas

The following ideas are under development!

<ul>
{% assign ideas = site.ideas | sort: 'title' %}
{% for idea in ideas %}
   <li><a href="{{ site.baseurl }}{{ idea.url }}">{{ idea.title }}</a></li>
{% endfor %}
</ul>

{: .fs-6 .fw-300 }

---
