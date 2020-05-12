# Getting Started

While the [OCI Charter](./CHARTER.md) is our official governing document, many
people have asked for a gentler introduction to the Open Container Initiative as
well as general guidance on how to interact with the projects and specifications
found under the OCI umbrella. This document attempts to be that starting point
for those who may be new to the OCI, interested in participation, or who want to
understand if a project is a fit for inclusion or contribution to the OCI.

## What is the OCI?

As our [website](https://opencontainers.org) states, chiefly the OCI is "an open
governance structure for the express purpose of creating open industry standards
around container formats and runtime." Created in 2015, the core initial purpose
was to align Docker and other ecosystem players around a runtime and image
specification that would become an industry baseline for how images are packaged
and executed in OCI compliant runtimes.

Since that initial work, finalized in 1.0 specs in the summer of 2017, a
distribution specification is now underway, based on the HTTP API of the initial
Docker distribution (registry) project. In 2019, an "artifacts" project was
approved by the TOB and will be used to define other artifact types (in addition
to OCI images) which may be defined and stored in registries conforming to the
OCI distribution spec.

## Who uses the OCI?

It makes the most sense to see consumers of OCI as fitting into a few specific
categories: contributors/members, implementors, and end users.

**Contributors**, including the project maintainers, and member companies have a
vested interest in bringing forward the "state of the art" with respect to the
scope of the OCI. Currently this is of course limited to specifications around
runtime, image, and distribution of containers. The artifacts repository and
project is related to both image and distribution and is a natural expansion
of OCI into ongoing experimentation with registries and cloud native tooling.
Specifically, [artifacts](https://github.com/opencontainers/artifacts) expands the concept around the **what** when
discussing non-OCI image content (Helm charts, Singularity container images,
SPDX, source bundles, etc.) and registries.

**Implementors** own projects outside the OCI for which they have determined
value in being "OCI compliant"; whether that's a registry, a unique container
runtime, or an end-user tool that talks to registries. They take the OCI
specifications and implement support for them in their project, and potentially
will use the conformance suite within the OCI to validate their compliance to
the specification(s).

**End Users** tend to gain value from the OCI specifications in an indirect
way: they will expect projects and products that claim OCI compliance to
interoperate smoothly with other projects and products which are OCI compliant.
They will look to the OCI to continue maturing conformance and specifications
to best support the cloud native ecosystem's goal of interoperability for
runtimes, images, and distributing images and artifacts across clouds and
platforms.

## What Types of Projects Exist within the OCI?

There has been some growth in the nature and use of the OCI since those
initial meetings around the image and runtime specification in 2015. The
following subsections define project categories which exist in the OCI today.

### Specifications

Clearly the image, runtime, and distribution specifications are the key
reason for the existence of the OCI today. These standards are meant to
provide a baseline to follow for implementors of runtimes, registries, and
tools which interact with container images and registries.
 - [Runtime spec](https://github.com/opencontainers/runtime-spec)
 - [Image spec](https://github.com/opencontainers/image-spec)
 - [Distribution spec](https://github.com/opencontainers/distribution-spec)

### Spec Conformance Test

Conformance tests should provide a clear, end-user runnable test suite for
implementors to use to determine and demonstrate that an implementing project
or product meets the explicit definitions of the specification.
 - [OCI Conformance](https://github.com/opencontainers/oci-conformance)

The most advanced conformance implementation to date is for the new distribution specification. Additional work on image and runtime conformance is ongoing.

### Libraries 

While hosting library code is not a common goal of the OCI, there are a few
specific cases where small, non-end user focused, and tightly scoped libraries
have been accepted into the OCI. The common denominator for these libraries are
that they help implementors properly use features of the specifications:
 - [go-digest](https://github.com/opencontainers/go-digest)
 - [selinux](https://github.com/opencontainers/selinux)

Utilities and end-user UX-oriented code is most likely better targeted at other
more broad communities like the [CNCF](https://cncf.io). While there are not
explicit rules, a discussion with the TOB is warranted for projects looking to
contribute a library to OCI.

### Reference Implementations

While theoretically a specification can have one or more reference
implementations, the OCI runtime spec and the program, `runc`, have gone
hand in hand simply due to the particulars around the founding of the OCI.

It is not inconceivable that more reference implementations would be 
contributed and supported within the OCI, but at this point, the only
active and viable reference implementation within the OCI is the `runc`
implementation of the runtime specification, based around the contributed
**libcontainer** codebase contributed by Docker.
 - [runc](https://github.com/opencontainers/runc)

Runc is also unique in that it is an open source reference implementation,
but also a core dependent ecosystem component underneath the majority of
container engine implementations in use today.

For any future reference implementation to be adopted by the OCI, it would
need to be kept in sync with the specification it implements. For a change
to be accepted to the spec, the equivalent implementation would need to be
authored and accepted as well.

## Should my Project be in the OCI?

The OCI receives proposals suggesting additions to the current suite
of project types listed above. We understand that a perfect framework
for determining inclusion or rejection of these proposals is an
intangible goal. However, we list the following considerations to help
guide future potential submissions.

 1. The OCI, unlike the CNCF, is not directly chartered for the advancement, marketing, and support of general cloud native software projects.
 2. Projects consumed via a UI and/or with a significant end user experience component are unlikely to be a good fit for the OCI model.
 3. The OCI has an small but active and vibrant group of participants today; however the specifications and related projects are a small niche of the overall cloud native world, and seeking out the OCI to validate or grow a community around a young project is unlikely to be a viable model. The CNCF is much more suited to that aim given the sandbox and maturity model.
