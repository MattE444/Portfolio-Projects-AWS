# Deploy Kubernetes Cluster using EKS and Dockerized Apps

## Introduction
This project demonstrates how to deploy a Dockerized application to a managed Kubernetes cluster using Amazon EKS. The solution follows AWS best practices for container orchestration, image management, scalability, and security.
The very simple application is containerized with Docker, stored in Amazon Elastic Container Registry (ECR), and deployed to Amazon Elastic Kubernetes Service (EKS) using Kubernetes manifests.

## AWS Services used
- Amazon EKS
- Amazon ECR
- IAM
- VPC

## Steps to complete:
1. Cluster Provisioning: The EKS cluster is created using eksctl, which automates:
    - VPC creation
    - IAM role setup
    - Worker node provisioning
    - kubectl configuration
    > eksctl create cluster \
      --name my-eks-cluster \
      --region us-east-2 \
      --nodegroup-name linux-nodes \
      --node-type t3.medium \
      --nodes 2 \
      --managed

2. Containerization & Image Management
   - Dockerfile:
    > FROM node:18-alpine  
    > WORKDIR /app  
    > COPY package*.json ./  
    > RUN npm install  
    > COPY . .  
    > EXPOSE 3000  
    > CMD ["npm", "start"]  

3. Build & Push to ECR  
    > docker build -t my-app .  
    > docker tag my-app:latest <ACCOUNT_ID>.dkr.ecr.us-east-2.amazonaws.com/my-app:latest  
    > docker push <ACCOUNT_ID>.dkr.ecr.us-east-2.amazonaws.com/my-app:latest  

4. Kubernetes Deployment
   > apiVersion: apps/v1  
kind: Deployment  
metadata:  
  name: my-app  
spec:  
  replicas: 2  
  selector:  
    matchLabels:  
      app: my-app  
  template:  
    metadata:  
      labels:  
        app: my-app  
    spec:  
      containers:  
      - name: my-app  
        image: <ACCOUNT_ID>.dkr.ecr.us-east-2.amazonaws.com/my-app:latest  
        ports:  
        - containerPort: 3000  



## Issues
No issues but slow going as I continually rechecked myself and made sure I understood what I was doing.
