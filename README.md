# Project 9: GitOps Monitoring

## Overview

GitOps workflow implementation with ArgoCD on AWS EKS. Prometheus and Grafana monitoring stack deployed via Helm charts.

## Technologies

- AWS EKS - Managed Kubernetes cluster in eu-west-2
- Terraform - Infrastructure as Code
- ArgoCD - GitOps continuous deployment
- Prometheus - Metrics collection
- Grafana - Visualisation dashboards
- Helm - Package management

## Architecture

- GitOps Pattern: Git repository monitored by ArgoCD for automatic deployments
- Monitoring Stack: Prometheus scrapes metrics, Grafana provides dashboards
- Self-Healing: ArgoCD ensures cluster state matches Git repository
- Declarative Configuration: All resources defined in manifests

## Implementation

### ArgoCD Configuration
- Monitors Git repository for changes
- Syncs applications automatically
- Manages both application and monitoring deployments

### Monitoring Setup
- Prometheus server collects cluster metrics
- Grafana dashboards for visualisation
- Pre-configured dashboards for cluster and namespace views

### Troubleshooting
- Resolved Prometheus CRD deployment issues using ServerSideApply
- Fixed DNS resolution for EKS endpoint
- Configured Terraform module defaults for public endpoint access

## Screenshots

1. ArgoCD dashboard showing applications synced and healthy
2. ArgoCD monitoring application details with Prometheus/Grafana components
3. ArgoCD webapp application showing deployed resources
4. Grafana cluster dashboard with CPU and memory metrics
5. Grafana namespace view showing pod resource usage
6. Deployed web application
7. Monitoring stack pods running
8. AWS EKS cluster in console

## Project Structure

```
Project-9-GitOps-Monitoring/
├── terraform/
│   └── main.tf           # EKS infrastructure
├── manifests/
│   ├── webapp.yaml       # Application deployment
│   └── monitoring.yaml   # ArgoCD application for monitoring
├── argocd/
│   └── applications.yaml # ArgoCD application definitions
└── screenshots/          # Documentation images
```

## Deployment Process

1. Terraform provisions EKS cluster
2. ArgoCD installed on cluster
3. ArgoCD applications configured to monitor Git repository
4. Changes to manifests trigger automatic deployments
5. Prometheus and Grafana deployed via Helm through ArgoCD

## Features

- Automated deployments from Git commits
- Cluster metrics collection
- Dashboard visualisation
- Application health monitoring
- Git-based rollback capability