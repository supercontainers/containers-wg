---
title: Honor media-type Accepts:
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

Registries often return media type other than what was requested. I was very
surprised to discover that returning the requested type is a SHOULD.

Doesn't this violate the HTTP spec?

## What ideas do we have for how to address these challenges?

Only return requested media types. If an implementation can accept multiple
types, it can just say so with the `Accepts:` header.

## How do these ideas break down into...

### Already existing OCI specs?


### A new project (CNCF or OCI)


## Questions?


## What pre-existing work or software can support these ideas?

## Relevant OCI Issues

