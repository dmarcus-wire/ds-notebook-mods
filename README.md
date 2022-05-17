# ds-notebook-mods
Goals of this repo are to explain updating 1) system packages 2) python packages at scale using OCI tools (Skopeo, Podman, Buildah).

## Goals
1. Start from UBI8 
2. Add system level packages 
3. Commit and Push Image
4. Add jupyter notebook from ODH
5. Commit and Push Image
6. Make available from Jupyter spawner

## Approaches
1. Editing existing container image
2. Build from Containerfile
3. Source-to-image