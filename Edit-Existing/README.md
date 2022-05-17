# Modifying Existing Containers

One method of creating container images previously discussed requires that you create a container, 
modify it to meet the requirements of the application to run in it, and then commit the changes to an image. 
This option, although straightforward, is only suitable for using or testing very specific changes. 
It does not follow best software practices, like maintainability, automation of building, and repeatability.

## What do you need? 
Podman or Buildah

## What are the steps?
1. run the container locally
2. update the packages
3. save and commit the container image
4. push the container image


### Modifying Existing Containers
```
# Install UBI8 Python image from trusted source
# Login Red Hat Registry
podman login -u <username> -p <password> registry.access.redhat.com

# Search for Python UBI Image
podman search registry.access.redhat.com/python

# Pull the Python UBI Image
podman pull registry.access.redhat.com/ubi8/python-38 

# List the image
podman images

# Run the image with a Bash terminal inside the container in the background
podman run -d --name edit-existing registry.access.redhat.com/ubi8/python-38:latest
podman exec -it python-container /bin/bash

# Check the current dir and user id
pwd #/opt/app-root/src
id #uid=1001(default) gid=0(root) groups=0(root)
pip --version # pip 21.2.3 from /opt/app-root/lib64/python3.8/site-packages/pip (python 3.8)
which python #/opt/app-root/bin/python

# install dlib
pip install dlib opencv-python opencv-contrib-python scipy

# commit the changes
podman commit python-container ub8-python38-computer-vision

# check images
podman images

# run new computer-vision image
podman run --name computer-vision -it localhost/ubi8-python38-computer-vision:latest /bin/bash

# list packages
pip list

# list the changes to the image
podman diff localhost/ubi8-python38-computer-vision:latest

# tag the image
podman tag localhost/ubi8-python38-computer-vision:latest quay.io/dmarcus/machine-leanring/ubi8-py38-cv:0.1

# Uninstall
podman ps -a
podman rm -a
podman images
podman rmi -a
```
