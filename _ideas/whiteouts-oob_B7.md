---
title: Whiteouts out-of-band
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

[White-outs][1] are in-band with special filenames. That is, layer tarballs
contain empty files with a `.wh.` prefix to indicate something has been
deleted. This makes it impossible to simply unpack tarballs and making those
names impossible to store.

Aleksa Sarai has [critiqued][2] white-out files in greater detail. It seems
the way the spec came about is that Docker simply tarred up the AUFS layers
and that that became the standard image format; i.e., the format wasn't
carefully designed but arose as a result of one existing implementation's way
to get a minimally-viable product working quickly.

[1]: https://github.com/opencontainers/image-spec/blob/81270cdee5c47c0f05168e5521830787d71aa50d/layer.md#whiteouts
[2]: https://www.cyphar.com/blog/post/20190121-ociv2-images-i-tar#issue-white-out

## What ideas do we have for how to address these challenges?

Store white-outs out of band, e.g. as a JSON blob accompanying a layer
tarball.

## How do these ideas break down into...

### Already existing OCI specs?

Image spec.


### A new project (CNCF or OCI)


## Questions?


## What pre-existing work or software can support these ideas?

## Relevant OCI Issues


<!--  LocalWords:  wh
 -->
