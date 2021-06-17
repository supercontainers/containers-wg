---
title: Digest input clarification
discussion: 
---

---

{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## What are the challenges that we are trying to solve?

The input to digest computations is not clear. For example:

  1. The ImageID is the hash of the config JSON, but JSON is text and hash
     algorithms take bytes, and text has multiple serializations to bytes.

  1. For composite objects like `.tar.gz` files, sometimes the hash is of the
     compressed object but sometimes it's the uncompressed object.

  1. Why both "Layer DiffID" and "layer digest"? Don't these serve the same
     purpose? And if they do have different purposes, the spec should explain
     the reasoning.

(The Charliecloud team had a lot of trouble debugging this because when a
digest computation is wrong, you just get the wrong output with no indication
of where the mistake is.)

## What ideas do we have for how to address these challenges?

Whenever a digest is introduced by a spec, it should state in the same
paragraph as the introduction (or a similar close location) what the input is.

## How do these ideas break down into...

### Already existing OCI specs?

This suggestion would be relevant to any interactions with [digests][1].

[1]: https://github.com/opencontainers/go-digest

### A new project (CNCF or OCI)


## Questions?


## What pre-existing work or software can support these ideas?

## Relevant OCI Issues
