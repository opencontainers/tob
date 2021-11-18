# Working Group Proposal: Reference Types

Proposal created from [OCI WG template](https://github.com/opencontainers/tob/blob/master/WG-TEMPLATE.md).

Proposal copied from [Proposal: Working Group for Reference Types #96](https://github.com/opencontainers/tob/issues/96)

## Reference Types OCI Working Group - Governance Charter

This document describes the basic governance principles for the Reference Types Working Group (the “WG”).

The WG operates as an OCI Working Group under the [Open Container Initiative (OCI) Charter](https://github.com/opencontainers/tob/blob/master/CHARTER.md), which describes the responsibilities of the OCI Technical Oversight Board (the "TOB”). The WG is established by the TOB as an OCI Working Group pursuant to the OCI Charter. Accordingly, the WG will operate in accordance with the OCI Charter and OCI's other policies and procedures, supplemented by the details below.

## Purpose

As cloud native development continues to grow, there is increased interest in evolving registries to natively store, discover, and pull a graph of content associated with specific container images in a registry. Use cases for said associated artifacts include but are not limited to Software Bill of Materials (SBoM), security scan results, and signing. Having a native way to store and discover artifacts associated with other artifacts enables end-users to answer the question of: “What SBOMs or signatures are associated with this container image?”

## Scope

* Define and deliver the capability to store, discover, and pull a graph of artifacts associated with a specific artifacts to OCI distribution compliant registries. These set of capabilities has been commonly known as "reference types" or "references".
  * Define supported use cases
  * Document impact to existing user-facing tools and registries
  * Define the method for creating, distributing, and discovering referenced objects
  * Document user expectations for promoting an artifact between registries with its references
  * Document onboarding process for registries and user-facing tools to adopt reference types
  * Defined expectations for artifact reference lifecycle management
  * Deliver a reference implementation of the reference types proposal

## Out of Scope

* Identified out of scope items will be listed here as WG progresses


## Intended work product

* Referrers API specification that provides the ability to discover references to existing container images. These include listing signatures, SBoMs, security scan results that refer to the digest of a manifest. The referrers API specification will sit within or along side the Distribution specification.
* Identify, and document the pros and cons for versioning the existing manifests, compared with creating a new manifest to support reference types.

## Proposed Owners
* Lachlan Evenson (@lachie83)
* Justin Cormack (@justincormack)
* Michael Brown (@michaelb990)
* Derek McGowan (@dmcgowan)
* Jon Johnson (@jonjohnsonjr)

## Sponsors

* Microsoft
* AWS
* Docker

## Related issues/PRs

* https://github.com/opencontainers/tob/issues/96
* https://github.com/opencontainers/artifacts/pull/27
* https://github.com/opencontainers/artifacts/pull/29
* https://github.com/opencontainers/artifacts/pull/37
* https://github.com/opencontainers/image-spec/issues/827
* https://github.com/opencontainers/image-spec/pull/828
* https://github.com/oras-project/artifacts-spec/

## Governance

* **Working Group**:
  * The TOB is establishing the WG as an OCI Working Group, pursuant to [section 6(p)](https://github.com/opencontainers/tob/blob/master/CHARTER.md#6-technical-oversight-board-tob) of the OCI Charter.
* **Owners**:
  * The WG proposal to the TOB will specify one or more initial "owners" of the WG.
  * The current owners will be listed in the [OCI Working Group documentation](https://github.com/opencontainers/tob/blob/master/WG-INFO.md).
  * The owners shall be responsible for:
    * scheduling regular meetings of the WG community;
    * facilitating open discussion among WG community participants;
    * coordinating and managing the development of the WG work product and outputs;
    * recording decisions that are reached by the WG community; and
    * keeping the TOB regularly informed about the status of the WG’s efforts, including when the WG has readied the work product and outputs for TOB approval.
* **Maintainers**:
  * If the WG owners request the TOB to approve a draft specification as a released OCI Specification, the request shall include a list of proposed "maintainers" of the OCI Specification.
  * The current maintainers will be listed in the [OCI Working Group documentation](https://github.com/opencontainers/tob/blob/master/WG-INFO.md).
  * The maintainers shall be responsible for continuing the work of overseeing updates, improvements and changes to a released OCI Specification on an ongoing basis.
* **Meetings**:
  * Meetings of the WG shall be open to the public.
  * Participants in the meetings shall comply with the [OCI Code of Conduct](https://github.com/opencontainers/.github/blob/master/CODE_OF_CONDUCT.md) and all other policies of OCI and The Linux Foundation.
* **TOB Approval**:
  * The WG shall operate pursuant to the procedures set forth in [section 6(p)](https://github.com/opencontainers/tob/blob/master/CHARTER.md#6-technical-oversight-board-tob) of the OCI Charter, with regards to obtaining TOB approval for initial release of the work product and outputs as an OCI Specification or other OCI Project, and for subsequent maintenance activities thereafter.
* **Amendments**:
  * The owners of the WG may from time to time propose to the TOB (1) amendments to this WG Governance Document, and/or (2) changes to the composition of the owners or maintainers of the WG.
  * As set forth in the OCI Charter, the TOB may, in its discretion by a two-thirds vote, approve or reject the requested amendments or changes.
  * As set forth in the OCI Charter, the TOB may also disband the WG by a two-thirds vote.