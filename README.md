# k8s

<img src="https://github.com/Midhilesh29/k8s/blob/master/gke.png" width="1000">

This repository provides the code to deploy Post Quantized mobilnetv2 model on Google Kubernetes Engine.

## Code Architecture

1. flask
    1. Dockerfile [Dockerfile the dependencies to run gunicorn+flask based application server for predicting the POST request image]
    2. deploy.py [Python code for running guincorn]
    3. FlaskApp.py [Python code for preprocessing the input image and predicting it with post quantized mobilenetv2 model]
    4. MobileNetV2Quantized.pth [Is the torchscript based serialized post quantized mobilenetv2 model]
2. deployment.yaml [YAML file to create pods using replicaset]
3. service.yaml [YAML file to create a service (type loadbalancer) for external word to reach this application service]
```
gcloud container clusters create cluster-1 --zone us-central1-a

gcloud container clusters get-credentials cluster-1 --zone us-central1-a

kubectl get nodes

kubectl apply -f deployment.yaml

kubectl apply -f service.yaml

```

**Note** 
1. Selector for service should be the label app given for pods
2. name in deployment, service are basically to identify it.
