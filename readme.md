# Node.js CI/CD Pipeline for Production Deployment

This project demonstrates a **production-grade CI/CD pipeline** built for a Node.js application using **Jenkins**, **Docker**, **Trivy**, **SonarQube**, **Kubernetes**, and other modern DevOps tools.

It is inspired by a real-world pipeline built for enterprise use (originally implemented in Java), and recreated here in Node.js for **open-source sharing**, **community contribution**, and **technical demonstration** purposes.

---

## Technologies & Tools Used

| Tool | Purpose |
|------|---------|
| **Jenkins** | CI/CD automation server |
| **GitHub** | Source control |
| **Node.js** | Application runtime |
| **Docker** | Containerization |
| **Kubernetes** | Deployment orchestration |
| **Trivy** | Filesystem & Docker image vulnerability scanning |
| **SonarQube** | Static code analysis |
| **Email Extension Plugin** | Build status notifications |
| **Nexus (optional)** | Artifact repository (not used in Node version) |

---

## Project Structure

cicd-nodejs-demo/
- app.js(Simple Express server)
- package.json (Node dependencies)
- Dockerfile (Docker build file)
- Jenkinsfile (Jenkins pipeline)
- sonar-project.properties (SonarQube configuration)
- trivy-fs-report.html  (Generated-Filesystem scan report)
- trivy-image-report.html (Generated-Docker image scan report)
- kubernetes/deployment-service.yaml


---

## Pipeline Stages Overview

1. **Git Checkout** – Clones the main branch using Jenkins credentials  
2. **Install Dependencies** – Runs `npm install`  
3. **Test** – Executes `npm test`  
4. **Filesystem Security Scan** – Trivy scan of project folder  
5. **SonarQube Analysis** – Static code analysis for bugs, smells, vulnerabilities  
6. **Quality Gate** – Verifies code quality via SonarQube  
7. **Build & Tag Docker Image** – Builds image and tags as `latest`  
8. **Docker Image Security Scan** – Trivy scan of the image  
9. **Push Docker Image** – Pushes image to Docker Hub  
10. **Deploy to Kubernetes** – Applies deployment/service YAML  
11. **Verify Deployment** – Lists pods and services in `webapps` namespace  
12. **Notification** – Sends HTML email with status and Trivy report

---

## How to Run Locally


# Clone this repo
git clone https://github.com/CliffordIsaboke/cicd-nodejs-demo.git
cd cicd-nodejs-demo

# Run the app locally
npm install
node app.js

## Docker Usage
docker build -t yourname/nodejs-demo:latest .
docker run -p 3000:3000 yourname/nodejs-demo

## Kubernetes Deployment
kubectl apply -f kubernetes/deployment-service.yaml
kubectl get pods -n webapps
kubectl get svc -n webapps


---


# Prerequisites
# Jenkins server with:
- NodeJS plugin
- SonarQube plugin
- Email Extension plugin
- Trivy installed


# Configured tools:
- Sonar Scanner
- Docker
- Kubernetes cluster access
- Valid credentials stored in Jenkins

# Contact
Maintainer: Clifford Isaboke
Email: isabokecliff@gmail.com

# License
MIT License — free to use and adapt with attribution.



