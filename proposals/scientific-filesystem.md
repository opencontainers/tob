# OCI Scientific Filesystem Project Proposal

## Abstract

The proposal below suggests adding the [Scientific Filesystem](https://sci-f.github.io/) (SCIF) specification
to OCI in order to support internal, modular organization of containers.

## Background

Containers are essential for reproducibility in both enterprise applications and science. Typically,
a single container is understood as a single unit with one shared environment, entrypoint, labels,
and metadata. While this works well for simple applications, when a single container must support
several applications (each tentatively with a distinct entrypoints, environments, and metadata)
discoverability is lost. Several approaches to address this have been:

* documentation that details the executables and environments in the container, and how to access them
* a complicated single entrypoint to present options to the user

While both of these approaches are reasonable, they are not ideal. For the first, if documentation is lost,
the container is again a black box with software and metadata hiding inside. The second
requires extensive work on the part of the developer to write custom entrypoints every time.
The internal organization of containers, while not completely essential for all containers,
is an incredibly important and overlooked detail for a large number of containers. It needs
to be a part of OCI so that users and application developers are encouraged to create
internally modular and discoverable containers.

### What has been done?

In January of 2018 Vanessa Sochat (@vsoch) created the Scientific Filesystem to address these concerns directly.
SCIF is an organizational format to help a user to install modular applications inside of a container, each with its own
environment, labels, libraries, metadata, and entrypoint. It works alongside package and environment managers, 
and ensures that the applications installed in a container are discoverable without special knowledge about
the container. The specification was written and [worked on by the community](https://docs.google.com/document/d/1k0I1M1BIR1aqGxVVJrow_Gj3T8BXHco-oqnreYKuxL8/edit), resulting in a peer reviewed [paper was published in GigaScience](https://academic.oup.com/gigascience/article/7/5/giy023/4931737) 
in March of 2018.

SCIF allows a user to write a simple recipe file (akin to a Dockerfile or Singularity recipe) and 
install with `scif install recipe.scif`. By performing this operation inside of
a container, the user can expose `scif` as the entrypoint, and the client will list applications,
shell into the container with an application environment active, or execute or run a command under
the same conditions. The specification was implemented natively in Singularity containers, 
and also exists as a [Python client](https://www.github.com/vsoch/scif). Python was chosen 
only because the (original) intended audience was the scientific community, and @vsoch has plans 
to implement a golang version to better integrate with other container software.

While @vsoch created SCIF specifically for containers (and has created [examples](http://github.com/sci-f/snakemake.scif) 
using it across different kinds, see [interactive example here](https://sci-f.github.io/snakemake.scif/)) 
it should also be noted that SCIF doesn't necessarily need to be exclusively for containers.

## What are long term goals?

The long term rationale for having applications be discoverable is writing software that can work
with any container that implements SCIF. For example, [here is a SCIF builder](https://sci-f.github.io/builder/)
that serves as a template to install a recipe, and run tests based on discovering the applications installed.
@vsoch hopes to better expose SCIF to the container community by exposure through OCI. She
will enthusiastically manage the project, help developers to implement and make suggestions to
improve SCIF, and assist and encourage users to use it.

For more examples, and the full specification, see [https://sci-f.github.io/](https://sci-f.github.io/).

## Proposal

 * Move the https://www.github.com/sci-f/scif.github.io specification into the OpenContainers organization

## Future Plans

 * Develop scif as a GoLang module (longer term, doesn't need to be under opencontainers but could be)
 * Create software (akin to the builder above) that easily interacts with SCIF containers.

### Project Descriptions

The following are descriptions to describe the first two points above:
 * scif: organizational format for consistency, transparency, programmatic accessibility, and discoverability of container software and metadata.
 * scif-go: a GoLang implementation of SCIF for better integration with container software.

### Initial Maintainers
Initial maintainers of the scif project:
 * Vanessa Sochat (@vsoch)

### Code of Conduct
The proposed project would incorporate (by reference) the OCI Code of Conduct

### Governance and Releases
The proposed project would incorporate the Governance and Releases processes from the OCI project template: https://github.com/opencontainers/project-template.

### Project Communications
SCIF would use the following OCI developer community channels for communication, in order of expected usage:
* GitHub for general discussion, issues and pull requests
* The dev@opencontainers.org email list for questions
* The weekly OCI developer community conference call
* The OpenContainers slack (included now with IRC)

### Versioning
The Scientific Filesystem uses semantic versioning. The current release is 1.0.0.


## Frequenty Asked Questions (FAQ)

For frequently asked questions and the philosophy behind SCIF, see the [pages here](https://sci-f.github.io/goals#philosophy).
