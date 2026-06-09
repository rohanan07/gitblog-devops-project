# GitOps-Based Blogging Platform on AWS EKS

A production-style GitOps project built to learn and implement modern DevOps practices using AWS, Kubernetes, Terraform, ArgoCD, GitHub Actions, Helm, Prometheus, and Grafana.

The project consists of a full-stack blogging platform (React + Node.js + PostgreSQL) deployed on Amazon EKS using Helm charts and managed through a GitOps workflow.

---

## Project Overview

The primary goal of this project was not just to deploy an application, but to understand and implement the complete lifecycle of a cloud-native application:

* Infrastructure provisioning using Terraform
* Containerization using Docker
* Kubernetes deployment using Helm
* GitOps workflow using ArgoCD
* CI/CD automation using GitHub Actions
* Monitoring using Prometheus and Grafana
* Managed database using Amazon RDS

Before deploying to AWS, the application was first deployed on a local Kubernetes cluster using Kind to validate Kubernetes manifests, networking, ingress, ConfigMaps, Secrets, and application behavior.

---

## Tech Stack

### Cloud & Infrastructure

* AWS EKS
* AWS ECR
* AWS RDS PostgreSQL
* AWS VPC
* AWS Application Load Balancer
* AWS IAM

### DevOps & Automation

* Terraform
* Docker
* Kubernetes
* Helm
* ArgoCD
* GitHub Actions

### Monitoring

* Prometheus
* Grafana

### Application

* React
* Node.js
* Express.js
* PostgreSQL
* JWT Authentication

---

## Repository Structure

This project is organized into multiple repositories following real-world separation of concerns.

### Application Repository

Contains frontend and backend application code.

Repository:
https://github.com/rohanan07/gitblog-complete-app.git

Contents:

* React Frontend
* Node.js Backend
* Dockerfiles
* Docker Compose
* JWT Authentication
* Blog CRUD APIs

---

### Infrastructure Repository

Contains Terraform code used to provision AWS infrastructure.

Repository:
https://github.com/rohanan07/Gitblog-Infra-TF.git

Resources Provisioned:

* VPC
* Public Subnets
* Private Subnets
* NAT Gateway
* Internet Gateway
* EKS Cluster
* EKS Managed Node Groups
* ECR Repositories
* PostgreSQL RDS

---

### GitOps Repository

Contains Helm Charts, ArgoCD Applications and deployment manifests.

Repository:
https://github.com/rohanan07/Gitblog-Gitops-Repo.git

Contents:

* Helm Charts
* ArgoCD Applications
* Kubernetes Jobs
* Deployment Configuration
* Environment Specific Values

---

## Architecture

```text
Developer
    |
    v
Git Push
    |
    v
GitHub Actions
    |
    v
Build Docker Images
    |
    v
Amazon ECR
    |
    v
Update GitOps Repository
    |
    v
ArgoCD
    |
    v
Amazon EKS
    |
    +-------------------+
    |                   |
    v                   v
Frontend Pods      Backend Pods
                          |
                          |
                          v
                    Amazon RDS

Monitoring Stack
----------------
Prometheus
Grafana

Traffic Flow
------------
Internet
   |
   v
Application Load Balancer
   |
   v
Ingress
   |
   v
Services
   |
   v
Pods
```

---

## Features

### Application Features

* User Registration
* User Login
* JWT Authentication
* Create Blog Posts
* View Blog Posts
* Delete Blog Posts

### DevOps Features

* Infrastructure as Code using Terraform
* Dockerized Frontend and Backend
* Kubernetes Deployments
* Helm Chart Packaging
* Automated Database Initialization using Kubernetes Jobs
* GitOps Deployment using ArgoCD
* CI/CD using GitHub Actions
* Monitoring using Prometheus and Grafana

---

## Kubernetes Resources Used

* Namespace
* Deployments
* Services
* ConfigMaps
* Secrets
* Ingress
* Jobs
* Persistent Volume Claims

---

## AWS Resources Used

* Amazon EKS
* Amazon ECR
* Amazon RDS PostgreSQL
* Amazon VPC
* Application Load Balancer
* IAM Roles
* Security Groups
* Public & Private Subnets
* NAT Gateway

---

## Key Learnings

### Kubernetes

* Deployments
* Services
* Ingress
* ConfigMaps
* Secrets
* Networking
* Service Discovery
* Kubernetes Jobs

### Helm

* Creating Helm Charts
* Helm Templates
* values.yaml
* Helm Releases
* Helm Upgrades
* Environment Specific Configuration

### Terraform

* Infrastructure as Code
* Terraform Modules
* Remote State Management
* AWS Networking
* EKS Provisioning
* RDS Provisioning

### AWS

* VPC Architecture
* Public vs Private Subnets
* EKS Managed Node Groups
* RDS Networking
* ALB Ingress Controller
* IAM Roles for Kubernetes

### GitOps

* ArgoCD
* Declarative Deployments
* Continuous Reconciliation
* Git as Source of Truth

---

## Challenges Faced

### Database Schema Initialization

The application worked locally but failed on Kubernetes because PostgreSQL tables were manually created in the local environment and were missing in Kubernetes.

Solution:

* Created a Kubernetes Job to initialize the database schema automatically before application startup.

### RDS Connectivity Issues

Faced issues related to:

* DNS resolution
* SSL configuration
* Authentication
* Security group access

Resolved by validating networking layer by layer and updating application configuration.

### Helm Migration

Converted raw Kubernetes manifests into reusable Helm Charts using templates and values files.

---

## Monitoring

The cluster and application are monitored using:

### Prometheus

* Cluster Metrics
* Pod Metrics
* Resource Utilization

### Grafana

* Kubernetes Dashboards
* Application Monitoring
* Resource Visualization

---

## Future Improvements

* HTTPS using ACM Certificates
* External Secrets Operator
* AWS Secrets Manager Integration
* Multi-Environment Deployment (Dev/Stage/Prod)
* Horizontal Pod Autoscaler
* Blue-Green Deployments
* Centralized Logging using Loki/ELK

---

## Screenshots

---

---

## Author

Rohan Nalawade

LinkedIn:
https://www.linkedin.com/in/rohan-nalawade-6b5a42255/

GitHub:
https://github.com/rohanan07
