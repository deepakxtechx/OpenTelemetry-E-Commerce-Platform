# OpenTelemetry-E-Commerce-Platform

A production-grade, polyglot microservices e-commerce platform deployed on **AWS EKS** using **Terraform**, **GitHub Actions CI**, **ArgoCD GitOps**, **Docker**, **Helm**, **Prometheus**, **Grafana**, and **OpenTelemetry** for full-stack observability.

This project replicates real-world cloud architecture with automated build pipelines, infrastructure-as-code, GitOps delivery, distributed tracing, metrics collection, and multi-service orchestration.

---

# 1. Implementation Video & Architecture

### **Implementation Video**
[(Add your 3-minute demo link here)](https://github.com/deepakxtechx/OpenTelemetry-E-Commerce-Platform/issues/4#issue-3722367746)

### **Architecture Diagrams**
- CI/CD + GitOps + Terraform/EKS Workflow  
- Full Microservices Communication Diagram  

(Insert PNG/SVG diagrams here)

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
- **Helm charts** for each microservice
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
```
- Checkout repository
- Setup Go 1.22
- Build product catalog binary:
  cd src/product-catalog && go build -o product-catalog-service main.go
```

### Unit Tests
```
cd src/
go test ./...
```

### Static Code Analysis (SCA) + Lint
```
golangci-lint run
```

### Docker Build & Push
- Build Docker image  
- Tag with `${{ github.run_id }}`
- Push to Docker Hub

### Kubernetes Manifest Update
```
sed -i "s|image: .*|image: <new image tag>|" kubernetes/productcatalog/deploy.yaml
```

### Auto Commit & Push
The updated manifest is pushed back to the **main branch**, triggering ArgoCD.

---

## 3. Terraform Provisioning

Terraform provisions cloud infrastructure:

- VPC  
- EKS cluster  
- Node groups  
- IAM roles & OIDC  
- Security groups  

All resources are fully reproducible and version-controlled.

---

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

- Envoy proxy routes traffi
- nginx controller  
- Singel source of truth from github repository
- Services scale using Kubernetes primitives    

---

## 6. Observability

### Prometheus
- Scrapes metrics from all microservices  
- Includes Kubernetes node, pod, and cluster monitoring  

### Grafana
- Dashboards for latency, throughput, saturation, error rates  
- Visualizes service-level performance  

### OpenTelemetry
- Captures distributed traces  
- Correlates events across 20+ microservices  
- Enables root-cause analysis of failures

---

# 6. Repository Structure

```
├── .github
│   └── workflows
├── internal
│   └── tools
├── kubernetes
│   ├── accounting
│   ├── ad
│   ├── cart
│   ├── checkout
│   ├── currency
│   ├── email
│   ├── flagd
│   ├── frauddetection
│   ├── frontend
│   ├── frontendproxy
│   ├── imageprovider
│   ├── kafka
│   ├── loadgenerator
│   ├── payment
│   ├── productcatalog
│   ├── quote
│   ├── recommendation
│   ├── shipping
│   └── valkey
├── pb
├── src
│   ├── accounting
│   ├── ad
│   ├── cart
│   ├── checkout
│   ├── currency
│   ├── email
│   ├── flagd
│   ├── flagd-ui
│   ├── fraud-detection
│   ├── frontend
│   ├── frontend-proxy
│   ├── grafana
│   ├── image-provider
│   ├── kafka
│   ├── load-generator
│   ├── opensearch
│   ├── otel-collector
│   ├── payment
│   ├── postgres
│   ├── product-catalog
│   ├── prometheus
│   ├── quote
│   ├── react-native-app
│   ├── recommendation
│   └── shipping
└── test
    └── tracetesting
```

This structure reflects a real polyglot microservices monorepo.

---

# 7. Challenges & Solutions

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

# 8. Conclusion

This project demonstrates a modern, production-grade DevOps stack, integrating:

- **Infrastructure-as-Code** (Terraform)  
- **CI Pipeline** (GitHub Actions)  
- **GitOps Deployment** (ArgoCD)  
- **Container Orchestration** (EKS)  
- **Observability** (Prometheus, Grafana, OpenTelemetry)  
- **Distributed Microservices**

It validates real-world skills expected from **DevOps, Cloud, SRE, and Platform Engineers**, including automation, scalability, reliability, and deep observability.

