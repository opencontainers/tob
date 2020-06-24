# OCI umoci Project Proposal #

## Abstract ##
The need for a "works out of the box" image tool that is supported by OCI has been clear for several years.
umoci was initially developed to fulfil this requirement, and after several years of development and wide-spread production usage, we feel it is time to include it within the OCI.
The following proposal outlines how this would be achieved.

## Background ##
To quote the description of umoci from [the project website][umoci]:

> umoci is a free software tool for manipulating and interacting with container
> images in the standardised Open Container Initiative’s image format. It
> provides one of the most flexible image management toolsets, requiring
> neither a daemon nor any particular filesystem setup. It is already used in a
> variety of different projects and by several companies.

umoci is primarily used as a command-line tool, and can be used to perform fundamental operations on an OCI container image.
An example session looks like

```ShellSession
## Unpack an existing image (image directory "opensuse" with tag "leap") into
## an OCI runtime-spec bundle in the directory "bundle".
##
% umoci unpack --image opensuse:leap bundle

## Start the container in "bundle" using the default generated configuration
## and make some changes to the container filesystem. Note that is not
## necessary to use containers in order to change the filesystem, umoci doesn't
## care how you modify the rootfs.
##
## Note that only modifications in "bundle/rootfs" will have any effect on
## "umoci repack". Of particular note is that you can only change the image
## configuration through "umoci config" and not by modifying
## "bundle/config.json".
##
% runc run -b bundle ctr
ctr# zypper in -y foobarbaz
ctr# exit
% echo foo > bundle/rootfs/README

## Based on the changes made above, build a new layer on top of the original
## image and replace "opensuse:leap" with the new image. If you wish to create
## a new image tag and leave the old one alone, pass a different value to
## --image here (though it must be in the same image directory "opensuse").
##
% umoci repack --image opensuse:new-leap bundle

## Modify the configuration of the image to specify a new author.
##
% umoci config --image opensuse:leap \
>              --author="Aleksa Sarai <cyphar@cyphar.com>" \
>              --config.workingdir="/var/www"

## Garbage-collect any unreferenced blobs in the image (directory "opensuse").
## umoci does not do this automatically, so users should do this after
## completing all operations on an image.
##
$ umoci gc --layout opensuse
```

umoci has a fairly minimal feature set, and was intended from the outset to implement all of the key features which are needed from a reference implementation of the OCI Image Specifications.
The help page for the latest version of `umoci` (`0.4.5` at the time of writing) is provided below:

```
NAME:
   umoci - umoci modifies Open Container images

USAGE:
   umoci [global options] command [command options] [arguments...]

VERSION:
   0.4.5

AUTHOR:
   Aleksa Sarai <asarai@suse.com>

COMMANDS:
   raw      advanced internal image tooling
   help, h  Shows a list of commands or help for one command

   image:
     config      modifies the image configuration of an OCI image
     unpack      unpacks a reference into an OCI runtime bundle
     repack      repacks an OCI runtime bundle into a reference
     new         creates a blank tagged OCI image
     tag         creates a new tag in an OCI image
     remove, rm  removes a tag from an OCI image
     stat        displays status information of an image manifest
     insert      insert content into an OCI image

   layout:
     gc        garbage-collects an OCI image's blobs
     init      create a new OCI layout
     list, ls  lists the set of tags in an OCI layout

GLOBAL OPTIONS:
   --verbose      alias for --log=info
   --log value    set the log level (debug, info, [warn], error, fatal) (default: "warn")
   --help, -h     show help
   --version, -v  print the version
```

