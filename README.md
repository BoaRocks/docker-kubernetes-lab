# Docker & Kubernetes Deployment Lab

A hands-on infrastructure lab demonstrating containerization with Docker and application deployment using Kubernetes.

## Overview

This project packages a simple web service into a Docker container and provides Kubernetes manifests for deploying and exposing the application.

The lab focuses on containerization, deployment configuration, service networking, workload management, and troubleshooting.

## Technologies

- Docker
- Kubernetes
- Linux
- NGINX
- YAML
- HTML

## Architecture

Web Application  
↓  
Docker Container  
↓  
Kubernetes Deployment  
↓  
Kubernetes Service

## Features

- Lightweight NGINX-based container
- Custom Docker image
- Kubernetes Deployment
- Two application replicas
- Kubernetes Service
- Health/readiness checking
- Resource requests and limits
- Reproducible infrastructure configuration

## Repository Files

`Dockerfile`  
Defines the application container.

`index.html`  
Simple web page served by NGINX.

`deployment.yaml`  
Defines the Kubernetes Deployment and application replicas.

`service.yaml`  
Creates a Kubernetes Service for accessing the application.

`.dockerignore`  
Excludes unnecessary files from the Docker build context.

## Build the Docker Image

```bash
docker build -t docker-kubernetes-lab:local .
```

## Run with Docker

```bash
docker run --rm -p 8080:80 docker-kubernetes-lab:local
```

Then open:

```text
http://localhost:8080
```

## Deploy to Kubernetes

Apply the Deployment:

```bash
kubectl apply -f deployment.yaml
```

Apply the Service:

```bash
kubectl apply -f service.yaml
```

## Verify the Deployment

Check deployments:

```bash
kubectl get deployments
```

Check pods:

```bash
kubectl get pods
```

Check services:

```bash
kubectl get services
```

## Access the Application

Port-forward the Kubernetes Service:

```bash
kubectl port-forward service/docker-kubernetes-lab-service 8080:80
```

Then open:

```text
http://localhost:8080
```

## Useful Troubleshooting Commands

Inspect a pod:

```bash
kubectl describe pod <pod-name>
```

View application logs:

```bash
kubectl logs <pod-name>
```

Check pod status:

```bash
kubectl get pods -o wide
```

Inspect the deployment:

```bash
kubectl describe deployment docker-kubernetes-lab
```

Check service configuration:

```bash
kubectl describe service docker-kubernetes-lab-service
```

## Troubleshooting Approach

When diagnosing deployment issues, useful checks include:

1. Checking pod status
2. Reviewing container logs
3. Inspecting Kubernetes events
4. Confirming image availability
5. Checking labels and selectors
6. Verifying container ports
7. Confirming Service connectivity
8. Reviewing readiness probe status

## Skills Demonstrated

- Docker containerization
- Kubernetes configuration
- Linux
- Infrastructure deployment
- YAML configuration
- Service networking
- Container troubleshooting
- Log analysis
- Technical documentation

## Purpose

This repository is part of my technical portfolio focused on systems, networking, cybersecurity, infrastructure, and troubleshooting.