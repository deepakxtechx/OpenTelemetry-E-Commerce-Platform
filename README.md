# OpenTelemetry-E-Commerce-Platform

A production-grade, polyglot microservices e-commerce platform deployed on **AWS EKS** using **Terraform**, **GitHub Actions CI**, **ArgoCD GitOps**, **Docker**, **Helm**, **Prometheus**, **Grafana**, and **OpenTelemetry** for full-stack observability.

This project replicates real-world cloud architecture with automated build pipelines, infrastructure-as-code, GitOps delivery, distributed tracing, metrics collection, and multi-service orchestration.

---

# 1. Implementation Video & Architecture

### **Implementation Video**
https://github.com/user-attachments/assets/994e1257-1a3b-4f81-9282-74a60f29ac63

### **Architecture Diagrams**
<img width="1572" height="839" alt="Opentelemetry drawio (1)" src="https://github.com/user-attachments/assets/5684b8fc-8d8b-4813-85fa-33eace059c7e" />


---

# 2. Problem This Platform Solves

This platform demonstrates how modern engineering teams solve critical DevOps and SRE challenges:

- Automated and repeatable **infrastructure provisioning**
- Secure and deterministic **container image builds**
- Continuous delivery with automated **Kubernetes manifest updates**
- Support for **polyglot microservices**
- Full observability stack (metrics, logs, traces)
- GitOps-driven consistency and reliability

It mirrors real e-commerce system architecture used by large-scale production systems.

---

# 3. Features & Capabilities

## Platform Capabilities

- **AWS EKS** cluster fully provisioned via **Terraform**
- **End-to-end CI pipeline**  
  Build → Test → Lint → SCA → Docker Build → Push → Manifest Update
- **ArgoCD GitOps** for automated, stable deployments
- **Prometheus + Grafana** monitoring stack
- **OpenTelemetry** distributed tracing
- Polyglot microservices written in:
  - Go  
  - Java  
  - Python  
  - Node.js  
  - Kotlin  
  - C#  
  - Rust  
  - TypeScript  
  - React Native  
- Envoy-based **frontend proxy** and production routing
- Realistic enterprise-level microservice communication

---

# 4. Microservices Overview

### Core Commerce Services
- Product Catalog  
- Cart  
- Checkout  
- Shipping  
- Payment  
- Accounting  
- Fraud Detection  
- Currency  
- Recommendation  
- Quote  
- Email  
- Ads  

---

# 5. End-to-End Workflow  
(From Git → Build → Deploy → Observe)

## 1. Developer Pushes Code → GitHub  
Triggers GitHub Actions CI Pipeline.

---

## 2. GitHub Actions CI Pipeline

### Build Stage

### Unit Tests

### Static Code Analysis (SCA) + Lint

### Docker Build & Push

### Kubernetes Manifest Update

### Auto Commit & Push


## 3. Terraform Provisioning

Terraform provisions cloud infrastructure:

- VPC  
- EKS cluster  
- Node groups  
- IAM roles & OIDC  
- Security groups  

## 4. GitOps with ArgoCD

ArgoCD continuously:

- Watches the Git repository  
- Pulls Helm charts & manifests  
- Applies updates safely  
- Ensures **desired state = live state**  
- Performs automatic rollouts and health checks  

---

## 5. Kubernetes Runtime

Inside EKS:

- Envoy proxy routes traffic
- nginx controller  
- Singel source of truth from github repository
- Services scale using Kubernetes primitives    

---

## 6. Observability

### Prometheus
- Scrapes metrics from Cluster
- Includes Kubernetes node, pod, and cluster monitoring  

### Grafana
- Dashboards for latency, throughput, saturation, error rates  
- Visualizes service-level performance  

### OpenTelemetry
- Captures distributed traces  
- Correlates events across 20+ microservices  
- Enables root-cause analysis of failures
---

# 6. Challenges & Solutions

### 1. EKS OIDC Role Mismatch  
**Issue:** Service accounts could not assume IAM roles.  
**Solution:** Corrected OIDC provider, updated trust policies, and reconfigured Terraform IAM module.

### 2. ArgoCD Auto-Sync Failure  
**Issue:** Helm CRDs applied out-of-order.  
**Solution:** Added sync waves, pinned Helm chart version.

### 3. Docker Hub Rate Limiting  
**Issue:** Image pulls failed during CI.  
**Solution:** Implemented authenticated pulls & caching.



---

# 7. Conclusion

This project demonstrates a modern, production-grade DevOps stack, integrating:

- **Infrastructure-as-Code** (Terraform)  
- **CI Pipeline** (GitHub Actions)  
- **GitOps Deployment** (ArgoCD)  
- **Container Orchestration** (EKS)  
- **Observability** (Prometheus, Grafana, OpenTelemetry)  
- **Distributed Microservices**

It validates real-world skills expected from **DevOps, Cloud, SRE, and Platform Engineers**, including automation, scalability, reliability, and deep observability.

