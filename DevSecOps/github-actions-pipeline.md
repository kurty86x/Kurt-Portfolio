# 📝 Overview
This project demonstrates how I built a beginner‑friendly CI/CD pipeline using GitHub Actions to automate building, testing, and deploying a containerized application.

The goal was to understand how pipelines improve consistency, reduce manual work, and support DevSecOps workflows.

--- 

### 🎯 Objectives
- Create a GitHub Actions workflow
- Automate Docker image builds
- Run basic linting or tests
- Push images to a container registry (optional)
- Use GitHub Secrets for secure variables
- Trigger pipelines on push and pull requests

---

### 🏗️ Lab Environment
- GitHub repository
- GitHub Actions enabled
- Docker installed locally (for testing)
- Optional: Docker Hub or GitHub Container Registry

---

## 📁 Project Structure
```Folder Structure
cicd-pipeline/
│── .github/
│     └── workflows/
│           └── ci.yml
│── app/
│     └── app.py (or index.js)
│── Dockerfile
└── docs/
```
---

## ⚙️ GitHub Actions Workflow
.github/workflows/ci.yml

```ci.yml
name: CI Pipeline

on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout code
      uses: actions/checkout@v3

    - name: Set up Docker Buildx
      uses: docker/setup-buildx-action@v2

    - name: Build Docker image
      run: docker build -t myapp:latest .

    - name: Run basic tests
      run: echo "Running tests..."  # placeholder for real tests

    - name: Lint Dockerfile
      run: |
        echo "Linting Dockerfile..."
        docker run --rm -i hadolint/hadolint < Dockerfile
```

🔐 Using GitHub Secrets

Secrets are stored under:

Repository → Settings → Secrets → Actions

Examples:
- DOCKERHUB_USERNAME
- DOCKERHUB_TOKEN
- REGISTRY_PASSWORD

```yaml
env:
  DOCKERHUB_USERNAME: ${{ secrets.DOCKERHUB_USERNAME }}
```

## 🐳 Optional: Push Image to Docker Hub

```yaml
- name: Log in to Docker Hub
  uses: docker/login-action@v2
  with:
    username: ${{ secrets.DOCKERHUB_USERNAME }}
    password: ${{ secrets.DOCKERHUB_TOKEN }}

- name: Push image
  run: docker push myapp:latest
```

---

## 🧪 Validation Checklist
- Workflow triggers on push and pull requests
- Docker image builds successfully
- Test steps run without errors
- Secrets are not exposed in logs
- Pipeline status shows ✔️ green checkmarks

---

## 🛠️ Troubleshooting
- **Workflow fails immediately**
Check YAML indentation — GitHub Actions is strict.

- **Docker build fails**  
  Validate Dockerfile locally:
  ```
  Command:
  docker build
  ```

- **Secrets not found** 
  Ensure they are added under Actions Secrets, not Dependabot Secrets.

- **Linting errors** 
  Fix Dockerfile formatting or base image issues.

---

## 📘 What I Learned
- How CI/CD pipelines automate builds and tests
- How GitHub Actions workflows are structured
- How to use secrets securely in pipelines
- How containerized apps integrate with CI/CD
- How automation supports DevSecOps practices