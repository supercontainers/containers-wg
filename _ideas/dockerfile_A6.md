---
title: Dockerfile specification
discussion: FIXME
---

---

{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## What are the challenges that we are trying to solve?

The best specification I've been able to find for Dockerfile syntax and
semantics is the [Dockerfile
reference](https://docs.docker.com/engine/reference/builder/). However, this
is a usage manual rather than a specification, so it doesn't cover all the
edge cases.

In particular:

* There is no official Dockerfile grammar. The best way I've found to evaluate
  compatibility is seek bug-compatibility with Docker, which is time-consuming
  and error-prone. (Charliecloud has reverse engineered a [grammar for
  `ch-image`](https://github.com/hpc/charliecloud/blob/e6413c9d0dcfe4e860d1fe63ce990247e0f361de/lib/charliecloud.py#L85)
  that works OK for us.)

* Extensibility is currently via [comment
  hacks](https://docs.docker.com/engine/reference/builder/#parser-directives)
  rather than a robust mechanism, e.g. an `OPTIONS` instruction (a la Python's
  [`from __future__` statement](https://www.python.org/dev/peps/pep-0236/)) or
  ignoring unknown instructions by default.

## What ideas do we have for how to address these challenges?

Solid specification of the Dockerfile syntax and semantics, including a
grammar. This could certainly be based on the Dockerfile reference.

It could be an opportunity to fix some of the inconsistencies, also; e.g.
`ARG` and `ENV` do almost the same thing but have different syntax.

## How do these ideas break down into...

### Already existing OCI specs?


### A new project (CNCF or OCI)


## Questions?


## What pre-existing work or software can support these ideas?

Charliecloud has made a lot of progress formalizing Dockerfile syntax and
explaining where [we found ambiguities](https://hpc.github.io/charliecloud/command-usage.html#compatibility-with-other-dockerfile-interpreters).

## Relevant OCI Issues