For a more detailed explanation of umoci, see the [project website's guide][umoci-guide].

[umoci]: https://umo.ci/
[umoci-guide]: https://umo.ci/quick-start/

## Proposal ##
Change the ownership of the existing umoci project from openSUSE:

  https://github.com/openSUSE/umoci

And move it inside the `opencontainers` organisation:

  https://github.com/opencontainers/umoci

The import paths will correspondingly be "github.com/opencontainers/umoci" (umoci does have some Go API users, but since the project will be renamed -- and GitHub will add a redirect -- there will be no significant downstream impact of the change).
In the future we may opt to use vanity imports (such as "umo.ci/cmd/umoci").

The project's domain "umo.ci" will also be transferred to the Linux Foundation so that it can be managed by someone other than the maintainers (though maintainers must maintain the necessary administrative access to maintain the website).

### Initial Maintainers ###
Initial maintainers of the umoci project would be:

* Aleksa Sarai <cyphar@cyphar.com> (@cyphar)
* Tycho Andersen <tycho@tycho.ws> (@tych0)
* Vincent Batts <vbatts@hashbangbash.com> (@vbatts)

### Code of Conduct ###
This project would incorporate (by reference) the OCI [Code of Conduct][code-of-conduct].

[code-of-conduct]: https://github.com/opencontainers/org/blob/master/CODE_OF_CONDUCT.md

### Governance and Releases ###
This project would initially incorporate the Governance and Release processes from [the OCI project template][oci-template], with two modifications:

 * Self-LGTMs are permitted.
 * Minor (`1.y`), point (`1.2.z`), and release candidate (`1.2.3~rcN`) releases only require 2 LGTMs.

The motivation for these changes is that the set of maintainers is rather small, so many of the [OCI project template rules][oci-template] will require unanimous votes which is an unfair burden on merging code changes.

[oci-template]: https://github.com/opencontainers/project-template

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

### Roadmap ###
umoci still has a fairly ambitious scope of work (much of it outside the scope of the OCI Image Specification), and this work would continue under OCI.
Examples of such work include:

 * Security hardening by porting umoci to [libpathrs][libpathrs].
 * Re-thinking the method by which images are referenced in the command-line.
 * Expanded support for configuring descriptor annotations in arbitrarily-structured OCI metadata trees.
 * Committing to a stable Go API and releasing a version 1.0 of the project.
 * Experimental design work for [a new OCI Image Specification layer format (code-named "OCIv2")][ociv2].
 * Hookable execution to allow for custom "storage drivers" to be defined by users (to avoid the maintenance overhead of supporting such drivers within umoci).
   This would effectively allow for higher-level tools to implement both image-build caching (by skipping the extraction of layers which are already available) and overlay filesystem support (by injecting `mount(8)` operations between layer extractions).

[libpathrs]: https://github.com/openSUSE/libpathrs
[ociv2]: https://hackmd.io/@cyphar/ociv2-brainstorm

## Frequently Asked Questions (FAQ)
> *Does this proposal change the OCI Charter?*

This proposal does not intend to amend the [OCI Charter][oci-charter].

[oci-charter]: https://github.com/opencontainers/tob/blob/master/CHARTER.md

> *Where does umoci fit into the OCI suite of projects?*

umoci is intended to be a *reference implementation of the OCI Image Specification* as a "works out of the box" image manipulation tool, which provides a minimally abstracted set of operations to avoid users having to implement the OCI Image Specification themselves.
It is intended to fill a similar role to runc within the OCI Runtime Specification -- that is, being a "boring container infrastructure tool" which larger systems can leverage.

Note that this proposal should not be interpreted as being intended to make the OCI prescribe the use of umoci for existing or new projects to use instead of their own OCI Image Specification implementation.
This proposal for umoci's inclusion is intended to make it easier for users who do not wish to implement the OCI Image Specification themselves to have a basic building block they can use for whatever system they are developing.
While umoci is usable on its own, it is expected that the vast majority of umoci's users will be consuming it as part of a larger build system which uses umoci internally to abstract away the specifics of the OCI Image Specification.

> *What about image-tools?*

The original intention of umoci was to be a wrapper around the OCI image-tools and slowly upstream the work.
Unfortunately, in the past 4 years, the image-tools project has not developed at a consistent pace -- and umoci works today and is fairly widely used.
It is far more important that the OCI provide a solid "works out of the box" image manipulation tool, and umoci is (in our view) the best candidate for this role.

In a future proposal, we may decide to sub-tree merge the OCI image-tools project into umoci (and archive the original project) in order to maintain the legacy of the work done by previous contributors and maintainers.
Alternatively we may decide to split out the validation code from the OCI image-tools project and place it inside an OCI conformance project.
However, we believe that these decisions should be considered a separate topic to the question of umoci's inclusion in the OCI.

> *Why bless umoci over other alternative tools?*

umoci is the only OCI image manipulation tool which was designed to be usable as a component to build other image-building tools.
This has proven to be a practical benefit, with several tools ([KIWI][kiwi], [stacker][stacker], and several others) being built on top of umoci.
In addition, umoci has been used by the [LXC project][lxc-oci] to support OCI-based images from *outside* the OCI ecosystem, something that was only reasonable because of umoci's unopinionated stance on images.
umoci has seen production usage for several years as part of the [Open Build Project][obs]'s build system, building container images using [kiwi][kiwi].

[kiwi]: https://osinside.github.io/kiwi/building/build_docker_container.html
[stacker]: https://github.com/anuvu/stacker
[lxc-oci]: https://github.com/lxc/lxc/blob/lxc-4.0.2/templates/lxc-oci.in
[obs]: https://openbuildservice.org/

> *How do we avoid the runc issue with implementation-specific quirks becoming a de-facto standard?*

When developing new features in umoci (which are within the scope of the OCI Image Specification), a strong effort will be made to include those features in the upstream specification.
In addition, any new features that are in the scope of the OCI Image Specification will be marked as strictly experimental and unsupported, to ensure that users do not depend on their stability until the relevant feature (or an equivalent feature) is included in the OCI Image Specification.
The scope of the OCI Image Specification is thankfully smaller than the OCI Runtime Specification, so this should not be as much of a concern as with runc.
However, the maintainers will be mindful of the issue and will make use of their experiences working on runc and the OCI Runtime Specification to avoid this situation occurring with umoci and the OCI Image Specification.

For the avoidance of doubt, any such features will require explcit user action to enable such that the user is made clearly aware that they are using an unsupported feature.
Examples include requiring the user to:

 * Specify a scary-sounding build tag during compilation to enable the feature (`go build -tag 'EXCEPTIONALLY-UNSTABLE--featureXYZ'`); or
 * Pass a scary-sounding flag (such as `--seriously-do-not-depend-on-this-feature`); or
 * Use a scary function name (such as `VeryUnstableFeature_FuncXyz`).

And all of the above requirements will be documented with an explicit warning that explains to the user why this policy is important.

> *Who are the other target users of umoci?*

End-users who want a simple tool to deal with OCI images, and developers of image-building tools that want a tried and tested implementation of the OCI image format.
