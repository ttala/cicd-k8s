# CI/CD Pipeline to Deploy a Python App on Kubernetes

This project demonstrates modern DevOps practices such as containerization, orchestration, and CI/CD. It uses GitHub Actions to automate the process of building a Docker image and deploying a Python application to a Kubernetes cluster.

## Workflow Overview

The GitHub Actions workflow triggers on every push and consists of two jobs:
- **Build:** Builds a Docker image and pushes it to Docker Hub.
- **Deploy:** Deploys the application to a Kubernetes cluster using the built image.

The workflow is defined in `.github/workflows/<your-workflow-file>.yaml`.

## Requirements

### Kubernetes Cluster
Extract or create a minimal `~/.kube/config` from your cluster, encode it in base64, and add it as a GitHub secret.

### Required GitHub Secrets
- `DOCKERHUB_USERNAME`: Your Docker Hub username
- `DOCKERHUB_TOKEN`: Docker Hub access token (not password)
- `KUBECONFIG_CICD`: Base64-encoded kubeconfig file
- `API_KEY`: API key used by the app ([Get one from OpenWeatherMap](https://home.openweathermap.org/))

## Getting Started

```bash
git clone https://github.com/ttala/cicd-k8s.git
cd cicd-k8s
```
Edit the workflow file to remove or update the Kubernetes context cicd-sa-ctx. Also, set your Docker username as an environment variable in the workflow:
```env:
  DOCKER_USER: your_dockerhub_username
```
The pipeline runs automatically on every push or can be manually triggered from the GitHub Actions tab.