---
layout: default
title: Ideas
nav_order: 3
has_children: true
permalink: /ideas/
---

# Ideas
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

<ul>
{% assign ideas = site.ideas | sort: 'title' %}
{% for idea in ideas %}
   <li><a href="{{ site.baseurl }}{{ idea.url }}">{{ idea.title }}</a></li>
{% endfor %}
</ul>
