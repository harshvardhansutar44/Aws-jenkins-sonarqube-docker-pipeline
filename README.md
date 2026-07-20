# 🚀 End-to-End CI/CD Pipeline with Jenkins, SonarQube, Docker & AWS

## 📌 Project Overview

This project demonstrates an end-to-end CI/CD pipeline using GitHub, Jenkins, SonarQube, Docker, and AWS EC2.

Whenever code is pushed to GitHub, Jenkins automatically triggers the pipeline, performs static code analysis using SonarQube, transfers the application to a Docker server, builds a Docker image, and deploys the application inside a Docker container.

---

# Architecture

```
Developer
     │
     ▼
 GitHub Repository
     │
     ▼
 GitHub Webhook
     │
     ▼
 Jenkins
     │
     ├──────────────► SonarQube
     │                 Code Analysis
     │
     ▼
 Copy Application
     │
     ▼
 Docker Server
     │
     ▼
 Docker Build
     │
     ▼
 Docker Container
     │
     ▼
 End Users
```

---

# Technologies Used

- AWS EC2
- Jenkins
- GitHub
- GitHub Webhooks
- SonarQube Community Edition
- Docker
- Ubuntu Linux
- Git
- Nginx

---

# Project Workflow

### Step 1

Launch three AWS EC2 instances.

| Instance | Purpose |
|----------|----------|
| Jenkins | CI/CD Automation |
| SonarQube | Code Quality Analysis |
| Docker | Application Deployment |

---

### Step 2

Configure Jenkins

- Install Jenkins
- Create Freestyle Project
- Connect GitHub Repository
- Configure GitHub Credentials
- Enable GitHub Webhook Trigger

---

### Step 3

Configure SonarQube

- Install Java
- Download SonarQube Community Edition
- Start SonarQube
- Create Project
- Generate Analysis Token
- Configure SonarScanner

---

### Step 4

Integrate SonarQube with Jenkins

- Install SonarQube Scanner Plugin
- Configure SonarQube Server
- Add Sonar Token
- Configure SonarScanner Tool
- Add Sonar Build Step

---

### Step 5

Configure Docker Server

- Install Docker Engine
- Enable Docker Service
- Configure SSH Access
- Generate Jenkins SSH Key
- Copy Public Key to Docker Server

---

### Step 6

Configure Remote Deployment

Install Jenkins SSH2 Easy Plugin

Configure

- Server Group
- Remote Server
- SSH Authentication

---

### Step 7

Create Dockerfile

```dockerfile
FROM nginx
COPY . /usr/share/nginx/html/
```

---

### Step 8

Transfer Project

Jenkins copies application files to Docker Server using SCP.

```bash
scp -r ./fruitkha-1.0.0 ubuntu@<DOCKER_SERVER_IP>:~/website/
```

---

### Step 9

Build Docker Image

```bash
docker build -t mywebsite .
```

---

### Step 10

Run Docker Container

```bash
docker run -d -p 8085:80 --name fruitkha-website mywebsite
```

---

# Jenkins Pipeline Flow

```
GitHub Push
      │
      ▼
GitHub Webhook
      │
      ▼
Jenkins Build
      │
      ▼
Checkout Code
      │
      ▼
SonarQube Analysis
      │
      ▼
Copy Files to Docker Server
      │
      ▼
Docker Build
      │
      ▼
Docker Run
      │
      ▼
Application Live
```

---

# SonarQube Analysis

The project performs

- Static Code Analysis
- Bug Detection
- Vulnerability Detection
- Code Smell Detection
- Security Hotspot Analysis

---

# Features

✅ GitHub Webhook Integration

✅ Jenkins Automation

✅ SonarQube Static Analysis

✅ Remote Deployment using SSH

✅ Docker Image Build

✅ Docker Container Deployment

✅ Continuous Integration

✅ Continuous Delivery

---

# Project Structure

```
.
├── Dockerfile
├── Jenkinsfile
├── README.md
├── fruitkha-1.0.0/
├── assets/
└── images/
```

---

# Screenshots

Add screenshots for:

- AWS EC2 Instances
- Jenkins Dashboard
- Jenkins Build Success
- SonarQube Dashboard
- Docker Container
- Running Website
- GitHub Repository
- Pipeline Build Logs

---

# Future Improvements

- Convert Freestyle Project to Jenkins Pipeline
- Docker Hub Integration
- Kubernetes Deployment
- ArgoCD
- Terraform
- Prometheus Monitoring
- Grafana Dashboard
- Email Notifications
- Slack Notifications

---

# Learning Outcomes

- Jenkins CI/CD
- SonarQube Integration
- Docker Deployment
- AWS EC2
- GitHub Webhooks
- SSH Automation
- Linux Administration
- DevOps Best Practices

---

# Author

Harshvardhan Sutar
DevOps Engineer
