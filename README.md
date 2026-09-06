# Docker & Kubernetes Deployment Lab

A hands-on infrastructure lab demonstrating Docker containerization, Kubernetes application deployment, service networking, health checks, resource management, and technical troubleshooting.

## Overview

This project packages a simple NGINX web application into a Docker container and provides Kubernetes manifests for deploying and exposing the application.

The lab demonstrates the relationship between container images, Kubernetes Deployments, Pods, Services, readiness probes, resource limits, and basic troubleshooting workflows.

## Technologies

- Docker
- Kubernetes
- Linux
- NGINX
- YAML
- HTML
- HTTP
- Container networking

## Architecture

```text
Client
  |
  v
Kubernetes Service
  |
  +---------------------+
  |                     |
  v                     v
Application Pod 1   Application Pod 2
NGINX               NGINX
```

## Features

- Custom Docker image
- Lightweight NGINX web service
- Kubernetes Deployment
- Two application replicas
- Kubernetes Service
- Readiness health probe
- CPU and memory requests
- CPU and memory limits
- Container networking
- Reproducible YAML configuration

## Repository Files

- `Dockerfile` — Defines the application container image
- `index.html` — Web page served by NGINX
- `deployment.yaml` — Defines the Kubernetes Deployment and application replicas
- `service.yaml` — Creates a Kubernetes Service for the application
- `.dockerignore` — Excludes unnecessary files from the Docker build context

## Build the Docker Image

Build the image locally:

```bash
docker build -t docker-kubernetes-lab:local .
```

Verify that the image exists:

```bash
docker images
```

## Run with Docker

Run the application directly with Docker:

```bash
docker run --rm -p 8080:80 docker-kubernetes-lab:local
```

Open:

```text
http://localhost:8080
```

You can also test it from the command line:

```bash
curl http://localhost:8080
```

## Kubernetes Local Image Requirement

The Kubernetes Deployment uses:

```yaml
image: docker-kubernetes-lab:local
imagePullPolicy: Never
```

Because `imagePullPolicy` is set to `Never`, Kubernetes will not attempt to download the image from an external container registry.

The `docker-kubernetes-lab:local` image must therefore be available to the Kubernetes node before the Deployment is created.

How a locally built image is made available to Kubernetes depends on the local Kubernetes environment being used.

## Deploy to Kubernetes

After confirming that the image is available to the Kubernetes node, apply the Deployment:

```bash
kubectl apply -f deployment.yaml
```

Apply the Service:

```bash
kubectl apply -f service.yaml
```

## Verify the Deployment

Check the Deployment:

```bash
kubectl get deployments
```

Check running Pods:

```bash
kubectl get pods
```

Check the Service:

```bash
kubectl get services
```

For additional information:

```bash
kubectl get pods -o wide
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

Or test from the command line:

```bash
curl http://localhost:8080
```

## Scaling

The Deployment is configured with two application replicas.

View the current replicas:

```bash
kubectl get deployment docker-kubernetes-lab
```

Scale the Deployment:

```bash
kubectl scale deployment docker-kubernetes-lab --replicas=4
```

Verify the new Pods:

```bash
kubectl get pods
```

Return to two replicas:

```bash
kubectl scale deployment docker-kubernetes-lab --replicas=2
```

## Troubleshooting

### Check Pod Status

```bash
kubectl get pods
```

### Inspect a Pod

```bash
kubectl describe pod <pod-name>
```

### View Container Logs

```bash
kubectl logs <pod-name>
```

### Inspect the Deployment

```bash
kubectl describe deployment docker-kubernetes-lab
```

### Inspect the Service

```bash
kubectl describe service docker-kubernetes-lab-service
```

### Check Service Endpoints

```bash
kubectl get endpoints
```

### Check Events

```bash
kubectl get events --sort-by=.metadata.creationTimestamp
```

## Troubleshooting Approach

When diagnosing a deployment issue, useful checks include:

1. Confirming that the container image is available to the Kubernetes node
2. Checking Pod status
3. Reviewing container logs
4. Inspecting Kubernetes events
5. Checking readiness probe status
6. Confirming Deployment labels
7. Confirming Service selectors
8. Verifying container and Service ports
9. Checking application connectivity

This approach helps isolate problems involving the container image, application process, Kubernetes configuration, networking, or Service routing.

## Readiness Probe

The Deployment includes an HTTP readiness probe.

Kubernetes uses the readiness probe to determine whether a Pod is ready to receive traffic through the Service.

If the readiness check fails, the Pod can continue running while Kubernetes temporarily prevents the Service from routing traffic to it.

## Resource Management

The Deployment defines CPU and memory requests and limits.

Requests specify the resources the container expects to require.

Limits restrict the maximum amount of CPU and memory the container can consume.

These settings demonstrate basic Kubernetes workload resource management.

## Skills Demonstrated

- Docker containerization
- Kubernetes Deployments
- Kubernetes Services
- Linux concepts
- Container networking
- YAML configuration
- HTTP troubleshooting
- Readiness probes
- Replica management
- Resource requests and limits
- Log analysis
- Systematic troubleshooting
- Technical documentation

## Purpose

This repository is part of my technical portfolio focused on systems, networking, infrastructure, cybersecurity, and technical troubleshooting.