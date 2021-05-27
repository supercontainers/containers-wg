---
layout: default
title: The Image Spec
nav_order: 3
has_children: true
parent: OCI Specs and Projects
---

# The Image Spec
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Overview

The [image specification](https://github.com/opencontainers/image-spec/blob/master/spec.md) generally is a grouping of things to describe a container image. 
While there is a definition for a [filesystem](https://github.com/opencontainers/image-spec/blob/master/layer.md) and [configuration](https://github.com/opencontainers/image-spec/blob/master/config.md), the most general entity to describe is the image manifest:

### Manifest

The [manifest](https://github.com/opencontainers/image-spec/blob/master/manifest.md) comes down to a json blob of properties for the container such as contents (in Docker, we refer to image layers since the image is a bunch of .tar.gz assembled at runtime), annotations, and a unique identifier for a configuration object. For example, here is a json dump that describes a Docker container:

```
{
  "schemaVersion": 2,
  "config": {
    "mediaType": "application/vnd.oci.image.config.v1+json",
    "size": 7023,
    "digest": "sha256:b5b2b2c507a0944348e0303114d8d93aaaa081732b86451d9bce1f432a537bc7"
  },
  "layers": [
    {
      "mediaType": "application/vnd.oci.image.layer.v1.tar+gzip",
      "size": 32654,
      "digest": "sha256:9834876dcfb05cb167a5c24953eba58c4ac89b1adf57f28f2f9d09af107ee8f0"
    },
    {
      "mediaType": "application/vnd.oci.image.layer.v1.tar+gzip",
      "size": 16724,
      "digest": "sha256:3c3a4604a545cdc127456d94e421cd355bca5b528f4a9c1905b15da2eb4a4c6b"
    },
    {
      "mediaType": "application/vnd.oci.image.layer.v1.tar+gzip",
      "size": 73109,
      "digest": "sha256:ec4b8955958665577945c89419d1af06b5f7636b4ac3da7f12184802ad867736"
    }
  ],
  "annotations": {
    "com.example.key1": "value1",
    "com.example.key2": "value2"
  }
}
```

**Where would I find an image manifest?**

An image manifest would be served by a registry, and would help the user to obtain the content (in the example above, the .tar.gz layers assembled at runtime to create the image). 

**What would I do with the image manifest?**

The manifest helps you to download image layers. 
I might query the registry API to find the image manifest for an image I'm interested in, get back this json blob, and then use the client to pull the image layers (the digests). 
Depending on the design of the registry, there would be another endpoint that I know to query with the blob digests to actually download them.

**What are the annotations for?**

Annotations are key value pairs of metadata to describe the image of interest. They are fairly flexible to allow for the registry and user to use as they see fit.

**How would I want to use this to solve a particular problem?**

The image manifest definition should be able to describe some kind of content blobs for an application like a registry.

**Where might I have seen this in the wild?**

An image manifest is what you see delivered by the [Docker registry](http://hub.docker.com/) to get metadata for a particular [container tag](https://docs.docker.com/engine/reference/commandline/manifest/).
