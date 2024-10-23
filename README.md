# Kubernetes Web Application Deployment

This repository contains a complete setup for deploying a web application with a MySQL backend using Kubernetes. It includes configurations for pods, ReplicaSets, deployments, and services, enabling efficient management and scaling of your application in a Kubernetes environment.

## Features

- **Containerization**: The application is fully containerized using Docker, allowing for consistent deployment across different environments.
- **Scalability**: Using Kubernetes ReplicaSets and Deployments, the application can be easily scaled up or down based on traffic and resource requirements.
- **High Availability**: Multiple replicas of the MySQL database and web application ensure that the application remains available even in the event of pod failures.
- **Service Discovery**: Kubernetes services allow different components of the application to communicate with each other easily, enabling robust microservices architecture.
- **Port Forwarding**: Quick access to the web application through port forwarding, allowing local development and testing without exposing the application externally.
- **Log Management**: Centralized logging for both MySQL and web application pods, simplifying debugging and monitoring of the application.
- **Namespace Isolation**: Uses separate namespaces for MySQL and web application components, promoting organization and security within the Kubernetes cluster.
- **Kubernetes Resource Management**: YAML configuration files provided for easy deployment and management of Kubernetes resources (pods, ReplicaSets, services, deployments).

## Table of Contents

- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
- [Kubernetes Tasks](#kubernetes-tasks)

## Prerequisites

- [Docker](https://www.docker.com/) installed and running
- [Kubernetes](https://kubernetes.io/) cluster set up
- `kubectl` configured to communicate with your cluster

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/kubernetes-webapp.git
   cd kubernetes-webapp
## Usage

1:  Start Docker and Check Kubernetes Components
```bash
sudo systemctl start docker
docker ps
kubectl get all -n kube-system
kubectl describe pod/kube-apiserver-kind-control-plane 
kubectl get all -n webapp-namespace
kubectl get all -n mysql-namespace
```

2 : Deploy Pods and Test Application
```bash
kubectl apply -f mysql-pod.yaml -n mysql-namespace
kubectl describe pod sql-pod -n mysql-namespace
kubectl apply -f app-pod.yaml -n webapp-namespace
kubectl port-forward web-app-pod 8080:8080 -n webapp-namepace
curl localhost:8080
kubectl logs sql-pod -n mysql-namespace
kubectl logs web-app-pod -n webapp-namespace
```

3: Create ReplicaSets
```bash
kubectl apply -f mysql-replicasets.yaml -n mysql-namespace 
kubectl apply -f app-replicasets.yaml -n webapp-namespace
```

4: Deploy Applications
```bash
kubectl apply -f mysql-deployment.yaml -n mysql-namespace 
kubectl apply -f webapp-deployment.yaml -n webapp-namespace
```


5: Create Services for Applications
```bash
kubectl apply -f mysql-service.yaml -n mysql-namespace 
kubectl apply -f app-service.yaml -n webapp-namespace 
```

6: Describe and Manage Pods
```bash
kubectl describe pod sql-pod -n mysql-namespace

kubectl describe replicaset web-app-replicaset -n webapp-namespace    

kubectl describe pod web-app-pod -n webapp-namespace

kubectl delete pod sql-pod -n mysql-namespace

kubectl port-forward web-app-pod 8080:8080 -n webapp-namepace
```

10.244.0.6

## Kubernetes Tasks


### Initial Setup and Status Check
- Start Docker and check running containers.
- Verify Kubernetes components and deployed resources.

### Pod Deployment and Logging
- Deploy MySQL and web application pods.
- Port-forward and test the application.
- Access logs for both pods.

### ReplicaSet Management
- Create ReplicaSets for MySQL and the web application.

### Deployment Management
- Deploy MySQL and web application using Deployment configurations.

### Service Management
- Create services to expose the MySQL and web application pods.
