# OCI go-digest project proposal

## Abstract
[image-spec#486][image-spec-486] introduces a dependency on a stable upstream implementation of https://github.com/docker/go-digest, which was recently broken out of the https://github.com/docker/distribution project.

This package has been instrumental in providing a strong hash-identity implementation in Go and we will extend this to OCI. This will be supported by moving https://github.com/opencontainers/go-digest to OCI. While this package does support opencontainers/image-spec, it is broadly useful in other image formats or outside image formats.

Having a solid, battle-proven, common digest implementation in OCI for use in and outside the image-spec will ensure long lasting security and interoperability throughout the container ecosystem.

## Proposal
With repositories under the http://github.com/opencontainers organization:

Rename (transfer) https://github.com/docker/go-digest would become https://github.com/opencontainers/go-digest.

### Initial Maintainers
Initial maintainers of the go-digest project would be seeded from the image-spec project:
* Brandon Philips <brandon.philips@coreos.com> (@philips)
* Brendan Burns <bburns@microsoft.com> (@brendandburns)
* Jason Bouzane <jbouzane@google.com> (@jbouzane)
* John Starks <jostarks@microsoft.com> (@jstarks)
* Jonathan Boulle <jon.boulle@coreos.com> (@jonboulle)
* Stephen Day <stephen.day@docker.com> (@stevvooe)
* Vincent Batts <vbatts@redhat.com> (@vbatts)

### Code of Conduct
This project would incorporate (by reference) the OCI Code of Conduct.

### Governance and Releases
This project would incorporate the Governance and Releases processes from the OCI project template: https://github.com/opencontainers/project-template.

### Project Communications
Both of the proposed projects would continue to use existing channels in use by the OCI developer community for communication including:
* GitHub for issues and pull requests
* The dev@opencontainers.org email list
* The weekly OCI developer community conference call
* The #OpenContainers IRC channel

### Versioning / Roadmap
We will probably minimize the releases of this project.

It will provide digesting functionality for all present and future versions of the specification.

## Frequenty Asked Questions (FAQ)
Q: Does this change the OCI Charter or Scope Table?
A: No.  Nothing in this proposal is intended to amend the OCI Charter (https://www.opencontainers.org/about/governance) or OCI Scope Table (https://www.opencontainers.org/about/oci-scope-table).

[image-spec-486]: https://github.com/opencontainers/image-spec/pull/486
