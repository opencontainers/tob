# OCI artifact project proposal

## Abstract
Container registries, implementing the [distribution-spec][distribtuion-spec], provide reliable, highly scalable, secured storage services for container images. Customers either use a cloud provider implementation, vendor implementations, or instance the open source implementation of distribution. They configure security and networking to assure the images in the registry are locked down and accessible by the resources required. Cloud providers and vendors often provide additional values atop their registry implementations from security to productivity features. 

Applications and services typically require additional artifacts to deploy and manage, including [helm](https://helm.sh) for deployment and [Open Policy Agent (OPA)](https://github.com/open-policy-agent/opa/issues/1413) for policy enforcement.

Utilizing the [manifest][image-manifest] and [index][image-index] definitions, new artifacts can be stored and served using the [distribution-spec][distribution-spec] without changing the actual distribution spec. This repository will provide  a reference for artifact authors and registry implementors for supporting new artifact types with the existing implementations of distribution.

By providing an OCI artifact definition, the community can continue to innovate, focusing on new artifact types without having to build yet another storage solution (yass). 

## Proposal
Under the http://github.com/opencontainers organization:

- Create a new **artifacts** repository, named http://github.com/opencontainers/artifacts
- Update [distribution][distribution-spec] to generically reference [manifest][image-manifest] and [index][image-index], with image as one of many artifact types it can store. 

## Contents

The repository will serve 2 primary goals:

1. **artifact authors** - guidance for authoring new artifact types. Including a clearing house for well known artifact types.
1. **registry operators and vendors** - guidance for how they can support new artifact types, including how they can opt-in or out of well known artifact types. 

### Initial Maintainers
Initial maintainers of the artifacts project would be :
* Steve Lasker <steve.lasker@microsoft.com> (@stevelasker)
* Derek McGowan <derek.mcgowan@docker.com> @derekmcgowan
* Mike Brown <brownwm@us.ibm.com> @mikebrow

### Code of Conduct
This project would incorporate (by reference) the OCI [Code of Conduct][code-of-conduct].

### Governance and Releases
This project would incorporate the Governance and Releases processes from the OCI project template: https://github.com/opencontainers/project-template.

### Project Communications
Both of the proposed projects would continue to use existing channels in use by the OCI developer community for communication including:
* GitHub for issues and pull requests
* The dev@opencontainers.org email list
* The weekly OCI developer community conference call
* The #OpenContainers IRC channel

### Versioning / Roadmap
Artifacts will reference specific [distribution][distribution-spec], [index][image-index] and [manifest][image-manifest] versions in its examples, identifying any dependencies required. 

## Frequenty Asked Questions (FAQ)

**Q: Does this change the OCI Charter or Scope Table?**

A: No.  Artifacts are a prescriptive means of storing [index][image-index] and [manifest][image-manifest] within [distribution][distribution-spec] implementations. 

[distribution-spec]: https://github.com/opencontainers/distribution-spec/
[code-of-conduct]: https://github.com/opencontainers/org/blob/master/CODE_OF_CONDUCT.md
[image-manifest]: https://github.com/opencontainers/image-spec/blob/master/manifest.md
[image-index]: https://github.com/opencontainers/image-spec/blob/master/image-index.md