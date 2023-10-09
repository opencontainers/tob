# Working Group Proposal: FreeBSD Runtime

Proposal created from [OCI WG template](https://github.com/opencontainers/tob/blob/master/WG-TEMPLATE.md).

# FreeBSD Runtime OCI Working Group - Governance Charter

This document describes the basic governance principles for the FreeBSD Runtime Spec Working Group Working Group (the “WG”).

The WG operates as an OCI Working Group under the [Open Container Initiative (OCI) Charter](https://github.com/opencontainers/tob/blob/master/CHARTER.md), which describes the responsibilities of the OCI Technical Oversight Board (the "TOB”). The WG is established by the TOB as an OCI Working Group pursuant to the OCI Charter. Accordingly, the WG will operate in accordance with the OCI Charter and OCI's other policies and procedures, supplemented by the details below.

## Purpose

With two working OCI runtimes for FreeBSD
([runj](https://github.com/samuelkarp/runj),
[ocijail](https://github.com/dfr/ocijail)) and several container engines
including containerd, podman and cri-o, there is a need to define a
FreeBSD-specific section of the runtime-spec to allow support for platform
features such as resource limits and fine-grained jail permissions. This will
help to ensure runtime compatibility and build a consensus for the best way to
support FreeBSD container runtimes.

## Scope

* Define a FreeBSD extension to the runtime-spec similar in scope to the
  existing extensions for linux, solaris, windows etc.
  * Identify platform features which should be part of the FreeBSD spec.
  * Build consensus on how to represent these features clearly.

## Out of Scope

* Changes to non-FreeBSD platform-specific sections.
* Addition of any new FreeBSD-specific features to the generic sections of `config.json` unless those sections are already structured to include platform-specific information (such as Mounts).

## Intended work product

* Add config-freebsd.md to the runtime-spec repository along with suitable tests
  and support in specs-go.

## Proposed Owners

* Doug Rabson (@dfr)
* Samuel Karp (@samuelkarp)
* Ed Maste (@emaste)
* Dave Cottlehuber (@dch)

## Related issues/PRs

* https://github.com/samuelkarp/runj/issues/4
* https://github.com/samuelkarp/runj/issues/8
* https://github.com/samuelkarp/runj/issues/19
* https://github.com/samuelkarp/runj/issues/20
* https://github.com/samuelkarp/runj/pull/11

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
