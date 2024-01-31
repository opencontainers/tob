# OCI Working Group: Reference Spec

# Reference Spec OCI Working Group - Governance Charter

This document describes the basic governance principles for the Reference Spec Working Group (the “WG”).

The WG operates as an OCI Working Group under the [Open Container Initiative (OCI) Charter](https://github.com/opencontainers/tob/blob/master/CHARTER.md), which describes the responsibilities of the OCI Technical Oversight Board (the "TOB”). The WG is established by the TOB as an OCI Working Group pursuant to the OCI Charter. Accordingly, the WG will operate in accordance with the OCI Charter and OCI's other policies and procedures, supplemented by the details below.

## Purpose

References are a string that is used by runtimes and other OCI registry clients to retrieve a container image.
They are currently a convention, used by many clients, adopted from Docker and implemented in distribution/distribution.
This WG seeks to define the syntax and parsing of a reference as an OCI spec.

## Scope

* Document the existing convention used by runtimes and other OCI registry clients.
* Specify the syntax for references to an [OCI Image Layout](https://github.com/opencontainers/image-spec/blob/7b36cea86235157d78528944cb94c3323ee0905c/image-layout.md) manifest, including support for a tag or digest.
* Define how the syntax can be extended to support other use cases, including:
  * Alternate layer formats
  * Immutable tags
  * Selecting an artifact that refers to another manifest (e.g. signature or SBOM)
* Provide backwards compatibility by using the existing reference convention when feasible.

## Out of Scope

* This WG will be limited to the creation of a new spec, and is not expected to impact other OCI specs.

## Intended work product

* Create a `reference-spec` with a formal specification for parsing a reference string.
* Provide a Go implementation of the spec.

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
