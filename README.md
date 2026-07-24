🚀 End-to-End CI/CD Pipeline with Jenkins, SonarQube, Docker & AWS
📌 Project Overview
This project demonstrates an end-to-end CI/CD pipeline using GitHub, Jenkins, SonarQube, Docker, and AWS EC2.
Whenever code is pushed to GitHub, Jenkins automatically triggers the pipeline, performs static code analysis using SonarQube, transfers the application to a Docker server, builds a Docker image, and deploys the application inside a Docker container.
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
________________________________________
Technologies Used
•	AWS EC2
•	Jenkins
•	GitHub
•	GitHub Webhooks
•	SonarQube Community Edition
•	Docker
•	Ubuntu Linux
•	Git
•	Nginx
________________________________________
Project Workflow
Step 1
Launch three AWS EC2 instances.
Instance	Purpose
Jenkins	CI/CD Automation
SonarQube	Code Quality Analysis
Docker	Application Deployment
________________________________________
Step 2
Configure Jenkins
•	Install Jenkins
•	Create Freestyle Project
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
Configure
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
Jenkins Pipeline Flow
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
________________________________________
SonarQube Analysis
The project performs
•	Static Code Analysis
•	Bug Detection
•	Vulnerability Detection
•	Code Smell Detection
•	Security Hotspot Analysis
________________________________________
Features
✅ GitHub Webhook Integration
✅ Jenkins Automation
✅ SonarQube Static Analysis
✅ Remote Deployment using SSH
✅ Docker Image Build
✅ Docker Container Deployment
✅ Continuous Integration
✅ Continuous Delivery
________________________________________
Project Structure
.
├── Dockerfile
├── Jenkinsfile
├── README.md
├── fruitkha-1.0.0/
├── assets/
└── images/
________________________________________
Screenshots
Add screenshots for:
•	AWS EC2 Instances
•	Jenkins Dashboard
•	Jenkins Build Success
•	SonarQube Dashboard
•	Docker Container
•	Running Website
•	GitHub Repository
•	Pipeline Build Logs
________________________________________
Future Improvements
•	Convert Freestyle Project to Jenkins Pipeline
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
•	SonarQube Integration
•	Docker Deployment
•	AWS EC2
•	GitHub Webhooks
•	SSH Automation
•	Linux Administration
•	DevOps Best Practices
________________________________________
Author
Harshvardhan Sutar DevOps Engineer
