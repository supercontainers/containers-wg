---
layout: default
title: Charliecloud
nav_order: 4
parent: HPC Projects
---

# Charliecloud
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Fully unprivileged containers

Our focus is on fully-unprivileged containers like Charliecloud, with no
privileged helper to set up namespaces. This document refers to this concept
as simply "unprivileged" for brevity.

Such unprivileged containers are both possible and a valid/important use case.
In HPC this supports container use and building by normal users on the
hardware where they will actually run.

These ideas are detailed in our pre-print [Minimizing privilege for building
HPC containers](https://arxiv.org/abs/2104.07508), by Priedhorsky, Canon,
Randles and Younge.

## Current OCI status

The Charliecloud team has (partially) implemented OCI in two contexts:

  1. Interacting with registries over HTTP, available in various `ch-image(1)`
     subcommands.
  2. A shim `ch-run-oci(1)` to support image builds using Buildah.

We did a lot of reverse engineering to deal with unclear
documentation/specifications.

Notes on the latter:

  * https://hpc.github.io/charliecloud/command-usage.html#ch-run-oci
  * https://hpc.github.io/charliecloud/dev.html#oci-technical-notes

From our docs:

> In summary, the philosophy and goals of OCI differ significantly from those
> of Charliecloud. Key differences include:
>
>   * OCI is designed to run services, while Charliecloud is designed to run
>     scientific applications.
>   * OCI containers are persistent things with a complex lifecycle, while
>     Charliecloud containers are simply UNIX processes.
>   * OCI expects support for a variety of namespaces, while Charliecloud
>     supports user and mount, no more and no less.
>   * OCI expects runtimes to maintain a supervisor process in addition to
>     user processes; Charliecloud has no need for this.
>   * OCI expects runtimes to maintain state throughout the container
>     lifecycle in a location independent from the caller.


## Contact

Reid Priedhorsky, Charliecloud project leader: reidpr@lanl.gov


## Detailed critique of OCI

Based on the above experience, as well as a review of the OCI Git repository
on 2021-06-14, Reid's concerns are as follows. Note I'm speaking for myself
here. Within each section, there is no particular order, other than I tried to
group related things together and avoid forward references.

I am very interested in feedback and questions.

### A. Meta

  1. In general, simply "following the specification" is insufficient; the
     quality of the spec matters. I hear a lot of arguments in HPC containers
     that basically boil down to "specs are good; OCI is a spec; therefore we
     should conform to OCI". I don't think this is a very good argument, and
     we should evaluate OCI in detail on its merits before pursuing
     conformance. Also, consider that good-quality specs are easier to
     implement. Given a container implementation that claims OCI compliance,
     how do you know this is true and how do you verify it?

  1. The organization of the specification is quite difficult for the
     uninitiated. It's a web of different documents with no clear reading
     order. There is a very large number of links throughout, and it's unclear
     whether they go to different spec documents, the same document (including
     more than once the very next section!), or a separate site.

  1. The spec does not have:

     * a way to evaluate conformance (i.e., a test suite), except for a
       [registry conformance
       test](https://github.com/opencontainers/distribution-spec/blob/main/conformance/README.md),
       or
     * sufficient examples, e.g. edge cases and a complete image with all
       the hashes computed.

     For example, we are only able to test one flavor of whiteouts
     (non-opaque) because we couldn't make Docker generate the other flavor
     (opaque) even when it seemed appropriate (`RUN rm -Rf mydir`).

  1. The spec documents often lack introductory material. For example, see
     [OCI Content
     Descriptors](https://github.com/opencontainers/image-spec/blob/master/descriptor.md);
     this page on a jargony topic opens directly into a highly jargony bullet
     list.

  1. The spec seems too Golang-specific to me in place, e.g. by calling out to
     Golang documentation for lists of valid values. In my view,
     specifications should be language-agnostic.

  1. There is no spec for the Dockerfile language (the [Dockerfile
     reference](https://docs.docker.com/engine/reference/builder/) is informal
     and has gaps), and extensibility is currently via comment hacks.

  1. There's [some
     implication](https://supercontainers.github.io/containers-wg/docs/oci/runc/)
     in the `containers-wg` write-up that `runc` is the only permissible
     runtime; in my view we should take care to talk about the specification
     in a runtime-agnostic way.

### B. Image

  1. It would be good to support ID-flattened images, where the user(s) and
     group(s) within the archive are not meaningful. Typically, these images
     are generated by unprivileged implementations and have a single user, and
     possibly multiple groups. The implementation should adjust these before
     upload to not leak the user's real IDs (Charliecloud uses 0:0), but
     that's not guaranteed. In my view the behavior on unpacking should be
     like `tar(1)` in unprivileged mode: change ownership to the user.

  1. It would be good to support other layer formats. Specifically:

     1. SquashFS.

     1. Binary diff of some kind. At present, changes in file contents can
        only be expressed by replacing the file in full; e.g., if you change
        one byte in 1 GiB file, you must wastefully store both states in full.
        (Content-addressable storage will not de-duplicate this, and the
        filesystem can't either because it's hidden in a compressed archive.)
        This would solve some other problems with layers too, e.g. in-band
        whiteouts.

  1. Applying layer changesets doesn't work well with unprivileged
     environments, where no type of overlay filesystem is available.
     (FUSE-OverlayFS is not yet widely available.) This use case would be well
     supported by diff layers.

  1. The input to digest computations is not clear. For example:

     1. The ImageID is the hash of the config JSON, but JSON is text and hash
        algorithms take bytes, and text has multiple serializations to bytes.

     1. For composite objects like `.tar.gz` files, sometimes the hash is of
        the compressed object but sometimes it's the uncompressed object.

     1. Why both "Layer DiffID" and "layer digest"? Don't these serve the same
        purpose? And if they do have different purposes, the spec should
        explain the reasoning.

     It would be better if, whenever a digest is mentioned, the spec said
     right there what the input is. (We had a lot of trouble debugging this
     because when a digest computation is wrong, you just get the wrong output
     with no indication of where the mistake is.)

  1. The specific tar flavor is not specified (there are several).

  1. What to do about symlinks and hard links is under-specified. For example:

     1. When should symlinks be followed and when should they not?

     1. Behavior of link replacement in a later layer is explicitly undefined.

     1. Is it permitted to have a link that climbs outside the image? (E.g.:
        `ln -s ../foo /bar`). What about other pathological link targets?

     (Much of Charliecloud's behavior in this area copies Docker, after much
     trial and error.)

  1. White-outs are in-band with special filenames, making it impossible to
     simply unpack tarballs and making those names impossible to store.

  1. More detailed architecture metadata would be useful for HPC, e.g. as
     provided by the [archspec library](https://github.com/archspec/archspec).

  1. Architecture valid values seems to point to an incomplete list, and
     variants aren't covered (e.g., `arm/v7`).

  1. `ENTRYPOINT` and `CMD` interactions are too complex; see the [16-cell
     matrix](https://docs.docker.com/engine/reference/builder/#understand-how-cmd-and-entrypoint-interact) in the Dockerfile reference.

  1. Config history: No machine-readable way to see how the layer was created.
     In practice, it seems the Dockerfile instruction goes into the comment
     field, but this ought to be codified and the needless `/bin/sh` prefixes
     for non-`RUN` instructions removed.

  1. The image config seems to *require* [conversion to an at-rest OCI
     image](https://github.com/opencontainers/image-spec/blob/master/conversion.md),
     rather than saying how the container should behave. Implementations
     should be free to not use the OCI image format internally. Even if you
     read the spec as not requiring this, the extra step in the spec makes it
     harder to interpret.

### C. Runtime

  1. The spec is a poor match for unprivileged containers. An image can
     request all kinds of things that are unavailable in an unprivileged
     implementation (e.g. arbitrary namespaces, user/group IDs, ID maps, port
     numbers).

  1. The spec assumes (but does not state) that the container implementation
     tracks containers somehow and has a notion of containers as persistent
     entities beyond their process lifetime, which Charliecloud does not,
     because containers are just processes and you can just use the process
     tools you already have.

  1. The container lifecycle is a poor match for things that are just
     process(es), rather than a daemon or a mini-VM. For example, Charliecloud
     has no persistent supervisor daemon: it simply sets up the container and
     then replaces itself with the user command. So there is no need for a
     separate *create* operation, and *delete* doesn't make sense because
     Charliecloud does not have any container resources to remove. *kill*
     doesn't make sense because the containerized user process can spawn
     whatever children it likes: which of these should be signaled? The state
     *running* doesn't make sense because when the user-specified program
     exits, the container is gone. Point being, all of this maps awkwardly to
     UNIX process lifetimes and requires the container implementation to
     maintain state it may not otherwise need. (For example, `ch-run-oci(1)`
     keeps a process that literally does nothing so that it can return the
     process ID to Buildah, which verifies that the process is running.)

  1. The runtime doesn't get enough information on the command line to remain
     stateless, because the bundle path is only provided on create. It would
     be better to provide the bundle path on every operation (perhaps *instead
     of* a container ID); also, then the implementation could put stuff there.
     (`ch-run-oci(1)` deals with this by inferring bundle path from container
     ID, which works OK for Buildah but is very brittle.)

  1. It's unclear whether cgroups support is required, but it shouldn't be.
     Generally speaking, it's unclear what parts of [Linux Container
     Configuration](https://github.com/opencontainers/runtime-spec/blob/master/config-linux.md)
     are required (MUST be supported by the runtime) or optional (SHOULD or
     MAY be supported).

### D. Distribution

  1. Registries often return media type other than what was requested. I was
     very surprised to discover that returning the requested type is a SHOULD;
     in my view this should be MUST. If an implementation can accept multiple
     types, it can just say so with the `Accepts:` header. And doesn't this
     violate the HTTP spec?

  1. Registries often don't send a `Content-Length:` header (hello Red Hat!).
     I realize the blob size is usually elsewhere (e.g., in the manifest), but
     why not also require it to be in the place where existing standards
     expect it. Many HTTP libraries also can do useful things with
     `Content-Length:` and provide no useful way to accept length in other
     ways.

  1. "[If the {manifest,blob} is not found in the registry, the response code
     MUST be 404 Not
     Found.](https://github.com/opencontainers/distribution-spec/blob/main/spec.md)"
     This is routinely violated in practice; we've seen both 401 and 400 to
     indicate not found.

  1. It would be nice if single POST blob upload were required (MUST), since
     that simplifies upload code.

<!--  LocalWords:  oci ImageID DiffID OverlayFS jargony Golang
 -->
