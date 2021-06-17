---
title: Clarify symlink and hardlink rules
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

What to do about symlinks and hard links is under-specified. For example:

  1. When should symlinks be followed and when should they not?

  1. Behavior of link replacement in a later layer is explicitly undefined.

  1. Is it permitted to have a link that climbs outside the image? (E.g.: `ln
     -s ../foo /bar`). What about other pathological link targets?

One interesting quirk is that symlinks need to be interpreted relative to the
*image's* root, which makes non-containerized code trickier.

## What ideas do we have for how to address these challenges?

Tighten up the spec to cover these and related ambiguities.


## How do these ideas break down into...

### Already existing OCI specs?

Image spec.


### A new project (CNCF or OCI)


## Questions?


## What pre-existing work or software can support these ideas?

Much of Charliecloud's behavior in this area copies Docker, after much trial
and error. We also have a bunch of validation code for things that seemed
reasonable to us (e.g., no, symlinks cannot climb out of the image).


## Relevant OCI Issues

