🚀 End-to-End CI/CD Pipeline with Jenkins, SonarQube, Docker & AWS
📌 Project Overview
This project demonstrates an end-to-end CI/CD pipeline using GitHub, Jenkins, SonarQube, Docker, and AWS EC2.
Whenever code is pushed to GitHub, Jenkins automatically triggers the build process. The project supports multiple Jenkins configurations:
•	Jenkins Freestyle Project
•	Jenkins Pipeline Project
It includes two different Jenkinsfiles:
1.	Jenkinsfile without SonarQube
o	Performs source code checkout
o	Transfers application files to Docker Server
o	Builds Docker image
o	Deploys application container
2.	Jenkinsfile with SonarQube
o	Performs source code checkout
o	Executes SonarQube static code analysis
o	Checks code quality
o	Transfers application files to Docker Server
o	Builds Docker image
o	Deploys application container
________________________________________
Architecture
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
     ├──────────────► Docker Server 1
     │                     │
     │                     ▼
     │              Docker Container
     │
     └──────────────► Docker Server 2
                           │
                           ▼
                    Docker Container
                           │
                           ▼
             AWS Application Load Balancer
                           │
                           ▼
                      End Users

Technologies Used
•	AWS EC2
•	Jenkins
•	Jenkins Freestyle Project
•	Jenkins Pipeline Project
•	GitHub
•	GitHub Webhooks
•	SonarQube Community Edition
•	Docker
•	Ubuntu Linux
•	Git
•	Nginx
________________________________________
Jenkins Project Configurations
This project contains two Jenkins implementation approaches.
1. Jenkins Freestyle Project
The Freestyle project is configured using the Jenkins GUI.
Configuration Includes:
•	GitHub Repository Integration
•	GitHub Webhook Trigger
•	Git Checkout
•	SonarQube Build Step (optional)
•	SSH File Transfer to Docker Server
•	Remote Shell Execution
•	Docker Image Build
•	Docker Container Deployment
Freestyle Workflow

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
Copy Files to Docker Server 1 & Docker Server 2
      │
      ▼
Docker Build
      │
      ▼
Docker Run
      │
      ▼
AWS Application Load Balancer
      │
      ▼
Application Live________________________________________
2. Jenkins Pipeline Project
The Pipeline project uses Jenkinsfile for automation.
Two pipeline versions are available:
Jenkinsfile Without SonarQube
Pipeline stages:
2. Jenkins Freestyle Project
Pipeline stages:
Checkout Code
      │
      ▼
Transfer Files to Docker Server 1 & Docker Server 2
      │
      ▼
Docker Build
      │
      ▼
Docker Deploy
      │
      ▼
AWS Application Load Balancer
Jenkinsfile With SonarQube
Pipeline stages:
Jenkinsfile With SonarQube

Pipeline stages:

Checkout Code
      │
      ▼
SonarQube Analysis
      │
      ▼
Quality Check
      │
      ▼
Transfer Files to Docker Server 1 & Docker Server 2
      │
      ▼
Docker Build
      │
      ▼
Docker Deploy
      │
      ▼
AWS Application Load Balancer________________________________________
Jenkins Files Structure
.
├── Jenkinsfile
├── Jenkinsfile-sonarqube
├── Dockerfile
├── README.md
├── fruitkha-1.0.0/
├── assets/
└── images/
Jenkinsfile
Pipeline configuration without SonarQube integration.
Jenkinsfile-sonarqube
Pipeline configuration with SonarQube static code analysis.
________________________________________
Project Workflow
Step 1

Launch Four AWS EC2 instances.

Instance              Purpose

Jenkins               CI/CD Automation

SonarQube             Code Quality Analysis

Docker Server 1       Application Deployment

Docker Server 2       Application Deployment
________________________________________
Step 2
Configure Jenkins
•	Install Jenkins
•	Create Freestyle Project
•	Create Pipeline Project
•	Connect GitHub Repository
•	Configure GitHub Credentials
•	Enable GitHub Webhook Trigger
________________________________________
Step 3
Configure SonarQube
•	Install Java
•	Download SonarQube Community Edition
•	Start SonarQube
•	Create Project
•	Generate Analysis Token
•	Configure SonarScanner
________________________________________
Step 4
Integrate SonarQube with Jenkins
•	Install SonarQube Scanner Plugin
•	Configure SonarQube Server
•	Add Sonar Token
•	Configure SonarScanner Tool
•	Add Sonar Build Step
________________________________________
Step 5
Configure Docker Server
•	Install Docker Engine
•	Enable Docker Service
•	Configure SSH Access
•	Generate Jenkins SSH Key
•	Copy Public Key to Docker Server
________________________________________
Step 6
Configure Remote Deployment
Install Jenkins SSH2 Easy Plugin
Configure:
•	Server Group
•	Remote Server
•	SSH Authentication
________________________________________
Step 7
Create Dockerfile
FROM nginx
COPY . /usr/share/nginx/html/
________________________________________
Step 8
Transfer Project
Jenkins copies application files to Docker Server using SCP.
scp -r ./fruitkha-1.0.0 ubuntu@<DOCKER_SERVER_IP>:~/website/
________________________________________
Step 9
Build Docker Image
docker build -t mywebsite .
________________________________________
Step 10
Run Docker Container
docker run -d -p 8085:80 --name fruitkha-website mywebsite

________________________________________

Step 11

Configure AWS Application Load Balancer (ALB)

Create and configure an Application Load Balancer to distribute incoming traffic between both Docker servers.

Configuration:

• Create an Application Load Balancer in AWS

• Select Internet-facing Load Balancer

• Configure Availability Zones and Subnets

• Create Target Group for Docker Servers

• Register Docker Server 1 and Docker Server 2 as Targets

• Configure Health Check Settings

• Add Listener (HTTP/HTTPS)

• Forward traffic from Load Balancer to Target Group

• Verify Target Health Status

Traffic Flow:

User Request
      │
      ▼
AWS Application Load Balancer
      │
      ├──────────────► Docker Server 1
      │                     │
      │                     ▼
      │              Docker Container
      │
      └──────────────► Docker Server 2
                            │
                            ▼
                     Docker Container


The Application Load Balancer distributes user traffic across both Docker servers, improving application availability and scalability.
________________________________________


SonarQube Analysis
The SonarQube-enabled pipeline performs:
•	Static Code Analysis
•	Bug Detection
•	Vulnerability Detection
•	Code Smell Detection
•	Security Hotspot Analysis
•	Code Quality Reporting
________________________________________
Features
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
________________________________________
Screenshots
Add screenshots for:
•	AWS EC2 Instances
•	Jenkins Freestyle Job
•	Jenkins Pipeline Job
•	Jenkins Build Success
•	SonarQube Dashboard
•	Docker Container
•	Running Website
•	GitHub Repository
•	Pipeline Build Logs
________________________________________
Future Improvements
•	Docker Hub Integration
•	Kubernetes Deployment
•	ArgoCD
•	Terraform
•	Prometheus Monitoring
•	Grafana Dashboard
•	Email Notifications
•	Slack Notifications
________________________________________
Learning Outcomes
•	Jenkins CI/CD
•	Jenkins Freestyle and Pipeline Projects
•	SonarQube Integration
•	Docker Deployment
•	AWS EC2
•	GitHub Webhooks
•	SSH Automation
•	Linux Administration
•	DevOps Best Practices
________________________________________
Author
Harshvardhan Sutar
DevOps Engineer
