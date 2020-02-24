# OCI ORAS Project Proposal #

## Abstract ##

In order to provide OCI end users a method to publish and retrieve any type of content to/from an OCI registry, as well as a reference implementation for the OCI Distribution Specification, the [ORAS project][oras-project] should be moved under the opencontainers GitHub org.

[oras-project]: https://github.com/deislabs/oras

### ORAS Details ###

ORAS is a CLI that can publish arbitrary content to an OCI registry, with special features for setting mediatypes on manifest configs and on content.

Note: the manifest mediatype itself is always `application/vnd.oci.image.manifest.v1+json`.

Example - uploading rockets, a brand new type of package:

```
# Create a thing
printf '🚀' > rocket.txt

# Create a manifest config
printf '{"RocketVersion":"v0.1.0"}' > rocket-config.json

# Upload your thing with a custom mediatype
oras push localhost:5000/mystuff/myrocket:v0.1.0 rocket.txt:text/plain \
  --manifest-config rocket-config.json:application/vnd.acme.rocket.config.v1+json
 ```

See manifest created:

```
$ curl -s -H 'Accept: application/vnd.oci.image.manifest.v1+json' \
    http://localhost:5000/v2/mystuff/myrocket/manifests/v0.1.0 | jq
{
  "schemaVersion": 2,
  "config": {
    "mediaType": "application/vnd.acme.rocket.config.v1+json",
    "digest": "sha256:310175f34d2d4d5cba3418be06ddd1ef948147d729516d78318ec7f5c2d83d49",
    "size": 26
  },
  "layers": [
    {
      "mediaType": "text/plain",
      "digest": "sha256:ebbc0b2870eb323f2b6cffa5c493ceef81ae7eb36afc73d4e0367301631daec5",
      "size": 4,
      "annotations": {
        "org.opencontainers.image.title": "rocket.txt"
      }
    }
  ]
}
```

Get that thing:

```
$ curl -s http://localhost:5000/v2/mystuff/myrocket/blobs/sha256:ebbc0b2870eb323f2b6cffa5c493ceef81ae7eb36afc73d4e0367301631daec5
🚀
```

#### Additional Usage ####

ORAS is built primarily on top of Go packages provided by [containerd][containerd-project], but it also imports packages from the [docker/cli][dockercli-project], which enables "docker-style" auth login:

```
oras login -u username -p password localhost:5000 -c rocket-creds.json
```

There are also public Go packages available to build on top of ORAS. The following is the equivalent of the rocket example with the CLI above, but in Go:

```go
package main

import (
	"context"
	"fmt"

	"github.com/containerd/containerd/remotes/docker"
	"github.com/deislabs/oras/pkg/content"
	"github.com/deislabs/oras/pkg/oras"
	ocispec "github.com/opencontainers/image-spec/specs-go/v1"
)

func main() {
	ctx := context.Background()
	resolver := docker.NewResolver(docker.ResolverOptions{})
	store := content.NewMemoryStore()

	registryRootURL := "localhost:5000"
	registryNamespace := "mystuff/myrocket"

	rocketVersion := "v0.1.0"
	rocketFileName := "rocket.txt"
	rocketMediaType := "text/plain"
	rocketContent := []byte("🚀")
	rocketDescriptor := store.Add(rocketFileName, rocketMediaType, rocketContent)

	rocketConfigMediaType := "application/vnd.acme.rocket.config.v1+json"
	rocketConfigContent := []byte(fmt.Sprintf("{\"RocketVersion\":\"%s\"}", rocketVersion))
	rocketConfigDescriptor := store.Add("", rocketConfigMediaType, rocketConfigContent)

	ref := fmt.Sprintf("%s/%s:%s", registryRootURL, registryNamespace, rocketVersion)
	_, err := oras.Push(ctx, resolver, ref, store, []ocispec.Descriptor{rocketDescriptor},
		oras.WithConfig(rocketConfigDescriptor))
	if err != nil {
		panic(err)
	}

	fmt.Println("Pushed to", ref)
	fmt.Printf("\nTry:\n\ncurl -s -H 'Accept: application/vnd.oci.image.manifest.v1+json' \\\n" +
		"    %s/v2/%s/manifests/%s | jq\n", registryRootURL, registryNamespace, rocketVersion)
}
```

