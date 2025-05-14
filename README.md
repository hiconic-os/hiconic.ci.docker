# Hiconic Docker Images (Runtime and CI/CD)

## Content

Contains:
* **Dockerfile** for a base image to run `Hiconic` **applications**
* **Dockerfile** for an image to run `Hiconic` **CI pipelines** (with `hiconic-sdk`)
* **GitHub actions** to build and push a fresh image to GitHub's `Container Registry`

As for the `hiconic-sdk` (CI) image, there  There are actually two Docker🐋 images:
* **ci-base**: based on `Ubuntu`, with `Git` and `Java` installed
* **ci-hiconic-sdk**: based on the **ci-base** one, with `hiconic-sdk`

(This is an optimization to build an image with the latest `hiconic-sdk` faster.)

## How to build

To build a new image trigger the right `GitHub action` manually:
* **Build Image - Runtime**
* **Build Image - CI Base**
* **Build Image - CI Hiconic SDK**

The images will be published using the tags

```
ghcr.io/hiconic-os/runtime-base:latest
ghcr.io/hiconic-os/ci-base/${branch}:latest
ghcr.io/hiconic-os/ci-hiconic-sdk/${branch}:latest
```

where `branch` is the name of the branch for which the action was triggered.

## How to use

To pull the Hiconic SDK image from the `main` branch use:
```
docker pull ghcr.io/hiconic-os/ci-hiconic-sdk/main:latest
```

To use it from a workflow YAML use:
```
container: ghcr.io/hiconic-os/ci-hiconic-sdk/main:latest
```

## Older versions

Older versions of the images are published using the following tag schemas:

```
ghcr.io/hiconic-os/runtime-base:${runNumber}
ghcr.io/hiconic-os/ci-base-snapshot/${branch}:${runNumber}
ghcr.io/hiconic-os/ci-hiconic-sdk-snapshot/${branch}:${runNumber}
```

To set an older version as the latest, run:
* **Restore Image - CI Hiconic SDK**

You need to enter the version (run number) as input. Note that the run number is visible in the [workflow runs list](https://github.com/hiconic-os/hiconic.ci.docker/actions), e.g.
> Build Image - CI Hiconic SDK #420: Manually run by codejunkie

Snapshots for `main` branch:
* [Base](https://github.com/hiconic-os/hiconic.ci.docker/pkgs/container/ci-base-snapshot%2Fmain)
* [Hiconic SDK](https://github.com/hiconic-os/hiconic.ci.docker/pkgs/container/ci-hiconic-sdk-snapshot%2Fmain)