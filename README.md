# VProfile GitOps Application Deployment Repository (vprofile-gitops-app-deploy)

## Parent GitOps Project

This repository is part of the GitOps platform:

https://github.com/josephmj0303/vprofile-gitops-eks-platform

## Overview

This repository manages the CI/CD pipeline and Kubernetes deployment of the VProfile application using GitHub Actions, Docker, Helm, and Amazon EKS.

This repository follows GitOps principles where application deployment is fully automated and controlled through Git.

---

## Purpose

This repository performs:

- Application testing
- Code quality analysis using SonarCloud
- Docker image build
- Push Docker image to Amazon ECR
- Deploy application to Amazon EKS using Helm

---

## GitOps Deployment Workflow

Deployment flow:

Code Push → GitHub Actions → Test → SonarCloud Scan → Docker Build → Push to ECR → Helm Deploy → EKS


---

## Technology Stack

- Java
- Maven
- Docker
- Kubernetes
- Helm
- GitHub Actions
- AWS ECR
- AWS EKS
- SonarCloud

---

## Repository Structure

```
vprofile-gitops-app-deploy/
│
├── architecture/
│   └── vprofile_gitops_architecture.png
│
├── src/
├── Dockerfile
├── pom.xml
│
├── helm/
│   └── vprofilecharts/
│        ├── Chart.yaml
│        ├── values.yaml
│        ├── templates/
│
├── .github/
│   └── workflows/
│        ├── main.yml
│
├── screenshots/
│   └── vprofile_action_deploy.png
│
└── README.md
```

---

## CI/CD Pipeline Stages

### Stage 1: Testing

Runs:

mvn test
mvn checkstyle

Ensures application correctness.

---

### Stage 2: Code Quality Scan

Runs:

SonarCloud Scan

Ensures code quality and security.

---

### Stage 3: Build Docker Image

Builds container image:

docker build

---

### Stage 4: Push Image to ECR

Pushes Docker image to Amazon ECR:

docker push

---

### Stage 5: Deploy to EKS

Deploys using Helm:

helm upgrade --install

---

## Deployment Instructions

### Step 1: Clone Repository

git clone https://github.com/josephmj0303/vprofile-gitops-app-deploy.git

cd vprofile-gitops-app-deploy

---

### Step 2: Configure GitHub Secrets

Required secrets:

AWS_ACCESS_KEY_ID
AWS_SECRET_ACCESS_KEY
REGISTRY
SONAR_TOKEN
SONAR_URL
SONAR_ORGANIZATION
SONAR_PROJECT_KEY

---

### Step 3: Trigger Deployment

Go to GitHub:

Actions → vprofile actions → Run Workflow

Pipeline will:

- Test application
- Scan code
- Build Docker image
- Push image to ECR
- Deploy to EKS

---

## Kubernetes Components Deployed

- Deployment
- Service
- Ingress
- ConfigMaps
- Secrets

Managed using Helm charts.

---

## Application Access

After deployment:

http://vprofile.joedevopslab.xyz

---

## Cache Architecture

Application uses Memcached for caching.

Cache Flow:

Cache miss:

Request → Database → Cache Insert → Response

Cache hit:

Request → Cache → Response

Benefits:

- Faster response
- Reduced database load
- Improved performance

---

## Benefits

- Fully automated CI/CD
- Immutable deployments
- Version-controlled deployments
- Scalable architecture
- Production-ready pipeline

---

## Future Improvements

Recommended improvements:

- Add ArgoCD
- Add Prometheus and Grafana monitoring
- Add logging stack
- Add Blue-Green deployment
- Add Canary deployment
- Add autoscaling

---

## Skills Demonstrated

- Kubernetes
- Docker
- Helm
- GitHub Actions
- AWS EKS
- AWS ECR
- GitOps
- CI/CD
- SonarCloud
