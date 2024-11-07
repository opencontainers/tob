# OCI cgroups project proposal

## Abstract
Having a common cgroups management implementation in OCI for use in and outside
of runc will ensure long lasting security and interoperability throughout the
container ecosystem.

## Proposal

Refactor and move cgroups packages out of runc into a separate project:

https://github.com/opencontainers/runc/tree/master/libcontainer/cgroups

The new project would live in the opencontainers github organization:

https://github.com/opencontainers/cgroups

A sample of how the project would look like is already here:

https://github.com/kolyshkin/opencontainers-cgroups

### Initial Maintainers
Initial maintainers of the cgroups project would be:

* Akihiro Suda <akihiro.suda.cz@hco.ntt.co.jp> (@AkihiroSuda)
* Aleksa Sarai <cyphar@cyphar.com> (@cyphar)
* Kir Kolyshkin <kolyshkin@gmail.com> (@kolyshkin)
* Mrunal Patel <mpatel@redhat.com> (@mrunalp)
* Sebastiaan van Stijn <github@gone.nl> (@thaJeztah)
* Odin Ugedal <odin@uged.al> (@odinuge)
* Peter Hunt <pehunt@redhat.com> (@haircommander)
* Davanum Srinivas <davanum@gmail.com> (@dims)

### Code of Conduct
This project would incorporate (by reference) the OCI [Code of Conduct][code-of-conduct].

### Governance and Releases
This project would incorporate the Governance and Releases processes from the
OCI project template: https://github.com/opencontainers/project-template.

### Project Communications
The proposed project would continue to use existing channels in use by the OCI
developer community for communication including:
* GitHub for issues and pull requests
* The dev@opencontainers.org email list
* The weekly OCI developer community conference call
* The #OpenContainers IRC channel

### Versioning / Roadmap

We'll start with v0.x until everything is stabilized after the split.

The plan is to have frequent releases to accommodate various users.

## Frequently Asked Questions (FAQ)
*Q: Does this change the OCI Charter or Scope Table?*
A: No. Nothing in this proposal is intended to amend the
[OCI Charter](https://www.opencontainers.org/about/governance) or
[OCI Scope Table](https://www.opencontainers.org/about/oci-scope-table).

*Q: Why move this out of the runc project?*
A: To be able to reuse this in different container projects, while avoiding
code duplication and fragmentation. This involves adding functionality and
cutting releases to accomodate existing users other than runc.

Here's an example: kubernetes needs PSI stats from cgroups, and while the
low-level functionality needed
([runc PR #3900](https://github.com/opencontainers/runc/pull/3900))
was merged in July 2023, it was only made available to kubernetes when runc
v1.2.0 was tagged in October 2024. Such delays might result in using
unversioned dependencies, or copying the code around and thus fragmentation.

A longer term goal is make this set of packages even more modular, avoiding
excessive third-party dependencies.

*Q: Who are the other target users of these packages?*

A: CRI-O, kubernetes, cadvisor.

[code-of-conduct]: https://github.com/opencontainers/org/blob/master/CODE_OF_CONDUCT.md
