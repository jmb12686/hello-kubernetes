# Hello Kubernetes

Simple get started projects for k8s

## Prerequisites

For this project, we will be using Kubernetes on Docker Desktop, as such the cluster and kube config will be named `docker-desktop`

## Deploy Kubernetes Dashboard

Run the following commands:

```ps
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v1.10.1/src/deploy/recommended/kubernetes-dashboard.yaml

kubectl proxy

$TOKEN=((kubectl -n kube-system describe secret default | Select-String "token:") -split " +")[1]

kubectl config set-credentials docker-desktop --token="${TOKEN}"
```

Then browse to: http://localhost:8001/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy/#!/overview?namespace=default

Select the config auth option, and select the kubernetes conf file under `C:\Users\USERPROFILE\.kube\config`

## Deploy hello-kubernetes

```ps
kubectl apply -f .\hello-kubernetes.yml
```

Browse to http://localhost

## Deploy go-loadtest-api

```ps
kubectl apply -f .\go-loadtest-api.yml
```

Browse to http://localhost:8000/hello and http://localhost:8000/loadtest/iterations/100000
