# OCI go-selinux project proposal

## Abstract
Having a solid, battle-proven, common selinux implementation in OCI for use in and outside of runc will ensure long lasting security and interoperability throughout the container ecosystem.

## Proposal
Refactor and move the selinux library out of runc into a separate project:

https://github.com/opencontainers/runc/tree/master/libcontainer/selinux

The new project would live in the opencontainers github organization:

https://github.com/opencontainers/go-selinux

A sample of how the project would look like is already here:

https://github.com/runcom/go-selinux

### Initial Maintainers
Initial maintainers of the go-selinux project would be:

* Antonio Murdaca <runcom@redhat.com> (@runcom)
* Daniel J Walsh <dwalsh@redhat.com> (@rhatdan)
* Mrunal Patel <mpatel@redhat.com> (@mrunalp)
* TODO

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

## Frequently Asked Questions (FAQ)
Q: Does this change the OCI Charter or Scope Table?
A: No.  Nothing in this proposal is intended to amend the OCI Charter (https://www.opencontainers.org/about/governance) or OCI Scope Table (https://www.opencontainers.org/about/oci-scope-table).

Q: Why move this out of the runc project?
A: TODO
