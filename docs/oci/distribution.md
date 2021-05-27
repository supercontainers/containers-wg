---
layout: default
title: The Distribution Spec
nav_order: 5
parent: OCI Specs and Projects
---

# The Distribution Spec
{:.no_toc}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

[Distribution](https://www.merriam-webster.com/dictionary/distribution):

> _the action of sharing something out among a number of recipients._

Distribution, or sharing of container images, is just as important as building them in the first place. 
If you can't easily distribute your container, you lose a [lot of the benefits]({{ site.baseurl }}/docs/introduction/container-images/#what-problems-do-containers-solve) that we outlined in the first place.

Generally, you can think of distribution eco-system as having different use cases. 
I should be able to easily:

 - *share*: the container images that I create, across hosts, institutions, and time zones.
 - *search*: I should be able to find the container that I'm looking for.
 - *obtain*: If I find a container, and given I have permission to do so, I should be able to get it
 - *verify*: that the container I requested is the one that I wanted, and not some malicious entity.
 
Generally, a distribution comes down to a strategy that includes software, servers, and databases to fulfill these goals.
The [distribution specification](https://github.com/opencontainers/distribution-spec/blob/master/spec.md) helps to outline a lot of the interactions to make this possible.

## Details

The [distribution specification](https://github.com/opencontainers/distribution-spec/blob/master/spec.md) describes the API that might be used by a registry to distribute images. 
This means actions like pull, push, along with how images are named, and errors are presented. 
You can think of the distribution specification as a collection of endpoints served by a registry to communicate with. Do you want a manifest? Use the manifest endpoint:

```
GET /v2/<name>/manifests/<reference>
```

Do you want to upload a blob? There is an endpoint to POST to for that:

```
POST /v2/<name>/blobs/uploads/
```

**Where would I find a distribution specification?**

An implementation of this specification would be found with a container registry that implements the OCI standard. For example, Docker Hub implements the specification. A developer could also roll their own registry (such as [this one](https://github.com/atlaskerr/stori)) that implements it.

**What would I do with the distribution specification?**

The specification outlines a method of interaction. If you are writing a client, for example, these are the endpoints that the client would use. If you are creating a new registry that you wanted to conform to OCI, these are the API endpoints you would implement.

**How might I contribute to the distribution specification?**

Generally, since the goals are to move (push and pull) images, and provide endpoints for a client, if you are designing a registry or a client and find that you are missing some key function of an endpoint, or information provided by an endpoint, you might want to suggest a change to the specification.

