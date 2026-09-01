# Getting Started

While the [OCI Charter](./CHARTER.md) is our official governing document, many
people have asked for a gentler introduction to the Open Container Initiative as
well as general guidance on how to interact with the projects and specifications
found under the OCI umbrella. This document attempts to be that starting point
for those who may be new to the OCI, interested in participation, or who want to
understand if a project is a fit for inclusion or contribution to the OCI.

**Note:** If there are any perceived or real conflicts between this document
and the OCI Charter, the OCI Charter takes precedence as the official governing
document of the Open Container Initiative.

## What is the OCI?

The [OCI website](https://opencontainers.org) has since inception carried a
mission statement that defined us as "an open governance structure for the
express purpose of creating open industry standards around container formats
and runtime." Created in 2015, the core initial purpose was to align Docker and
other ecosystem players around a runtime and image specification that would
become an industry baseline for how images are packaged and executed in OCI
compliant runtimes.

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
of OCI into ongoing support of additional types within registries and related
cloud native tools. Specifically, [artifacts](https://github.com/opencontainers/artifacts)
expands the concept around the **what** when discussing non-OCI image content
(Helm charts, Singularity container images, SPDX, source bundles, etc.) and
registries, and allows for further experimentation with arbitrary file types
within the context of this stable andd well-defined capability.

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

Artifacts is not a standalone specification, but fits within this category
as it is a repository which serves as the extension point for media types
which include the core media types found within the image spec, as well as
connecting those and additional media types with the distribution spec as
the means for storage, query, and delivery of a growing list of well-defined
artifact types defined within the project.
 - [Artifacts](https://github.com/opencontainers/artifacts)

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

The OCI does not require that its specifications have reference
implementations, and any project which aims to be adopted by the OCI as a
reference implementation has to be judged on its own merits. Reference
implementations should be generally usable as a building block for other
programs (thus should not be *overly opinionated*) and should have their
features limited to the set of features outlined by the relevant specification.
In addition, the popularity of the project (especially in production use-cases)
should be taken into consideration: reference implementations should be
battle-tested, after all.

The first (and currently only viable) reference implementation included in the
OCI was runc, as a reference implementation of the OCI runtime specification.
This project's inclusion is a slight oddity of history, having been a
production-ready project predating the OCI's formation and was included in the
OCI as part of the original draft runtime specification. However this strange
history does not preclude the addition of any new reference implementations,
merely that this is a process which is not well-established in the OCI and thus
any proposed projects need to have significant justification for inclusion.

 - [runc](https://github.com/opencontainers/runc)

## Should my Project be in the OCI?

The OCI receives proposals suggesting additions to the current suite
of project types listed above. We understand that a perfect framework
for determining inclusion or rejection of these proposals is an
intangible goal. However, the following considerations are provided
to help guide potential submissions.

 * The OCI is not directly chartered for the advancement, marketing, and
 support of general cloud native software projects. As our charter states: *The
 Open Container Initiative does not seek to be a marketing organization, define
 a full stack or solution requirements, and will strive to avoid standardizing
 technical areas undergoing innovation and debate.*
 * The project should be a piece of "**boring core container infrastructure**".
 While this is partially subjective criterion, the key factors towards
 fulfilling this requirement are:
   1. The project should be as un-opinionated and extensible as is reasonably
   possible.
   2. Rather than being a complete solution or framework, the project should be
   usable as a building-block for larger solutions and frameworks.
   3. Projects consumed via a UI and/or including a significant end user
   experience component may be one clear sign of a lack of fit with the OCI
   as one example.
 * Proposed projects should fit logically into the scope and mission of the
 OCI: a home for open standards and tools which underpin the wider container
 ecosystem. Proposed additions to the OCI should not conflict with existing OCI
 projects, nor should they be completely unrelated to existing OCI projects.
 The precise scope of the OCI is defined by the OCI Charter, but the TOB may
 choose to expand the scope if they feel it is within the mission of the OCI.

In summary, the OCI has a small but active and vibrant group of participants
today. However the OCI specifications and related OCI projects are but a small
niche of the overall cloud native world, and seeking out the OCI to validate
or grow a community around an untested or experimental new project is highly
unlikely to fit the more narrow scope and mission of the OCI. We recommend
the CNCF as a much more suitable target for such projects given the maturity
model and sandbox starting point within that community.
