# 🚀 CI/CD Pipeline using Jenkins, Docker, AWS ECR & ECS

## 📖 Project Overview

This project demonstrates a complete **CI/CD pipeline** using **Jenkins** and **AWS**.

Whenever code is pushed to GitHub, Jenkins automatically:

- Clones the latest source code
- Builds a Docker image
- Pushes the image to Amazon ECR
- Registers a new ECS Task Definition
- Deploys the latest version to Amazon ECS Fargate

The application is served through an **Application Load Balancer (ALB)**.

---

## 🛠️ Technologies Used

- Git & GitHub
- Jenkins
- Docker
- AWS EC2
- Amazon ECR
- Amazon ECS (Fargate)
- Application Load Balancer (ALB)
- AWS IAM
- Linux

---

## 🔄 CI/CD Workflow

```text
Developer
    │
    ▼
GitHub
    │
    ▼
Jenkins
    │
    ▼
Build Docker Image
    │
    ▼
Push Image to Amazon ECR
    │
    ▼
Register New Task Definition
    │
    ▼
Deploy to Amazon ECS
    │
    ▼
Application Load Balancer
    │
    ▼
Live Website
```

---

## ✨ Features

- Automatic build using GitHub Webhooks
- Automatic Docker image creation
- Push Docker images to Amazon ECR
- Automatic deployment to Amazon ECS Fargate
- Rolling deployment using ECS
- Automatic Docker cleanup after every pipeline execution

---

## 📂 Project Structure

```text
📁 Project
├── Dockerfile
├── Jenkinsfile
├── index.html
└── README.md
```

---

## 👨‍💻 Author

**Rahul K**

- GitHub: https://github.com/Rahul-693
- LinkedIn: https://www.linkedin.com/in/rahul-kumaresan-a278a6258
