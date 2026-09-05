# NGINX Security & Reverse Proxy Lab

A hands-on infrastructure lab demonstrating NGINX reverse proxy configuration, HTTPS/TLS termination, request rate limiting, security headers, and web-service troubleshooting.

## Overview

This project creates a small reverse-proxy environment using NGINX and Docker Compose. Client traffic is received by an NGINX proxy and forwarded to a backend web service.

The configuration also demonstrates HTTPS redirection, TLS termination, rate limiting, proxy headers, and basic HTTP security headers.

## Technologies

- Linux
- NGINX
- Docker
- HTTP/HTTPS
- TLS
- OpenSSL

## Architecture

Client  
↓  
NGINX Reverse Proxy  
↓  
Backend Web Service

NGINX handles incoming HTTP/HTTPS requests before forwarding traffic to the backend container.

## Features

- NGINX reverse proxy
- HTTP to HTTPS redirection
- TLS 1.2 and TLS 1.3
- Self-signed certificate support for local testing
- Request rate limiting
- Reverse-proxy headers
- Basic security headers
- Docker Compose environment

## Repository Files

`nginx.conf`  
Main NGINX configuration containing HTTPS, reverse proxy, rate limiting, and security settings.

`docker-compose.yml`  
Creates the NGINX proxy and backend containers.

`generate-certs.sh`  
Generates a self-signed TLS certificate for local testing.

`.gitignore`  
Prevents generated certificates and local files from being committed.

## Running the Lab

Generate a local TLS certificate:

```bash
chmod +x generate-certs.sh
./generate-certs.sh
```

Start the containers:

```bash
docker compose up -d
```

Open:

```text
https://localhost:8443
```

Because the lab uses a self-signed certificate, the browser may display a certificate warning during local testing.

## Useful Troubleshooting Commands

Validate the NGINX configuration:

```bash
docker compose exec proxy nginx -t
```

View running containers:

```bash
docker compose ps
```

View proxy logs:

```bash
docker compose logs proxy
```

View backend logs:

```bash
docker compose logs backend
```

Test HTTPS from the command line:

```bash
curl -k https://localhost:8443
```

Stop the environment:

```bash
docker compose down
```

## Troubleshooting Approach

When diagnosing reverse-proxy issues, useful checks include:

1. Confirming that both containers are running
2. Validating the NGINX configuration
3. Reviewing proxy and backend logs
4. Testing network connectivity between services
5. Checking HTTP response codes
6. Verifying certificate paths and permissions
7. Confirming that the backend service is reachable

## Skills Demonstrated

- Linux system configuration
- NGINX administration
- HTTP and HTTPS concepts
- TLS configuration
- Reverse proxy configuration
- Rate limiting
- Docker networking
- Technical troubleshooting
- Log analysis
- Technical documentation

## Purpose

This repository is part of my technical portfolio focused on systems, networking, cybersecurity, and troubleshooting.