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
* Stephen Smalley <sds@tycho.nsa.gov> (@stephensmalley)

### Code of Conduct
This project would incorporate (by reference) the OCI [Code of Conduct][code-of-conduct].

### Governance and Releases
This project would incorporate the Governance and Releases processes from the OCI project template: https://github.com/opencontainers/project-template.

### Project Communications
The proposed project would continue to use existing channels in use by the OCI developer community for communication including:
* GitHub for issues and pull requests
* The dev@opencontainers.org email list
* The weekly OCI developer community conference call
* The #OpenContainers IRC channel

### Versioning / Roadmap
We will probably minimize the releases of this project.

## Frequently Asked Questions (FAQ)
Q: Does this change the OCI Charter or Scope Table?
A: No.  Nothing in this proposal is intended to amend the [OCI Charter](https://www.opencontainers.org/about/governance) or [OCI Scope Table](https://www.opencontainers.org/about/oci-scope-table).

*Q: Why move this out of the runc project?*

A: To be able to reuse this in different container projects as well as have dedicated maintainers for the SELinux library. Getting more exposure and others to use it would probably lead to completing lots of features that are missing from the libcontainer/selinux bindings. There are lots of bindings in libselinux that do not have native bindings yet. Getting other projects to use SELinux bindings would also lead to potential improvements in the bindings.

*Q: Why is versioning this package with runc insufficient today? What issues have been encountered?*

A: There's no versioning of selinux in run.  For instance, we fixed something in selinux in runc because CRI-O needed it but at the same time we broke docker which was relying on it. Having fixed versions for selinux wouldn't have led to this issue since docker could have stuck to a previous version and carefully test the new version w/o pulling new changes as part of a libcontainer library bump.

*Q: Who are the other target users of go-selinux?*

A: docker, rkt, CRI-O, kubernetes, any other project out there requiring a dedicated selinux library.

[code-of-conduct]: https://github.com/opencontainers/org/blob/master/CODE_OF_CONDUCT.md
