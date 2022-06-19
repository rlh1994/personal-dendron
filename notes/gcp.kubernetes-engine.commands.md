---
id: n0yrw4vqkdtuds5p37lngb4
title: Commands
desc: ''
updated: 1646050941566
created: 1646050594102
---

## gcloud

#### Create New Container
```bash
gcloud container clusters create [CLUSTER-NAME]
```

#### Authenticate Cluster
```bash
gcloud container clusters get-credentials [CLUSTER-NAME]
```

#### Delete Cluster
```bash
gcloud container clusters delete [CLUSTER-NAME]
```

## Kubernetes
#### New Deployment
[Docs](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#create)
```bash
kubectl create deployment hello-server --image=gcr.io/google-samples/hello-app:1.0
```
#### New Service
```bash
kubectl expose deployment hello-server --type=LoadBalancer --port 8080
```

#### Inspect Service
```bash
kubectl get service
```