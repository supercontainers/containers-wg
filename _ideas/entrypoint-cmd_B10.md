---
title: ENTRYPOINT and CMD are too complex
discussion: https://github.com/supercontainers/containers-wg/discussions/30
---

---

{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## What are the challenges that we are trying to solve?

`ENTRYPOINT` and `CMD` interactions are too complex. See the [16-cell
matrix][1] in the Dockerfile reference and note its (a) large size and (b)
inconsistencies. For example, behavior differs between `ENTRYPOINT` specified
as a command line (`ENTRYPOINT foo bar`) or list (`ENTRYPOINT ["foo",
"bar"]`), and the difference between the 2nd and 3rd lines is unclear.

[1]: https://docs.docker.com/engine/reference/builder/#understand-how-cmd-and-entrypoint-interact

## What ideas do we have for how to address these challenges?

New instruction (`EXEC`?) that specifies both the command and default
arguments.

## How do these ideas break down into...

### Already existing OCI specs?


### A new project (CNCF or OCI)

If a Dockerfile spec could be created, this idea would supplement it.

## Questions?


## What pre-existing work or software can support these ideas?

## Relevant OCI Issues
