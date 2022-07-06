# Tensorflow Serving

```
# search for the tensorflow serving image
podman search --format "table {{.Index}} {{.Name}}" docker.io/tensorflow/serving

# pull the image
podman pull docker.io/tensorflow/serving:latest

# list the image
podman images

# test the container image with a model
podman run --rm -d --name tfserving_base tensorflow/serving

# set environment variable for the latest pipeline run for trained model directory
LATEST=`ls -dt serving/*/ | head -1`
echo $LATEST

# copy the models directory contents to the container
podman cp $LATEST/. tfserving_base:/models/sepsis
```