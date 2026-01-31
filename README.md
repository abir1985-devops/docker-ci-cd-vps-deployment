# CI/CD Docker Deployment to VPS

This repository demonstrates a simple DevOps workflow to deliver and run a containerized backend service on a Linux VPS using GitHub Actions, GitHub Container Registry (GHCR), and Docker Compose.

---

## What this project shows

- Automated build pipeline with GitHub Actions
- Docker image publishing to GitHub Container Registry (GHCR)
- Pulling the published image on a VPS
- Running the service with Docker Compose
- Environment-based configuration (no secrets in Git)

---

## Deployment Flow (high level)

1. Developer pushes code to GitHub
2. GitHub Actions runs tests and builds a Docker image
3. The image is pushed to GHCR (registry)
4. The VPS pulls the image from GHCR
5. Docker Compose starts the containers on the server

---

## Environment Configuration

Create a `.env` file on the server based on `.env.example` and set a strong `JWT_SECRET`.
Environment variables are not committed to GitHub.



## Production Compose (concept)

In production we do **not** build on the server.
We run a pre-built image from the registry:

- API container: pulled from GHCR
- MongoDB container: runs with a persistent volume

---

## Example (Live Deployment)

This workflow is used to deploy the following backend API:

- API: http://82.165.138.175:3000
- Swagger UI: http://82.165.138.175:3000/api/docs
- Health Check: http://82.165.138.175:3000/health

---

## Tools Used

- Docker
- Docker Compose
- GitHub Actions
- GitHub Container Registry (GHCR)
- Linux VPS (Ubuntu)
