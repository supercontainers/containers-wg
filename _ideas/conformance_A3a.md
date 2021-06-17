---
title: Conformance tests
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

No way to evaluate OCI conformance (aside from the [registry conformance
test][1].

[1]: https://github.com/opencontainers/distribution-spec/blob/main/conformance/README.md

## What ideas do we have for how to address these challenges?

Add conformance tests for image, runtime, and distribution client specs. These
should report granular results rather than simply yes/no so that
implementations can say what parts of OCI they do and don't support.

## How do these ideas break down into...

### Already existing OCI specs?

This suggestion is relevant to the image, runtime, and a distribution client
spec. Any news specs that arise should also be developed with conformance
testing as a priority.

### A new project (CNCF or OCI)


## Questions?


## What pre-existing work or software can support these ideas?

## Relevant OCI Issues
