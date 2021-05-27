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

## Content

 - [Ideas]({{ site.baseurl }}/docs/ideas/): for how we can contribute a spec or project.
 - [OCI Specs and Projects]({{ site.baseurl }}/docs/oci/): review (and comments) on current OCI specs and projects.
 - [HPC projects]({{ site.baseurl }}/docs/hpc-projects/): notes about why OCI works (or not) for our projects.
 - [Contributing]({{ site.repo }}): instructions are in the repository README.

## Ideas

The following ideas are under development!

<ul>
{% for idea in site.ideas %}
   <li><a href="{{ site.baseurl }}{{ idea.url }}">{{ idea.title }}</a></li>
{% endfor %}
</ul>

{: .fs-6 .fw-300 }

---
