# Abstract

The Docker registry protocol has become the defacto standard across the container registry world.

In the OCI, having a solid, common distribution specification with conformance testing will ensure long lasting security and interoperability throughout the container ecosystem.

## Proposal

TL;DR; Move [`api.md`][api.md] to a new [distribution-spec project](https://github.com/opencontainers/distribution-spec).

This proposal covers the distribution API spec, and while it does not cover the code for the docker-registry, that implementation is considered the reference implementation. There are other implementations of this protocol, not all are open-source though (Google gcr.io, Amazon ECR, CoreOS Quay, Gitlab registry, JFrog Artifactory registry, Huawei Dockyard, etc).

In the past when the topic of having an OCI specification around the distribution of container images was discussed, it was deferred as "let’s get the image format defined, meanwhile the industry will settle on a distribution standard". Fast forward, OCI image format is out and adopted, and the Registry v2 is the defacto standard. There is and will be use-cases for alternate methods and the future will likely hold creative ways to push, fetch and share container images, but right now this promotion serves to acknowledge by the OCI the current industry standard of distributing container images.
This proposal also provides the container ecosystem with a means to discuss and schedule extensions to the distribution specification.

There is polish that is needed e.g. broken links to storage-driver docs, as well as making sections more generic regarding the OCI descriptors and media-types, but on the whole this is a lateral move.

## Initial Maintainers

* Stephen Day <stephen.day@docker.com> (@stevvooe)
* Vincent Batts <vbatts@redhat.com> (@vbatts)
* Derek McGowan <derek.mcgowan@docker.com> (@dmcgowan)

Additional Maintainers to consider:

* Ahmet Alp Balkan (Google)
* Matt Moore (Google)
* Yuwa (MSFT)
* Clayton Coleman (Red Hat)
* Antonio Murdaca (@runcom) (Red Hat)
* Samuel Karp (@samuelkarp) (AWS)
* Mike Brown (IBM)
* Jimmy Zelinskie jimmy@coreos.com (@jzelinskie)
* Liu Genping <[liugenping@huawei.com](mailto:liugenping@huawei.com)>
* Vanessa Sochat (@vsoch) (Stanford) <vsochat@stanford.edu>
* Eduardo Arango (@ArangoGutierrez) (Sylabs) <eduardo@sylabs.io>

## Code of Conduct

This project would incorporate (by reference) the OCI Code of Conduct ([https://github.com/opencontainers/tob/blob/master/code-of-conduct.md](https://github.com/opencontainers/tob/blob/master/code-of-conduct.md)).

## Governance and Releases

This project would incorporate the Governance and Releases processes from the OCI project template: [https://github.com/opencontainers/project-template](https://github.com/opencontainers/project-template).

## Project Communications

Both of the proposed projects would continue to use existing channels in use by the OCI developer community for communication including:

* GitHub for issues and pull requests
* The dev@opencontainers.org email list
* The monthly OCI developer community conference call
* The #OpenContainers freenode IRC channel

## Versioning / Roadmap

The API spec is currently considered v2 and we will start the specification at v2.0. Fewer places to change and compare, and it would keep with it being a lateral move.

## Frequently Asked Questions (FAQ)

**Q: Does this include the code of the docker-registry?**

A: No. This is an API specification discussion.

**Q: Does this change the OCI Charter or Scope Table?**

A: Not the charter, but it does change the scope table.
This project is scoped to specifying per-image client ↔ registry interaction with an [HTTP][rfc7230]-based protocol.
The following scope entries should be removed from the [scope table][scope]:

* “Use of Hash as Content Addressable name for immutable containers”.
    This entry is in scope for this project, and a more detailed entry will be added as described below.
* “Creating Reference spec for optional DNS based naming & distribution”.
    This entry conflates naming and distribution, which will be separated by this proposal.
* “Standardizing on a particular Distribution method”.
    This proposal will provide one (of possibly many) distribution specifications, so the old “There is no current agreement on how to distribute content” no longer applies.

The following entries should be added to the [scope table][scope]:

* “Specifying authentication and authorization schemes”.
    Docker's current registry uses an [extension][token] of the [`Bearer`][rfc6750] [auth scheme][rfc7235-s2.1].
    Work on specifying Docker's scheme will continue independently, and is orthogonal to the registry API.

    * What: Specifying authentication and authorization schemes
    * In/Out/Future: Out of scope
    * Status: N/A
    * Description: Defining protocols for authenticating and authorizing distribution access.
    * Why: As an HTTP-based protocol, clients and servers can negotiate authentication via HTTP's [challenge-response authentication framework][rfc7235-s2.1].

* “Creating a reference spec for optional DNS based naming and discovery”.
    Discovery and registry protocols are completely separate and do not need to be added together.
    This entry replaces part of the previous “Creating Reference spec for optional DNS based naming & distribution” entry.

    * What: Creating a reference spec for optional DNS based naming and discovery
    * In/Out/Future: In scope for future specification
    * Status: Work not yet started
    * Description: Define a protocol for resolving an image name to retrieval information.
        When we address this, we will also allow for alternative name-to-image discovery protocols in parallel with the OCI-specified protocol.
    * Why: It is reasonable to provide a standardized way to use DNS based distribution in conjunction with OCI without requiring its use.
        There are many good use cases for DNS based distribution, but not all use cases support this.
        Furthermore, encoding the location of a bundle into the bundle can cause issues with downloads from alternate locations other than the origin specified in the name.

* “Specifying a distribution method”.
    This entry replaces part of the previous “Creating Reference spec for optional DNS based naming & distribution” and “Standardizing on a particular Distribution method” entries.

    Retrieving image indexes covers the current “tag listing” (e.g. “what named manifests are in `library/busybox`?”), because tags are entries in the image format's [`manifests` array][manifests].
    Other tag-listing endpoints needed for backwards-compatibility are therefore in scope as well.

    Grouping image indexes in repositories is considered part of distribution policy or content management, which are out of scope for this entry's per-image action.
    For example, “what images are under `library/`?” is out of scope for this project.

    * What: Specifying a distribution method
    * In/Out/Future: In scope
    * Status: In progress (see opencontainers/distribution-spec)
    * Description: Define a protocol for creating, retrieving, updating, and deleting objects defined in the [image specification][image-spec].
        Listing repositories (like [`/v2/_catalog`][catalog]) is a multi-[image-index][] action, which is out of scope for this entry.
        Managing groups of image indexes requires multi-[image-index][] actions, which are out of scope for this entry.
        Listing image indexes within a group is a multi-[image-index][] action, which is out of scope for this entry.
    * Why: This specification will provide one (of possibly many) distribution specifications.
        Alternative distribution specifications may be developed for uses cases not covered by this specification, but defining them is currently out of scope for the OCI.

* “Retrieving image content by its content-addressable hash”.
    Docker's registry API already provides [endpoints for fetching manifest objects by digest][get-manifest].
    Docker's registry API does not currently provide endpoints for fetching [image-index][] objects by digest, but this is the project where that will happen.

    * What: Retrieving image content by its content-addressable hash
    * In/Out/Future: In scope
    * Status: In progress (see opencontainers/distribution-spec)
    * Description: Specify a protocol for retrieving an [image index][image-index], [manifest][], or other [image specification][image-spec] object from a distribution engine by its content-addressable hash.
    * Why: Using a hash as a name is a way to ensure a unique image name without relying on a particular naming authority or system.
        Using hashing for name is an acceptable addition as it does not encode any centralized namespace.

The following entries should remain in the [scope table][scope] but not be addressed by this project:

* “Specifying way to attach signatures”.
    We don't need to address this as part of distribution, because all resources are content-addressable and can be signed in external systems.

## Related GitHub Issues

* Simplifies tag listing: docker/distribution#2169
* Allows listing of manifests: docker/distribution#2199

[api.md]: https://github.com/docker/distribution/blob/5cb406d511b7b9163bff9b6439072e4892e5ae3b/docs/spec/api.md
[catalog]: https://github.com/docker/distribution/blob/5cb406d511b7b9163bff9b6439072e4892e5ae3b/docs/spec/api.md#catalog
[get-manifest]: https://github.com/docker/distribution/blob/5cb406d511b7b9163bff9b6439072e4892e5ae3b/docs/spec/api.md#pulling-an-image-manifest
[image-spec]: https://github.com/opencontainers/image-spec/
[image-index]: https://github.com/opencontainers/image-spec/blame/v1.0.1/image-index.md
[manifest]: https://github.com/opencontainers/image-spec/blob/v1.0.1/manifest.md
[manifests]: https://github.com/opencontainers/image-spec/blame/v1.0.1/image-index.md#L23
[rfc6750]: https://tools.ietf.org/html/rfc6750
[rfc7230]: https://tools.ietf.org/html/rfc7230
[rfc7235-s2.1]: https://tools.ietf.org/html/rfc7235#section-2.1
[scope]: https://www.opencontainers.org/about/oci-scope-table
[token]: https://github.com/docker/distribution/blob/5cb406d511b7b9163bff9b6439072e4892e5ae3b/docs/spec/auth/token.md
