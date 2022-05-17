# Source-to-Image (S2I) 
The Source-to-Image (S2I) process provides an alternative to Containerfiles. S2I implements
a standardized container image build process for common technologies from application
source code. This allows developers to focus on application development and not Containerfile
development.

## What do you need?
Install S2i tool from https://github.com/openshift/source-to-image

## What are the Steps?

1. Start a container from a base container image called the builder image. 
2. This image includes a programming language runtime and essential development tools, such as compilers and package managers.
3. Fetch the application source code, usually from a Git server, and send it to the container.
4. Build the application binary files inside the container.
5. Save the container, after some clean up, as a new container image, which includes the programming language runtime and the application binaries.