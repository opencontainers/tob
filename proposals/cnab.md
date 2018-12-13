# Abstract

Cloud Native Application Bundles (CNAB) are a package format specification that describes a technology for bundling, installing, and managing distributed applications that are, by design, cloud agnostic.

## Proposal

That the Cloud Native Application Bundles (CNAB) specification be hosted and governed as a part of the Open Container Initiative (OCI). Addtionally we would move [https://github.com/deislabs/cnab-spec/](https://github.com/deislabs/cnab-spec/) to a new [cnab-spec project](https://github.com/opencontainers/cnab-spec).

### Background 

The goal of Cloud Native Application Bundles (CNAB) is to provide a packaging standard that is flexible enough to accommodate the services and runtimes of today and anticipate those of tomorrow. 

The introduction of CNAB facilitates standardization around packaging and distribution as a foundation, while creating an opporunity for an ecosystem of opinionated tooling to exist. For example, in existing prototypes an application can be built with Docker-App and deployed using Duffle.

Cloud Native Application Bundles (CNAB) is a standard packaging format for multi-component distributed applications. It allows packages to target different runtimes and architectures. It empowers application distributors to package applications for deployment on a wide variety of cloud platforms, cloud providers, and cloud services. It also provides the capabilities necessary for delivering multi-container applications in disconnected environments.

CNAB is not a platform-specific tool. While it uses containers for encapsulating installation logic, it remains un-opinionated about what cloud environment it runs in. CNAB developers can bundle applications targeting environments spanning IaaS (like OpenStack or Azure), container orchestrators (like Kubernetes or Nomad), container runtimes (like local Docker or ACI), and cloud platform services (like object storage or Database as a Service). CNAB can also be used for packaging other distributed applications, such as IoT or edge computing.

## Initial Maintainers

* Matt Butcher <matt.butcher@microsoft.com> (@technosophos)
* Lachlan Evenson <lachlan.evenson@microsoft.com> (@lachie83)
* Gareth Rushgrove <gareth.rushgrove@docker.com> (@garethr)

Additional Maintainers to consider:

* Chris Crone (Docker)

## Code of Conduct

This project would incorporate (by reference) the OCI Code of Conduct ([https://github.com/opencontainers/tob/blob/master/code-of-conduct.md](https://github.com/opencontainers/tob/blob/master/code-of-conduct.md)).

## Governance and Releases

This project would incorporate the Governance and Releases processes from the OCI project template: [https://github.com/opencontainers/project-template](https://github.com/opencontainers/project-template).

## Project Communications

Both of the proposed projects would continue to use existing channels in use by the OCI developer community for communication including:

* GitHub for issues and pull requests
* The dev@opencontainers.org email list
* The monthly OCI developer community conference call
* The #OpenContainers freenode IRC channel

## Versioning / Roadmap

The CNAB spec is currently Cloud Native Application Bundle Core 1.0.0 (CNAB1) Working Draft, November 2018.

## Frequently Asked Questions (FAQ)

**Q: What are the tangible day to day problems that I have that CNAB helps me solve?**

A: CNAB solves two major use cases. First, it provides a standard package format for delivering a distributed application. From marketplaces and app stores to CI/CD pipelines, packaged applications streamline the tooling and user experience for installing an application.

Because CNAB supports a robust import and export model, the standard also addresses a number of difficult distribution situations such as air gapped networks, constrained network environments, "submarine" scenarios, and IoT distribution. CNAB supports a signed, verified sneaker-net scenario for distributed, heterogenous applications.  This means that it gives you the ability to take a distributed application deployment, export it to a file system that can be carried over to an air-gapped or otherwise disconnected environment, and then import it into a duffle or other CNAB-compliant runtime there and deployed without having a connection to the internet.

**Q: How is this different from provisioning tools such as Chef, Puppet, Ansible, or Terraform?**

CNAB provides the packaging and distribution layer, but not the provisioning logic. Consequently, CNAB can make use of these tools as internal components of a package. For example, a CNAB bundle can execute a Terraform plan or an Ansible playbook as a step in setting up a cloud native application. CNAB, then, is a complimentary technology to existing provisioning and orchestration tools.

**Q: How can you hope to achieve a consistent bundle experience across all of these heterogeneous runtimes?**
 
We cannot hope to “fix” poor experiences in a particular installation technology; but we can hope to add the network effect of a common and widespread tool ecosystem to them, and we can hope to add features such as digital signing and verification to them that they may not possess now.  
 
The most difficult area to improve across all these heterogeneous runtimes is not installation or uninstallation, but rather the upgrade, introspection, and debugging of the overall experience. Here we intend to focus on providing installation images that export or can attach debuggers to enable the clearest amount of transparency into each installation technology.  
 
This area is a real challenge, but one that we think we can meet with CNAB because of the vast, deep knowledge of specific operational stacks that the community possesses.   

**Doesn't this add more complexity to an already complex cloud native ecosystem?**

This introduces another step in the typical build pipeline. However, that cost is small compared to the improved end user experience. For an end user, CNAB becomes common while the precise tools inside of a CNAB are unimportant. The user needn't know how terraform works in order to install a CNAB that uses terraform, nor does the user need to manage the tooling and dependencies used by the bundle. All of this is encapsulated by the bundle producer.

As a result, the user can rely upon tooling to manage complexity, while the package produces can pick and choose from their preferred provisioning tools.

## References

* Specification: https://github.com/deislabs/cnab-spec
* Website: https://cnab.io
* Sample Bundles: https://github.com/deislabs/bundles
* Reference CNAB implementation: https://github.com/deislabs/duffle
* Docker-app CNAB implementation: https://github.com/docker/app

