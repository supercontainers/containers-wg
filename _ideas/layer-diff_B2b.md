---
title: Binary diff layers
discussion: https://github.com/supercontainers/containers-wg/discussions/27
---

---

{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## What are the challenges that we are trying to solve?

At present, OCI layers use a diff format that is tarballs containing
replacement file contents and in-band whiteout files. This has several
problems:

* Unprivileged container implementations can't non-destructively assemble
  layers because they don't have access to an overlay filesystem.
  (FUSE-OverlayFS is not yet widely available.)

* Can be wasteful of storage because all versions of a file must be stored in
  full. E.g., if you change one byte in 1 GiB file, you must wastefully store
  both states in full. (Content-addressable storage will not de-duplicate
  this, and the block-level de-duplicating filesystems can't either if the
  layers are compressed, which they typically are.)

* Because of in-band white-outs, layers can *almost* but not quite be simply
  unpacked by standard tar implementations. They must be instead "applied" by
  purpose-built procedures.

My critique is based in part on Aleksa Sarai's [previous critique][1] of
tarball layers in quite a bit more detail.

[1]: https://www.cyphar.com/blog/post/20190121-ociv2-images-i-tar

## What ideas do we have for how to address these challenges?

Store layers as binary diffs.

## How do these ideas break down into...

### Already existing OCI specs?

This idea would be relevant for specs that are interested in interacting with
an image manifest with layers.

### A new project (CNCF or OCI)


## Questions?


## What pre-existing work or software can support these ideas?

This scheme would work a lot like Git. Git does not store file metadata, but
that would be a straightforward extension. It's not hard to imagine an image
store that's really just a Git repo.

Charliecloud scans tarball metadata to deal with whiteouts, then unpacks
tarballs in-place.


## Relevant OCI Issues
