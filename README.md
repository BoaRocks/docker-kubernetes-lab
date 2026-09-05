# NGINX Security & Reverse Proxy Lab

A hands-on portfolio lab demonstrating reverse proxy configuration, request
routing, rate limiting, HTTP troubleshooting, and TLS termination concepts
using NGINX and Docker.

## Overview

This lab uses NGINX as a reverse proxy in front of a separate backend web
service. Requests enter through the proxy, are evaluated against a per-client
rate limit, and are forwarded to the backend container.

The project is designed to demonstrate practical Linux, networking,
configuration, troubleshooting, and security concepts in a small reproducible
environment.

## Technologies

- NGINX
- Docker
- Docker Compose
- Linux
- HTTP/HTTPS
- TCP/IP
- TLS

## Architecture

```text
Client
  |
  | HTTP :8080
  v
NGINX Reverse Proxy
  |
  | Internal Docker network
  v
Backend NGINX Service