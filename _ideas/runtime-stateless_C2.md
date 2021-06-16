---
title: Stateless runtime support
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

The spec assumes (but does not state) that the container implementation tracks
containers somehow and has a notion of containers as persistent entities
beyond their process lifetime.

However, because a valid view of containers is that they are simply processes
with their own view of certain kernel processes, it's possible and legitimate
to create a runtime (like Charliecloud) that sets up a container and then
replaces itself with the containerized user process, with no further tracking.
Notably:

1. This user process can spawn children and even re-parented daemons, just
   like any other UNIX process. That is, knowing its PID *does not* let you
   find all the processes in the namespace or even whether the namespace has
   *any* processes in it.

1. Namespaces also have IDs. This ID cannot be used to directly access the
   namespace, but it can be used to check if a given process is in a given
   namespace (via symlinks in `/proc/$PID/ns`). So in principle one could test
   container emptiness via an exhaustive search of `/proc`. I do not know if
   this is reliable, and it's a lot of `stat(2)` calls.

(Details and subtleties on how containers work, related to this, in
[Minimizing privilege for building HPC containers][1], by Priedhorsky, Canon,
Randles and Younge.)

[1]: https://arxiv.org/abs/2104.07508

## What ideas do we have for how to address these challenges?

Brainstorming (this needs more thinking & feedback):

1. At least one of:

   * Allow the runtime to reassign container IDs. This could be the user
     process PID / namespace ID (though see caveats above), or perhaps the
     bundle path.

   * Provide the bundle path on every lifecycle command (currently it only
     comes with `create`).

2. Let the runtime store things in the bundle directory.

3. Let `create` be a no-op, with the `prestart`, `createRuntime`, and
   `createContainer` hooks invoked during `start`. (Currently the spec
   requires implementations to have a pause after `create` waiting for
   `start`, which isn't needed and Charliecloud does not.)

4. Let `kill` be a no-op, because the runtime might not know which processes
   to kill.

5. Let `delete` (and the `poststop` hooks) be a no-op, because the runtime
   might not know what processes are in the container.

6. Allow a status `unknown` for runtimes that don't track containers.

7. Don't assume anything about the process structure of the runtime, including
   whether any runtime process will be persistent or available. (For example,
   `ch-run-oci(1)` keeps a process that literally does nothing so that it can
   return the process ID to Buildah, which checks that the process is
   running.)

## How do these ideas break down into...

### Already existing OCI specs?


### A new project (CNCF or OCI)


## Questions?


## What pre-existing work or software can support these ideas?

Kludges to make Charliecloud's `ch-run(1)` work as an OCI runtime for Buildah
can be examined in the [`ch-run-oci(1)` source code][1], [documentation][2],
and [implementation notes][3].

[1]: https://github.com/hpc/charliecloud/blob/e6413c9d0dcfe4e860d1fe63ce990247e0f361de/bin/ch-run-oci.py.in
[2]: https://hpc.github.io/charliecloud/command-usage.html#ch-run-oci
[3]: https://hpc.github.io/charliecloud/dev.html#oci-technical-notes

## Relevant OCI Issues

