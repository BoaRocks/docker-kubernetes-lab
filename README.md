# Docker & Kubernetes Deployment Lab

A small infrastructure lab demonstrating containerized application deployment
and Kubernetes configuration.

## Technologies
- Docker
- Kubernetes
- Linux
- YAML

## What This Lab Demonstrates
- Containerized application deployment
- Kubernetes Deployments and Services
- Replica management
- Service discovery concepts
- Basic troubleshooting of containerized workloads

## Kubernetes Files
- `deployment.yaml` creates two application replicas
- `service.yaml` exposes the application internally through a Kubernetes Service

## Useful Troubleshooting Commands

```bash
kubectl get pods
kubectl get deployments
kubectl get services
kubectl describe pod <pod-name>
kubectl logs <pod-name>