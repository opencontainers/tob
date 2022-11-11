# OCI Working Group Proposal: Authentication and Authorization

Proposal created from [OCI WG template](https://github.com/opencontainers/tob/blob/master/WG-TEMPLATE.md).

## Auth OCI Working Group - Governance Charter

This document describes the basic governance principles for the Auth Working Group (the “WG”).

The WG operates as an OCI Working Group under the [Open Container Initiative (OCI) Charter](https://github.com/opencontainers/tob/blob/master/CHARTER.md), which describes the responsibilities of the OCI Technical Oversight Board (the "TOB”).
The WG is established by the TOB as an OCI Working Group pursuant to the OCI Charter.
Accordingly, the WG will operate in accordance with the OCI Charter and OCI's other policies and procedures, supplemented by the details below.

## Purpose

Authentication and authorization are a key requirement for registries to control access.
Implementations of this in registries and clients have roughly followed standards set by Docker and have mostly focused on compatibility with specific implementations of registries or clients.
This working group will define a standard to be supported by OCI compatible registries and clients when support for authentication and authorization is required.

## Scope

* Define registry responses to unauthenticated requests.
* Define supported authentication methods (e.g. basic and bearer authentication).
* Specify how clients negotiate access a repository and different types of access to that repository (e.g. pull and push).
* Specify how clients negotiate access to multiple repositories for actions like a cross-repository blob mount.
* Specify how clients and registries should renegotiate access for a request with expired or insufficient authorization.
* Specify expected lifetime of registry credentials.
* Avoid specifications that would prevent added functionality (e.g. fine grain access control).

## Out of Scope

* Registries and clients that do not require authentication and authorization support should be unaffected by these changes.
* How clients store and access credentials, including credential helpers, will remain undefined.

## Intended work product

* The result of this WG should be a PR to the distribution-spec.
* Effort should be made to avoid breaking changes to existing registries and clients.
* Effort should be made to utilize existing IETF standards when appropriate.

## Related Issues/PRs

* <https://github.com/opencontainers/distribution-spec/issues/240>
* <https://github.com/opencontainers/distribution-spec/issues/338>

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
