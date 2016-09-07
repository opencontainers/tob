# OCI Runtime-Tools and Image-Tools Project Proposals

## Abstract
The below proposal contemplates creation of two tools projects (runtime-tools and image-tools.)
These would be associated with the OCI specification projects (runtime-spec and image-spec) and serve as repositories for testing  tools. 

## Background
Testing tools have been organically developed by the OCI developer community.
These include:
* Runtime-spec test code in a OCITools repository
* Image-spec test code in the image-spec repository

On Monday, August 22nd, 2016, the OCI Certification Program WG designated Chris Aniszczyk and Rob Dolin to draft a proposal for formalizing approval of tools.

On Wednesday, August 24th, 2016, the OCI Developer Community (TDC) met and recommended establishing a tools repository corresponding to each of the spec repositories.  

## Proposal
With repositories under the http://github.com/OpenContainers organization:
* Rename the OCITools repository as runtime-tools
* Create a new repository named image-tools and populate this with the files from: https://github.com/opencontainers/image-spec/tree/master/cmd/oci-image-tool

### Project Descriptions
Below are brief draft project descriptions intended to serve as an initial abstract for each project:
* Runtime-Tools: Tools for testing of container runtimes implementing the OCI runtime-spec.  
This includes code that tests a runtime's conformance to the OCI Container Runtime spec.
* Image-Tools: Tools for testing of container images implementing the OCI image-spec.  
This includes code that validates a file's conformance to the OCI Container Image Format spec.  

### Initial Maintainers
Initial maintainers of the runtime-tools project:
* Maintainers of the runtime-spec project

Initial maintainers of the image-tools project shall be:
* Maintainers of the image-spec project

### Code of Conduct
Both of the proposed projects would incorporate (by reference) the OCI Code of Conduct

### Governance and Releases
Both of the proposed projects would incorporate the Governance and Releases processes from the OCI project template: https://github.com/opencontainers/project-template.

### Project Communications
Both of the proposed projects would continue to use existing channels in use by the OCI developer community for communication including:
* GitHub for issues and pull requests
* The dev@opencontainers.org email list
* The weekly OCI developer community conference call
* The #OpenContainers IRC channel

### Versioning / Roadmap
Released version numbers of the runtime-tools and image-tools projects should roughly align with released verions of the associated specs projects.

It is expected that releases of the tools projects will follow releases of the specs projects by anywhere from a few days to a few months.

## Frequenty Asked Questions (FAQ)
Q: What about the runc project?
A: This proposal would not impact runc.  
Runc is a reference implementation of the runtime-spec and it lives in its own repo.

Q: What about schemas?
A: It would be up to the OCI developer community to determine if schemas fit best with the specs or tools projects.

Q: Why are the repo names plural (tools) instead of singular (tool)?
A: There may be multiple tools or a single tool with multiple functionalities.

Q: Why not prefix the repo names with "oci-" aligning to the CLI commands for invoking the tools?
A: The repos will be under the http://www.github.com/OpenContainers/ organization.

Q: Why two tools repos?
A: Having a tools repo for each spec repo allows for releasing a tools repo shortly after a spec stabilizes even if the other tools repo is in a state of flux.

Q: Why is contribution count used to identify potential maintainers?
A: Contribution count is not a great metric for the value of a contributor's contributions, but this seemed like a reasonable, rough way to identify additional potential maintainers beyond the spec maintainers.  

Q: Can additional code/tools be added to the proposed tools repos beyond what is listed above?
A: Yes.  If there is other code or functionality that a contributor believes would be relevant for runtime-related or image-related tools, it would be great if it is contributed.

Q: Does this change the OCI Charter or Scope Table?
A: No.  Nothing in this proposal is intended to amend the OCI Charter (https://www.opencontainers.org/about/governance) or OCI Scope Table (https://www.opencontainers.org/governance/oci-scope-table).
