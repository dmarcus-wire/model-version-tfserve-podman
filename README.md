# Project Goal:

Build a basic Tensorflow Pipeline that automatically executes tasks from ingestion to serving. Scenario, uses sythentically generated patient data (Heart Rate, Temperature, Respiratory Rate, White Blood Cell Count) that has been labelled with a 1 (Septic) or 0 (Not-Septic).
    
All training steps are executed through the train_pipeline_notebook.ipynb. 
All post-training steps are executed through the serve_notebook.ipynb. 

[x] pipeline automation using TensorFlow Extended (TFX)
[x] code development with Jupyter Notebook from Open Data Hub on OpenShift on AWS
[x] source code management integration with GitHub
[x] data ingestion with TFX "ExampleGen"
[x] model training with TFX "Trainer" 
[x] model deployment with TFX "Pusher"
[x] model serving with with TFX "TensorFlow Serving" 
[x] model versioning with pipeline and TensorFlow Serving

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
