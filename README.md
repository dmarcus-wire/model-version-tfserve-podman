# model-version-tfserve-podman
Model versioning with TensorFlow Serving on Podman

Getting started using TensorFlow Serving is with Podman on RHEL.

```
# confirm current root directory setting for the containers
podman info | grep -i root

# clone in the github project and move into the directory
https://github.com/dmarcus-wire/model-version-tfserve-podman.git && cd model-version-tfserve-podman

# search for the tensorflow serving image on docker.io
podman search --format "table {{.Index}} {{.Name}}" docker.io/tensorflow/serving

# pull the image
podman pull docker.io/tensorflow/serving:latest

# test the container image with a model
podman run --rm -d --name tfserving_base tensorflow/serving

# copy the models directory contents to the container
podman cp models/. tfserving_base:/models
```
