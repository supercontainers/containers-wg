---
title: Content-Length: required
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

Registries often don't send a `Content-Length:` header. I realize the blob
size is usually elsewhere (e.g., in the manifest), but why not also require it
to be in the place where existing standards expect it. Many HTTP libraries
also can do useful things with `Content-Length:` and provide no useful way to
accept length in other ways.

## What ideas do we have for how to address these challenges?

Registries MUST return `Content-Length:` headers on all responses where it's
meaningful, that match the manifest/config.

## How do these ideas break down into...

### Already existing OCI specs?

This suggestion would be a change to the distribution spec.

### A new project (CNCF or OCI)


## Questions?


## What pre-existing work or software can support these ideas?

## Relevant OCI Issues

