# Sample MERN with Microservices



For `helloService`, create `.env` file with the content:
```bash
PORT=3001
```

For `profileService`, create `.env` file with the content:
```bash
PORT=3002
MONGO_URL="specifyYourMongoURLHereWithDatabaseNameInTheEnd"
```

Finally install packages in both the services by running the command `npm install`.

<br/>
For frontend, you have to install and start the frontend server:

```bash
cd frontend
npm install
npm start
```

Note: This will run the frontend in the development server. To run in production, build the application by running the command `npm run build`

# Authenticate Docker with AWS ECR
aws ecr get-login-password --region ca-central-1 | docker login --username AWS --password-stdin 975050024946.dkr.ecr.ca-central-1.amazonaws.com

# Tag Docker images for ECR
docker tag mern-backend 7982222472.dkr.ecr.ca-central-1.amazonaws.com/mern-backend
docker tag mern-frontend 7982222472.dkr.ecr.ca-central-1.amazonaws.com/mern-frontend

# Push images to ECR
docker push 7982222472.dkr.ecr.ca-central-1.amazonaws.com/mern-frontend
Absolutely, Ravindra! Here's your updated and polished `README.md` incorporating your initial ECR setup, with a clear architecture diagram, CI/CD flow, and onboarding-friendly structure. It’s designed for clarity, team enablement, and stakeholder presentation.

---

# 🚀 MERN Stack Deployment on AWS with CI/CD, EKS, and Infrastructure as Code

This project demonstrates a full-scale deployment of a containerized MERN (MongoDB, Express, React, Node.js) application on AWS using Docker, ECR, EC2, CodeCommit, Jenkins, Boto3, Lambda, and EKS. It includes infrastructure automation, CI/CD pipelines, monitoring, and documentation — ideal for real-world QA automation and DevOps enablement.

---

## 📦 Initial Setup (Executed)

```bash
# Authenticate Docker with AWS ECR
aws ecr get-login-password --region ca-central-1 | docker login --username AWS --password-stdin 975050024946.dkr.ecr.ca-central-1.amazonaws.com

# Tag Docker images for ECR
docker tag mern-backend 7982222472.dkr.ecr.ca-central-1.amazonaws.com/mern-backend
docker tag mern-frontend 7982222472.dkr.ecr.ca-central-1.amazonaws.com/mern-frontend

# Push images to ECR
docker push 7982222472.dkr.ecr.ca-central-1.amazonaws.com/mern-frontend
```

---

## 🧰 Project Workflow Overview

### 🔧 Step 1: AWS Environment Setup
- Install and configure AWS CLI.
- Install Python and Boto3:
  ```bash
  pip install boto3
  aws configure
  ```

---

### 🐳 Step 2: Containerize MERN Application
- Create `Dockerfile` for both frontend and backend.
- Build and tag Docker images.
- Create ECR repositories and push images.

---

### 📁 Step 3: Version Control with CodeCommit
- Create a CodeCommit repository.
- Push MERN source code:
  ```bash
  git remote add origin <CodeCommit-URL>
  git push -u origin main
  ```

---

### 🔄 Step 4: CI/CD with Jenkins
- Launch EC2 and install Jenkins.
- Install plugins: Git, Docker, AWS CLI, Pipeline.
- Create Jenkins jobs:
  - Build and push Docker images to ECR.
  - Trigger builds on CodeCommit commits.

---

### 🏗️ Step 5: Infrastructure as Code with Boto3
- Use Python scripts to define:
  - VPC, subnets, security groups.
  - Auto Scaling Group (ASG) for backend.
  - Lambda functions for automation.

---

### 🚀 Step 6: Deploy Backend Services
- Launch EC2 instances in ASG.
- Pull backend image from ECR and run container.

---

### 🌐 Step 7: Networking Setup
- Create Elastic Load Balancer (ELB) for backend.
- Configure Route 53 DNS for domain mapping.

---

### 🎨 Step 8: Deploy Frontend Services
- Launch EC2 instances for frontend.
- Pull frontend image from ECR and run container.

---

### 🧠 Step 9: AWS Lambda Functions
- Create Lambda functions using Boto3.
- Automate DB backups to S3 with timestamped filenames.

---

### ☸️ Step 10: Kubernetes Deployment (EKS)
- Create EKS cluster using `eksctl`:
  ```bash
  eksctl create cluster --name mern-cluster --region ca-central-1
  ```
- Use Helm to deploy:
  ```bash
  helm install mern-app ./helm-chart
  ```

---

### 📊 Step 11: Monitoring and Logging
- Use CloudWatch for:
  - Metrics and alarms.
  - Centralized logging via CloudWatch Logs.

---

### 📚 Step 12: Documentation
- Document architecture using diagrams and markdown.
- Include:
  - AWS resource map.
  - CI/CD flow.
  - Deployment steps.
  - Troubleshooting tips.
- Host documentation in this GitHub repo.

---

## 🧭 Architecture Diagram

```plaintext
[CodeCommit] → [Jenkins CI] → [Docker + ECR] → [EC2 + ASG] → [ELB] → [Route 53]
                             ↘ [Lambda + S3] ↘ [EKS + Helm]
```

---

## 🔁 CI/CD Flow

```plaintext
[Code Commit] → [Jenkins Build Job]
     ↓
[Docker Build] → [Push to ECR]
     ↓
[EC2 Pull + Deploy] → [ASG + ELB]

