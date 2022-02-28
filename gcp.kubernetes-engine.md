---
id: 9ucimnicgxcwumqvpfidc9j
title: Kubernetes Engine
desc: ''
updated: 1646050790331
created: 1646050348013
---

> [Google Kubernetes Engine](https://cloud.google.com/kubernetes-engine/) (GKE) provides a managed environment for deploying, managing, and scaling your containerized applications using Google infrastructure. The Kubernetes Engine environment consists of multiple machines (specifically [[Compute Engine|gcp.compute-engine]] instances) grouped to form a container cluster. In this lab, you get hands-on practice with container creation and application deployment with GKE.

Kubernetes provides the mechanisms through which you interact with your container cluster. You use Kubernetes commands and resources to deploy and manage your applications, perform administrative tasks, set policies, and monitor the health of your deployed workloads.

# Kubernetes Objects
### Deployment
Used to deploy stateless applications (ones that do not save client data between sessions) e.g. web servers.

[Docs](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)

### Service
Defines rules and load balances for accessing the application from the internet.

[Docs](https://kubernetes.io/docs/concepts/services-networking/service/)