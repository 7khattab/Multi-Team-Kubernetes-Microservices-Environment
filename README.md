# Multi-Team Kubernetes Microservices Environment

## 🔢 Project Overview

This project demonstrates a structured, secure, and automated multi-team environment on a shared Kubernetes cluster. It simulates two teams (Team A and Team B) working in isolated namespaces with independent microservices, CI/CD pipelines.

---

## 📂 Repository Structure

```bash
multiTeam-in-K8S/
├── .github/
│   └── workflows/
│       ├── team-a-ci-cd.yaml         # CI/CD pipeline for Team A
│       └── team-b-ci-cd.yaml         # CI/CD pipeline for Team B
├── kubernetes-config/
│   ├── namespaces/                   # Namespace definitions
│   ├── rbac/                         # Role-based access control configs
│   ├── resource-quotas/              # CPU/Memory quotas per namespace
│   └── network-policies/             # Pod-to-pod communication restrictions
├── team-a/
│   ├── src/                          # Microservice source code
│   ├── Dockerfile                   # Container image definition
│   └── k8s/                         # Kubernetes manifests
└── team-b/
    ├── src/
    ├── Dockerfile
    └── k8s/
```

---

## 🚀 Key Features

### 🏙️ Namespaces

Each team has a dedicated Kubernetes namespace (`team-a`, `team-b`) to isolate workloads, resources, and network boundaries.

### 🔐 RBAC (Role-Based Access Control)

Granular access control per team using `Roles` and `RoleBindings` to ensure secure access to only allowed namespaces.

### 🌡️ Resource Quotas

Defines memory/CPU limits per namespace to avoid noisy neighbor problems.

### 🛋️ Network Policies

Restricts pod-to-pod traffic between teams for network-level isolation.

### ⚙️ CI/CD Pipelines

Using GitHub Actions, each team has their own pipeline for automated build, test, image push to DockerHub, and Kubernetes deployment.

---

## 📊 CI/CD Workflow (Team A & Team B)

* Trigger: Push to `main` under `team-a/` or `team-b/`
* Actions:

  1. Checkout source code
  2. Build Docker image
  3. Authenticate to DockerHub using GitHub Secret
  4. Push image
  5. Apply Kubernetes manifests:

     * Namespace creation
     * RBAC
     * Quotas
     * Network policies
     * Deploy app and service

---

## 🔒 Security & Best Practices

* Namespaces + RBAC = team isolation
* Secrets managed via GitHub + Kubernetes
* Limited resources per namespace to prevent overuse


