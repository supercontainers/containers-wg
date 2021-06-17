---
title: Tar flavor
discussion: https://github.com/supercontainers/containers-wg/discussions/18
---

---

{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## What are the challenges that we are trying to solve?

Tar has several flavors, including old POSIX, new POSIX (PAX), GNU, UStar, and
Schily; another issue is whether or not layer should be tarbombs (in practice
they seem to be). The spec seems aware of this, but lacks any discussion of
which flavors are and are not supported.

Aleksa Sarai has written a detailed history of tar in his [critique of tarball
layers][1].

[1]: https://www.cyphar.com/blog/post/20190121-ociv2-images-i-tar

## What ideas do we have for how to address these challenges?

Amend the spec to document what tar formats and features are supported.

## How do these ideas break down into...

### Already existing OCI specs?

Image spec.


### A new project (CNCF or OCI)


## Questions?


## What pre-existing work or software can support these ideas?

## Relevant OCI Issues

Someone proposed ustar in 2016 ([issue #342][1]). The response started as
"This is a bit excessive. Honestly i'm inclined to just close this." and more
or less ended the same way. Note this discussion claims that the "docs" call
for "GNU tar 'standard' format", but I was not able to find anything to this
effect in the image spec.

[1]: https://github.com/opencontainers/image-spec/pull/342


<!--  LocalWords:  UStar Schily PAX
 -->
