# OCI Image Format Spec Proposal

The TOB will create a new OCI project tasked with creating a software shipping container image format spec (OCI Image Format) with security and naming as components. In addition the OCI TOB will establish a new set of maintainers for this new project with people who have expertise in image formats and package management.

## Initial Recommendation

This new OCI project would be recommended to start with the Docker v2.2 specification, improve any remaining technical concerns, and create an OCI project and maintainers to develop and shepherd an OCI Image Fromat Spec. By starting from this project we intend to standardize and improve the understood properties of a container image format. This new project will have the objectives of:

* A serialized image format (base layer)
* A process of hashing the image format for integrity and content-addressing (base layer)
* Signatures that are based on signing image content address (optional layer)
* Naming that is federated based on DNS and can be delegated (optional layer)

Initial Maintainers: to be brainstormed on a separate thread.

## Cooperation with OCI Runtime Project

The OCI Runtime Specs project is working diligently to create a specification for the lifecycle of a running container. The OCI Image Format Spec project should work with the OCI Runtime Spec project so that the image can support the UX that users have come to expect from container engines like Docker and rkt: primarily, the ability to run an image with no additional arguments:

* docker run example.com/org/app:v1.0.0
* rkt run example.com/org/app,version=v1.0.0

This implies that the OCI Image Format contain sufficient information to launch the application on the target platform e.g. command, arguments, environment variables, etc.

## FAQ

**Q: Why doesn't this project mention distribution?**

A: Distribution, for example using HTTP as both Docker v2.2 and AppC do today, is currently out of scope on the [OCI Scope Table](https://www.opencontainers.org/governance/oci-scope-table). There has been [some discussion on the TOB mailing list]( https://groups.google.com/a/opencontainers.org/d/msg/tob/A3JnmI-D-6Y/tLuptPDHAgAJ) to make distribution an optional layer but this topic is a work in progress.

**Q: Why a new project?**

A: The first OCI spec centered around defining the run side of a container. This is generally seen to be an orthogonal concern to the shipping container component. As practical examples of this separation you see many organizations separating these concerns into different teams and organizations: the Docker Distribution project and the Docker containerd project; Amazon ECS and Amazon EC2 Container Registry, etc.

**Q: Why start this work now?**

A: We are seeing many independent implementations of container image handling including build systems, registries, and image analysis tools. As an organization we would like to encourage this growth and bring people together to ensure a technically correct and open specification continues to evolve reflecting the OCI values.

**Q: What happens to AppC or Docker Image Formats?**

A: Existing formats can continue to be a proving ground for technologies, as needed. The OCI Image Format project should strive to provide a dependable open specification that can be shared between different tools and be evolved for years or decades of compatibility; as the deb and rpm format have.

## Proposed Roadmap

* March ?? v0.0.0
  * Import Docker v2.2 format
* April ??? v0.1.0
  * Spec factored for top to bottom reading with three audiences in-mind:
    * Build system creators
    * Image registry creators
    * Container engine creators
* May ??? v0.2.0
  * Release version of spec with improvements from two independent experimental implementations from OCI members e.g. Amazon Container Registry and rkt
* June ??? v1.0.0
  * Release initial version of spec with two independent non-experimental implementations from OCI members

