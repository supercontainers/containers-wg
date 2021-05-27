# The Container Working Group

This working group is organized to discuss the needs of the HPC community, and how
they can be integrated into existing or new Open Container Initiative (OCI) projects.
Each idea document is in [_ideas](_ideas) and renders to an interface for easier
consumption.

⭐ [View the Ideas](https://supercontainers.github.io/containers-wg/) ⭐

You might also be interested in:

 - [Discussions](https://github.com/supercontainers/containers-wg/discussions) for each idea on the Discussion Board here
 - [Open an issue](https://github.com/supercontainers/containers-wg/issues) to request an invite link to the hpc-containers slack, we are in the `#containers-wg` channel

## How does it work?

### Too Long, Didn't Read:

1. Contribute an idea by creating a new markdown in [_ideas](_ideas) and creating a [discussion](https://github.com/supercontainers/containers-wg/discussions) for it.
2. Critique an existing OCI spec or project by editing the spec/project file in [docs/oci](docs/oci)
3. Write up any introductory material or presentation in [docs/introduction](docs/introduction)
4. If you are familiar with or maintain a project related to OCI (e.g., a container technology? Registry?) tell us about the project in [docs/hpc-projects](docs/hpc-projects) and what in OCI works (and does not work).

### Ideas

Each idea is organized into the following sections. If an idea is good we should
be able to have confident, clear answers for all of the following.

1. What are the challenges that we are trying to solve?
2. What ideas do we have for how to address these challenges?
3. How do those ideas break down into:
 - already existing OCI specs?
 - a new project (either CNCF or OCI)?
4. Which people working on the repository here can take ownership of this idea?
5. What pre-existing work or software can support these ideas?

## OCI Projects and Specs

The site has a section for [OCI projects and specs](https://supercontainers.github.io/containers-wg/docs/oci/)
that provides an overview, and can be used to write general feedback.

### Voting

To get a sense of community interest in each idea along with comments and feedback, 
we link them to GitHub discussions that can (along with comments and discussion) 
have an ability to +1 (or vote) for favorites via the thread. If we can regularly
share our top ideas (as determined by maintainers, for example) in discussion spaces
like Slack and social media, we can get good feedback on the ideas.

## How do I...

### Add a new idea?

The ideas are organized in [_ideas](_ideas), and you can copy the _template.md
into a new markdown named for your idea.

```bash
$ cp _ideas/_template.md _ideas/add-new-thing.md
```

Sections are provided in the template that mirror the questions discussed above.
The idea will render automatically on the site.

### Give feedback on a current OCI spec or project?

Each spec has a markdown file in [docs/oci](docs/oci)

```bash
docs/oci/
├── distribution.md
├── image-spec.md
├── oci-projects.md
├── oci-specs.md
├── runc.md
└── runtime-spec.md
```

And you can add notes or general comments there.

### Add Introductory Material or Links?

If the link isn't appropriate for a specific section already listed, we have
a resources page at [docs/resources.md](docs/resources.md) where you can add it.
Please feel free to add a section that describes it.

## Add one of my projects?

Feedback about our projects and how we would want to use OCI, are using OCI, or
even can't use OCI, is useful in this discussion space. You can
create a new file in [docs/hpc-projects](docs/hpc-projects) to add your project.
Copy an existing file to use as a template.
