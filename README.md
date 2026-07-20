# 🚀 End-to-End CI/CD Pipeline with Jenkins, SonarQube, Docker & AWS

## 📌 Project Overview

This project demonstrates an end-to-end CI/CD pipeline using GitHub, Jenkins, SonarQube, Docker, and AWS EC2.

Whenever code is pushed to GitHub, Jenkins automatically triggers the build process. The project supports multiple Jenkins configurations:

* Jenkins Freestyle Project
* Jenkins Pipeline Project

It includes two different Jenkinsfiles:

1. **Jenkinsfile without SonarQube**

   * Performs source code checkout
   * Transfers application files to Docker Server
   * Builds Docker image
   * Deploys application container

2. **Jenkinsfile with SonarQube**

   * Performs source code checkout
   * Executes SonarQube static code analysis
   * Checks code quality
   * Transfers application files to Docker Server
   * Builds Docker image
   * Deploys application container

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

* AWS EC2
* Jenkins
* Jenkins Freestyle Project
* Jenkins Pipeline Project
* GitHub
* GitHub Webhooks
* SonarQube Community Edition
* Docker
* Ubuntu Linux
* Git
* Nginx

---

# Jenkins Project Configurations

This project contains two Jenkins implementation approaches.

## 1. Jenkins Freestyle Project

The Freestyle project is configured using the Jenkins GUI.

### Configuration Includes:

* GitHub Repository Integration
* GitHub Webhook Trigger
* Git Checkout
* SonarQube Build Step (optional)
* SSH File Transfer to Docker Server
* Remote Shell Execution
* Docker Image Build
* Docker Container Deployment

### Freestyle Workflow

```
GitHub Push
      │
      ▼
GitHub Webhook
      │
      ▼
Jenkins Freestyle Job
      │
      ▼
Checkout Code
      │
      ▼
SonarQube Analysis (Optional)
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

## 2. Jenkins Pipeline Project

The Pipeline project uses Jenkinsfile for automation.

Two pipeline versions are available:

### Jenkinsfile Without SonarQube

Pipeline stages:

```
Checkout Code
      │
      ▼
Transfer Files
      │
      ▼
Docker Build
      │
      ▼
Docker Deploy
```

### Jenkinsfile With SonarQube

Pipeline stages:

```
Checkout Code
      │
      ▼
SonarQube Analysis
      │
      ▼
Quality Check
      │
      ▼
Transfer Files
      │
      ▼
Docker Build
      │
      ▼
Docker Deploy
```

---

# Jenkins Files Structure

```
.
├── Jenkinsfile
├── Jenkinsfile-sonarqube
├── Dockerfile
├── README.md
├── fruitkha-1.0.0/
├── assets/
└── images/
```

### Jenkinsfile

Pipeline configuration without SonarQube integration.

### Jenkinsfile-sonarqube

Pipeline configuration with SonarQube static code analysis.

---

# Project Workflow

### Step 1

Launch three AWS EC2 instances.

| Instance  | Purpose                |
| --------- | ---------------------- |
| Jenkins   | CI/CD Automation       |
| SonarQube | Code Quality Analysis  |
| Docker    | Application Deployment |

---

### Step 2

Configure Jenkins

* Install Jenkins
* Create Freestyle Project
* Create Pipeline Project
* Connect GitHub Repository
* Configure GitHub Credentials
* Enable GitHub Webhook Trigger

---

### Step 3

Configure SonarQube

* Install Java
* Download SonarQube Community Edition
* Start SonarQube
* Create Project
* Generate Analysis Token
* Configure SonarScanner

---

### Step 4

Integrate SonarQube with Jenkins

* Install SonarQube Scanner Plugin
* Configure SonarQube Server
* Add Sonar Token
* Configure SonarScanner Tool
* Add Sonar Build Step

---

### Step 5

Configure Docker Server

* Install Docker Engine
* Enable Docker Service
* Configure SSH Access
* Generate Jenkins SSH Key
* Copy Public Key to Docker Server

---

### Step 6

Configure Remote Deployment

Install Jenkins SSH2 Easy Plugin

Configure:

* Server Group
* Remote Server
* SSH Authentication

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

# SonarQube Analysis

The SonarQube-enabled pipeline performs:

* Static Code Analysis
* Bug Detection
* Vulnerability Detection
* Code Smell Detection
* Security Hotspot Analysis
* Code Quality Reporting

---

# Features

✅ GitHub Webhook Integration

✅ Jenkins Freestyle Automation

✅ Jenkins Pipeline Automation

✅ Two Jenkinsfiles (With and Without SonarQube)

✅ SonarQube Static Analysis

✅ Remote Deployment using SSH

✅ Docker Image Build

✅ Docker Container Deployment

✅ Continuous Integration

✅ Continuous Delivery

---

# Screenshots

Add screenshots for:

* AWS EC2 Instances
* Jenkins Freestyle Job
* Jenkins Pipeline Job
* Jenkins Build Success
* SonarQube Dashboard
* Docker Container
* Running Website
* GitHub Repository
* Pipeline Build Logs

---

# Future Improvements

* Docker Hub Integration
* Kubernetes Deployment
* ArgoCD
* Terraform
* Prometheus Monitoring
* Grafana Dashboard
* Email Notifications
* Slack Notifications

---

# Learning Outcomes

* Jenkins CI/CD
* Jenkins Freestyle and Pipeline Projects
* SonarQube Integration
* Docker Deployment
* AWS EC2
* GitHub Webhooks
* SSH Automation
* Linux Administration
* DevOps Best Practices

---

# Author

Harshvardhan Sutar
DevOps Engineer
