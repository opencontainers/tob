# OCI Artifacts Project Proposal

## Abstract

Container registries, implementing the [OCI distribution-spec][distribution-spec], provide reliable, highly scalable, secured storage services for container images. Customers use cloud provider implementations, vendor implementations, and instances of the open source implementation of docker distribution. They configure security and networking to assure the images in the registry are locked down and accessible by the resources required. Cloud providers and vendors often provide additional value atop their registry implementations from security to productivity features. 

Applications and services typically require additional artifacts to deploy and manage container images, including [helm](https://helm.sh) charts for deployment and [Open Policy Agent (OPA) bundles](https://github.com/open-policy-agent/opa/issues/1413) for policy enforcement.

Utilizing the [OCI manifest][image-manifest] and [OCI index][image-index] definitions, new artifact types can be stored and served using the [OCI distribution-spec][distribution-spec] without changing the actual distribution spec. This repository will provide a reference for artifact authors and registry implementors for supporting these new artifact types themselves with the existing implementations of distribution.

By providing support for OCI artifact types over OCI distributions, the community can continue to innovate, focusing on new artifact types without having to build yet another storage solution (YASS). 

## Proposal

Under the [github.com/opencontainers](http://github.com/opencontainers) organization:

- Create a new **artifacts** repository, named [github.com/opencontainers/artifacts](http://github.com/opencontainers/artifacts)
- Update the [OCI distribution-spec][distribution-spec] to generically reference [OCI manifest][image-manifest] and [OCI index][image-index], with [OCI Image][image-spec] as one of many artifact types it can store. 
- Update the [OCI image-spec][image-spec] to reference images as an implementation of artifacts, using [OCI manifest][image-manifest] and [OCI index][image-index]

## Contents

The repository will serve 3 primary goals:

1. **artifact authors** - guidance for authoring new artifact types. Including a clearing house for well known artifact types.
1. **registry operators and vendors** - guidance for how operators and vendors can support new artifact types, including how they can opt-in or out of well known artifact types. Registry operators that already implement `media-type` filtering will not have to change. The artifact repo will provide context on how new `media-type`s can be used, and how `media-type`s can be associated with a type of artifact. 
1. **clearing house for well known artifacts** - artifact authors can submit their artifact definitions, providing registry operators a list by which they can easily support. 

### Process for Approving New Artifact Definitions

1. Proposals for new artifact types should be opened as pull requests on the artifact repository
1. The artifact project maintainers will review new proposals, ask clarifying questions, and choose or not to accept the suggested artifact type
1. Acceptance requires at least 2 +1s from the maintainers (currently 3 maintainers)
1. Where the submitter disagrees strongly with the decision they can bring to the issue to the TOB for a vote, under the current voting rules.

### Initial Maintainers

Initial maintainers of the artifacts project would be :

- Steve Lasker <steve.lasker@microsoft.com> (@stevelasker)
- Derek McGowan <derek.mcgowan@docker.com> (@derekmcgowan)
- Mike Brown <brownwm@us.ibm.com> (@mikebrow)
- Stephen Day <stevvooe@gmail.com> (@stevvooe)

### Code of Conduct

This project would incorporate (by reference) the [OCI Code of Conduct][code-of-conduct].

### Governance and Releases

This project would further incorporate the Governance and Releases processes from the OCI project template: [github.com/opencontainers/project-template](https://github.com/opencontainers/project-template).

### Project Communications

This project would continue to use existing channels in use by the [OCI developer community for communication](https://github.com/opencontainers/org#communications)

### Versioning / Roadmap

This repository will not be versioned, but will be continuously updated with a list of versioned types with historical references. This repository will not have releases.

Artifacts will reference specific [OCI distribution][distribution-spec], [OCI index][image-index] and [OCI manifest][image-manifest] versions in its examples and references for capabilities.

## Frequently Asked Questions (FAQ)

**Q: Does this change the OCI Charter or Scope Table?**

A: No. Artifacts are a prescriptive means of storing [OCI index][image-index] and [OCI manifest][image-manifest] within [OCI distribution][distribution-spec] implementations. 

[distribution-spec]: https://github.com/opencontainers/distribution-spec/
[image-spec]: https://github.com/opencontainers/image-spec/
[code-of-conduct]: https://github.com/opencontainers/org/blob/master/CODE_OF_CONDUCT.md
[image-manifest]: https://github.com/opencontainers/image-spec/blob/master/manifest.md
[image-index]: https://github.com/opencontainers/image-spec/blob/master/image-index.md
