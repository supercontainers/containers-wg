---
title: Fully unprivileged runtime support
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

It's impossible to be a conformant, fully unprivileged implementation because
"[if the runtime is unable to create the environment specified in the
`config.json`, it MUST generate an
error](https://github.com/opencontainers/runtime-spec/blob/master/runtime.md#lifecycle)",
but `config.json` includes a *large* number of things that are disallowed by
unprivileged namespace setup, including arbitrary namespaces, UID/GID maps,
and port numbers. cgroups is another possible source of problems. I didn't do
a detailed analysis yet.

I suspect that in most cases, images don't really need everything they claim
to in `config.json`.

## What ideas do we have for how to address these challenges?

Split the configuration into required and optional components, and try to
enforce that inclusion into required is only things that really are required.

(To be clear, the latter will never fully be reliable, so Charliecloud would
still allow overriding required things to work around config errors.)

## How do these ideas break down into...

### Already existing OCI specs?


### A new project (CNCF or OCI)


## Questions?


## What pre-existing work or software can support these ideas?

Charliecloud just ignores all the things in `config.json` that it doesn't
support.

## Relevant OCI Issues

