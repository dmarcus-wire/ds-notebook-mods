# Containerfile
A Containerfile contains instructions that specify how to construct a container image.

Containerfiles are another option for creating container images that addresses these limitations. Containerfiles are easy to share, version control, reuse, and extend.
Containerfiles also make it easy to extend one image, called a child image, from another image, called a parent image. A child image incorporates everything in the parent image and all changes and additions made to create it.
A file referred to as a Containerfile can be a file named either Containerfile or Dockerfile. Both share the same syntax. Containerfile is the default name used by OCI compliant tools.

## What do you need?
Podman or Buildah

## What are the steps?
1. Create a working directory.
2. Specify the build instructions in a Containerfile file.
3. Build the image with the podman build command.

Podman creates many anonymous intermediate images during the build process.
They are not be listed unless -a is used. Use the --layers=false option of the
build subcommand to instruct Podman to delete intermediate images.

## Containerfile

```commandline
# build the image with podman or buildah
podman build -t ubi8-python38-cv:0.2 . --layers=false
buildah bud -f Containerfile . -t b.uildah-bud

# list the images and check size
podman images

# tag the image
podman tag localhost/ubi8-python38-cv:0.2 quay.io/dmarcus/machine-learning/ubi8-py38-cv:0.2

# login to quay
podman login quay.io -u <username> -p <password>

# push the container image
podman push <image_id> quay.io/organization/repository
```