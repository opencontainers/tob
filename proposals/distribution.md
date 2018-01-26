# Abstract

The Docker registry protocol has become the defacto standard across the container registry world ([https://github.com/docker/distribution/blob/master/docs/spec/api.md](https://github.com/docker/distribution/blob/master/docs/spec/api.md)).

In the OCI, having a solid, common distribution specification with conformance testing will ensure long lasting security and interoperability throughout the container ecosystem.

## Proposal

TL;DR; Move [https://github.com/docker/distribution/tree/master/docs/spec](https://github.com/docker/distribution/tree/master/docs/spec) to [https://github.com/opencontainers/distribution-spec](https://github.com/opencontainers/distribution-spec)

This proposal covers the distribution API spec, and while it does not cover the code for the docker-registry, that implementation is considered the reference implementation. There are other implementations of this protocol, not all are open-source though (Google gcr.io, Amazon ECR, CoreOS Quay, Gitlab registry, JFrog Artifactory registry, Huawei Dockyard, etc).

In the past when the topic of having an OCI specification around the distribution of container images was discussed, it was deferred as "let’s get the image format defined, meanwhile the industry will settle on a distribution standard". Fast forward, OCI image format is out and adopted, and the Registry v2 is the defacto standard. There is and will be use-cases for alternate methods and the future will likely hold creative ways to push, fetch and share container images, but right now this promotion serves to acknowledge by the OCI the current industry standard of distributing container images.

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

* Does this include the code of the docker-registry?
    * No. This is an API specification discussion.
