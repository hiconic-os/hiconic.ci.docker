# Hiconic CI/CD Docker images

## Content

Contains:
* **Dockerfile** for an image to run `Hiconic` pipelines (with `devrock-sdk`)
* **Github action** to build and push a fresh image to Github's `Container Registry`

There are actually two Docker🐋 images:
* **base**: based on `Ubuntu`, with `Git` and `Java` installed
* **devrock-sdk**: based on the **base** one, with `devrock-sdk`

(This is an optimization to build an image with the latest `devrock-sdk` faster.)

## How to build

To build a new image trigger the right `Github action` manually:
* **Build Image - Base**
* **Build Image - Devrock SDK**

The images will be published using the tags

```
ghcr.io/hiconic-os/ci-base/${branch}:latest
ghcr.io/hiconic-os/ci-devrock-sdk/${branch}:latest
```

where `branch` is the name of the branch for which the action was triggered.

## How to use

To pull the Devrock SDK image from the `main` branch use:
```
docker pull ghcr.io/hiconic-os/ci-devrock-sdk/main:latest
```

To use it from a workflow yml use:
```
container: ghcr.io/hiconic-os/ci-devrock-sdk/main:latest
```