You can see all features in the project [README][oras-readme].

[containerd-project]: https://github.com/containerd/containerd
[dockercli-project]: https://github.com/docker/cli
[oras-readme]: https://github.com/deislabs/oras/blob/master/README.md

## Proposal ##
Change the ownership of the existing ORAS project from deislabs:

  https://github.com/deislabs/oras

And move it inside the `opencontainers` organization:

  https://github.com/opencontainers/oras

The import paths will correspondingly be "github.com/opencontainers/oras" (oras does have some Go API users, but since the project will be renamed -- and GitHub will add a redirect -- there will be no significant downstream impact of the change).

### Initial Maintainers ###
Initial maintainers of the ORAS project would be:

* Josh Dolitsky <josh@bloodorange.io> (@jdolitsky)
* Shiwei Zhang <shizh@microsoft.com> (@shizhMSFT)
* Sajay Antony <sajaya@microsoft.com> (@sajayantony)
* Steve Lasker <steve.lasker@microsoft.com> (@stevelasker)
* Jimmy Zelinskie <jimmyzelinskie@gmail.com> (@jzelinskie)
* Vincent Batts <vbatts@hashbangbash.com> (@vbatts)

### Code of Conduct ###
This project would incorporate (by reference) the OCI [Code of Conduct][code-of-conduct].

[code-of-conduct]: https://github.com/opencontainers/org/blob/master/CODE_OF_CONDUCT.md

### Governance and Releases ###
This project would incorporate the Governance and Releases processes from the [OCI project template][oci-project-template].

It should be noted that since ORAS is not a specification, it is not bound by the ordinary quorum and voting rules for specification release.
As such, new versions will be released as regularly as needed without the need for a quorum vote.

Pull requests will require two (2) reviews (signified by "LGTM") from project maintainers.
Maintainers are not allowed to review a pull request which they authored.

[oci-project-template]: https://github.com/opencontainers/project-template

### Project Communications ###
The proposed project would continue to use existing channels in use by the OCI developer community for communication including:

 * GitHub for issues and pull requests.
 * The [`dev@opencontainers.org`][oci-ml] email list.
 * The weekly OCI developer community conference call.
 * The `#opencontainers` IRC channel on Freenode.
 * The [OCI Slack workspace][oci-slack].
 * The [OCI Matrix Room][oci-matrix].

[oci-ml]: mailto:dev@opencontainers.org
[oci-slack]: https://opencontainers.slack.com/
[oci-matrix]: https://matrix.to/#/#opencontainers:matrix.org

## Frequently Asked Questions (FAQ)
> *Does this proposal change the OCI Charter?*

This proposal does not in any way intend to amend the [OCI Charter][oci-charter].

[oci-charter]: https://github.com/opencontainers/tob/blob/master/CHARTER.md

> *Where does ORAS fit into the OCI suite of projects?*

ORAS is intended to be a *reference implementation of the OCI Distribution Specification*.

As ORAS was designed to handle any type of content, it will serve to exercise the spec
to make it more independent of details that may have leaked in from image-spec or Docker.

> *Why bless ORAS over other alternative tools?*

ORAS has already been used successfully in the wild as a building block for 
publishing custom content to an OCI registry.

The following projects are already successfully using ORAS to work with custom artifacts:

- [Helm][helm-usage]
- [Conftest][conftest-usage]
- [Singularity][singularity-usage]

[helm-usage]: https://github.com/helm/helm/search?q=oras
[conftest-usage]: https://github.com/instrumenta/conftest/search?q=oras
[singularity-usage]: https://github.com/sylabs/singularity/search?q=oras

> *How do we avoid the runc issue with implementation-specific quirks becoming a de-facto standard?*

When developing new features in ORAS (which are within the scope of the OCI Distribution Specification),
a strong effort will be made to include those features in the upstream specification.

> *Who are the other target users of ORAS?*

Users seeking a common way to store different types of content (not just container runtime images),
using the OCI Distribution Spec as the baseline API.

> *How do you pronounce ORAS?*

The name ORAS is actually an acronym for "OCI Registry As Storage",
but when speaking of it, you can say "or-ahs".
