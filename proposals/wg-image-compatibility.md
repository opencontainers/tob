# OCI Working Group Proposal: Image Compatibility

Proposal created from [OCI WG template](https://github.com/opencontainers/tob/blob/master/WG-TEMPLATE.md).

## Image Compatibility OCI Working Group - Governance Charter

This document describes the basic governance principles for the Image Compatibility Working Group (the “WG”).

The WG operates as an OCI Working Group under the [Open Container Initiative (OCI) Charter](https://github.com/opencontainers/tob/blob/master/CHARTER.md), which describes the responsibilities of the OCI Technical Oversight Board (the "TOB”).
The WG is established by the TOB as an OCI Working Group pursuant to the OCI Charter.
Accordingly, the WG will operate in accordance with the OCI Charter and OCI's other policies and procedures, supplemented by the details below.

## Purpose

In mission-critical industries, applications often require special features provided by host operating systems.
These are usually described in the release notes or installation guides.
We believe we have identified the missing puzzle in the OCI standard, the image compatibility, which is a key feature that describes the requirements of special containerized applications that have hard requirements for specific kernel versions, configurations, modules, or out-of-tree drivers.

For example, a container application free5GC UPF requiring the gtp5g kernel module will only be compatible with kernel 5.0.0-23-generic or 5.4.x due to the module's hard kernel version requirements - https://free5gc.org/guide/3-install-free5gc/.
If SR-IOV or GPU is required by the container, other requirements have to be specified against the host OS.
Kata Containers use cases are the best example: https://github.com/kata-containers/kata-containers/tree/main/docs/use-cases.

The described incompatibility issue applies to all use cases where specific host configuration is required, from bare-metal (e.g. high-performance computing) to distributed systems, from non-kubernetes to kubernetes orchestrated applications.

In multi-cloud or hybrid cloud scenarios, one containerized cloud-native application will need to run on different Kubernetes distributions that use different host operating systems on worker nodes.

For bare-metal and cloud operating systems can use different kernel versions with different configurations.
Different operating system distributions may integrate different devices and their corresponding drivers, even for the same device different versions of drivers may be used.
Therefore, different operating system distributions are not identical.
Even within the same OS distro, different releases are also not identical.

An image compatibility would help container image authors describe compatibility requirements in a standard way.
The specification will be uploaded with the image to the image registry.
This makes hard container compatibility requirements discoverable, programmable, and will support different consumers and cover use cases where the application requires a specific compatible environment.

For further reference please follow:
* [OCI Image Compatibility - the spec reasoning](https://docs.google.com/presentation/d/1F9GnCm2sULuyTJ5BEFZlL8Qjab81DK7g9Oy6qBfe5Qs/edit?usp=sharing)
* [Revisit container and host OS compatibility](https://docs.google.com/document/d/1lzwh8DGMu5vXXHwJmnewYIMffkcOEvH8owX4UYjRcw0/edit#heading=h.fcxt9vheg92c)

## Scope

* Define image compatibility that describes special host OS requirements of containerized application.
* The compatibility should describe container requirements for Linux, illumos and Windows.
* The final list of supported fields (like kernel modules, configuration, out-of-tree drivers etc.) is to be determined by the working group for each supported OS.
* An appropriate solution for expressing compatibility should be determined by the working group.

## Out of Scope

* Change images build or container execution flow.
* Introduce a new hard requirement to build images or run containers.
* Cover applications ABI compatibility.

## Intended work product

* The result of this WG should be extended or a new OCI specification that allows containers to describe host OS requirements.
* The specification will provide a much better experience for users to find out about container requirements against host OS, if those exist.
* The specification will provide programmatic data for various OS operators that could influence configuration of nodes.

## Proposed Owners

The following have agreed to participate in the working group, review progress, report progress back to the OCI community, and present the results to the TOB once the working group has completed its objectives.

* Marcin Franczyk (@mfranczy)
* Joe Huang (@chaoyihuang)
* Zvonko Kaiser (@zvonkok)
* Till Wegmüller (@toasterson)
* Toru Komatsu (@utam0k)
* B. Dewayne Branch (@GeoEducator)
* Samuel McGraw (@smcgrawDotNet)
* Vanessa Sochat (@vsoch)
* Brandon Mitchell (@sudo-bmitch)
* Aleksa Sarai (@cyphar)
* Jason Du (@xdu31)
* Dirk Mueller (@dirkmueller)
* Christian Kniep (@ChristianKniep)
* Bjorn Neergaard (@neersighted)

## Stakeholders

OCI Projects, non-OCI projects, or organizations sponsoring the working group and participating in the implementation and use case validation of the work done by the group.

* Huawei
* NVIDIA
* illumos
* OKD
* Intel
* SUSE
* HPC Container Advisory Council
* Docker, Inc.

## Related Issues/PRs

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
