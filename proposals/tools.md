# OCI Runtime-Tools and Image-Tools Project Proposals

## Abstract
The below proposal contemplates creation of two tools projects (runtime-tools and image-tools.)
These would be associated with the OCI specification projects (runtime-spec and image-spec) and serve as repositories for testing  tools. 

## Background
Testing tools have been organically developed by the OCI developer community.
These include:
* Runtime-spec test code in a OCITools repository
* Image-spec test code in the image-spec repository
On Wednesday, June 8th, 2016, the OCI developer community discussed potential location(s) for tools associated with specs.  

Pro and con arguments were raised for both:
* A. Having test tools in separate repositories for specs (while possibly keeping schemas with the specs)
* B. Keeping test tools in the same repository as a spec (with independent versioning of files)

The below proposal describes option A.

## Proposal
Create runtime-tools and image-tools repositories under the http://github.com/OpenContainers organization.

### Initial Maintainers
Initial maintainers of the runtime-tools project shall be:
* Maintainers of the runtime-spec project
* The four most active contributors (by commit count) to the OCITools project 

Initial maintainers of the image-tools project shall be:
* Maintainers of the image-spec project

### Code of Conduct
Both of the proposed projects would incorporate (by reference) the OCI Code of Conduct from the 

### Project Communications
Both of the proposed projects would continue to use existing channels in use by the OCI developer community for communication including:
* GitHub for issues and pull requests
* The dev@opencontainers.org email list
* The weekly OCI developer community conference call
* The #OpenContainers IRC channel

### Versioning / Roadmap
Released version numbers of the runtime-tools and image-tools projects should roughly align with released verions of the associated specs projects.

It is expected that releases of the tools projects will follow releases of the specs projects by anywhere from a few days to a few months.
