# Intro
This repo is created to log the learning of Kubernetes deployments on local controlled environment using Minikube & Docker Desktop.

# Preview
<!-- ToDo - Add Preview Image here. -->
![Preview Image](https://raw.githubusercontent.com/AashishSinghal/kube-mern/main/preview.png)

# Commands that are used to setup and run this project.

## Prerquisites

* Docker desktop application.

**Note** - You can download the docker desktop application [here](https://www.docker.com/products/docker-desktop/).

## Installation

First we install the `kubectl` package by Kubernetes to get access to the Kubernetes cli which we can use to manage the deployments.
Use the below commands to install the `kubectl`.

For MacOS
```
brew install kubectl
```
For Windows
```
curl.exe -LO "https://dl.k8s.io/release/v1.26.0/bin/windows/amd64/kubectl.exe"
```
you can refer to the `kubectl` installation guide [here](https://kubernetes.io/docs/tasks/tools/).


Now we install `minikube` which will give us an local environment to deploy our app and db.

```
brew install minikube
```

## Setup 

we will create the following yaml files - 
* `secrets.yaml`
* `mongo-config.yaml`
* `mongo-app.yaml`
* `web-app.yaml`

we are using [`mongo`](https://hub.docker.com/_/mongo) as the DB image & [`mongo-express`](https://hub.docker.com/_/mongo-express) as our application for this demo.


## Deployment

Start the minikube environment -
```
minikube start
```

Apply the configs & deploy - 
```
kubectl get pod
kubectl apply -f mongo-config.yaml
kubectl apply -f secret.yaml
kubectl apply -f mongo-app.yaml
kubectl apply -f web-app.yaml
kubectl get pod
```

Get the details of the pods, services, secrets, ip & node - 
```
kubectl get configmap
kubectl get secret
kubectl get svc
minikube ip
kubectl get node -o wide
```

the `minikube ip` command will only give you the IP, for accessing the application we have to start the service -

```
minikube service webapp-service
```

we have successfully deployed the application.

After we are done we can delete the deployements using the following commands.

```
kubectl delete deployment --all
```
```
kubectl delete secret --all
```

Thank You.
