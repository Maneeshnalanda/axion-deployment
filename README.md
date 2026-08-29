AXION Intelligence Platform 🚀

An Industrial IoT & AI-Powered Asset Monitoring Platform built using Microservices, Kubernetes, Azure Cloud and DevOps practices.

AXION is a modern Industrial Intelligence Platform designed to monitor industrial assets, collect real-time telemetry data, detect anomalies, and provide intelligent insights through a centralized dashboard.

The platform follows a Microservices Architecture and is designed for cloud-native deployment using Docker, Kubernetes (AKS), Azure Container Registry, Azure Application Gateway and Infrastructure Automation.

![alt text](axion-app.JPG)

📌 Project Overview

AXION simulates and monitors industrial equipment such as:

Compressors
Motors
Pumps
Industrial Sensors
Telemetry Devices

The platform continuously processes telemetry metrics such as:

🌡️ Temperature
📈 Vibration
⚡ Current
🔄 Asset Status
🚨 Anomaly Events

The collected data is processed through backend services and displayed on the AXION Intelligence Dashboard.

🏗️ Architecture
                    ┌─────────────────────┐
                    │    AXION UI         │
                    │   React Dashboard   │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │ Azure Application  │
                    │ Gateway / Ingress  │
                    └──────────┬──────────┘
                               │
            ┌──────────────────┼──────────────────┐
            │                  │                  │
            ▼                  ▼                  ▼
    ┌──────────────┐   ┌──────────────┐   ┌──────────────┐
    │  Ingestion   │   │ Telemetry    │   │  Simulator   │
    │   Service    │   │ Query Service│   │   Service    │
    └──────┬───────┘   └──────┬───────┘   └──────────────┘
           │                  │
           └─────────┬────────┘
                     │
                     ▼
              ┌──────────────┐
              │ PostgreSQL   │
              │  Database    │
              └──────────────┘
🔥 Microservices Architecture

The AXION platform consists of multiple independent repositories and services.

1️⃣ AXION UI

Repository: axion-ui

The frontend application provides a centralized dashboard for monitoring industrial assets.

Features
Asset hierarchy
Real-time telemetry monitoring
Temperature monitoring
Vibration monitoring
Current monitoring
Asset diagnostics
Digital Twin visualization
Live anomaly monitoring
Industrial intelligence dashboard
Technology
React
TypeScript
Vite
REST APIs
Nginx
Docker
2️⃣ AXION Data Simulator

Repository: axion-data-simulator

This service simulates industrial telemetry data and continuously sends data to the ingestion service.

Simulated Metrics
Temperature
Vibration
Current
Asset Health
Anomaly Events
Example Flow
Simulator
    │
    │ Telemetry Data
    ▼
Ingestion Service
3️⃣ AXION Ingestion Service

Repository: axion-ingestion-service

The ingestion service receives telemetry data from industrial devices and simulators.

Responsibilities
Receive telemetry data
Validate incoming data
Detect anomalies
Store telemetry in PostgreSQL
Provide ingestion APIs
Example API
POST /api/v1/telemetry/ingest
4️⃣ AXION Telemetry Query Service

Repository: axion-telemetry-query-service

This service provides APIs for retrieving telemetry and historical data.

Features
Historical telemetry queries
Asset telemetry data
Time-series analysis
Dashboard API integration
Asset diagnostics
🗄️ Database

AXION uses PostgreSQL as the primary database.

The database stores:

Asset Information
Telemetry Data
Historical Metrics
Anomaly Events
Device Information

Example architecture:

Microservices
      │
      ▼
PostgreSQL
      │
      ▼
Persistent Volume
☁️ Kubernetes Architecture

All AXION services are deployed on Kubernetes.

AXION Namespace
│
├── UI Deployment
│
├── Ingestion Deployment
│
├── Telemetry Query Deployment
│
├── Simulator Deployment
│
└── PostgreSQL Stateful Service

Each service contains:

Deployment
Service
ConfigMap
Secret
Ingress
Persistent Volume
☁️ Azure Architecture

The platform is designed for deployment on Microsoft Azure.

Azure Services
Service	Purpose
Azure Kubernetes Service	Container orchestration
Azure Container Registry	Docker image storage
Azure Application Gateway	Application routing
Azure DNS	Domain management
Azure Managed Identity	Secure Azure authentication
Azure Storage	Infrastructure storage
Azure Monitor	Monitoring and observability
🐳 Containerization

Each microservice is containerized using Docker.

Source Code
     │
     ▼
Dockerfile
     │
     ▼
Docker Image
     │
     ▼
Azure Container Registry
     │
     ▼
Azure Kubernetes Service

Example:

docker build -t axion-ui:v1 .

docker tag axion-ui:v1 <ACR_NAME>.azurecr.io/axion-ui:v1

docker push <ACR_NAME>.azurecr.io/axion-ui:v1
☸️ Kubernetes Deployment

Example workflow:

kubectl apply -f manifests/

Check pods:

kubectl get pods -n axion-app

Check services:

kubectl get svc -n axion-app

Check ingress:

kubectl get ingress -n axion-app
🔐 Configuration Management

Sensitive information is managed using Kubernetes Secrets.

Example:

Database Username
Database Password
API Keys
Connection Strings

Application configuration is managed using:

Environment Variables
ConfigMaps
Kubernetes Secrets
🌐 Application Flow
Industrial Device
       │
       ▼
Data Simulator
       │
       ▼
Ingestion Service
       │
       ▼
PostgreSQL Database
       │
       ▼
Telemetry Query Service
       │
       ▼
AXION UI Dashboard
🚀 DevOps Workflow

The project follows a modern DevOps lifecycle.

Developer
    │
    ▼
GitHub
    │
    ▼
CI Pipeline
    │
    ├── Code Quality
    ├── Security Scan
    ├── Docker Build
    │
    ▼
Azure Container Registry
    │
    ▼
Kubernetes Deployment
    │
    ▼
AXION Platform
🔄 CI/CD Pipeline

Recommended CI/CD stages:

1. Source Code Checkout

2. Dependency Installation

3. Code Quality Scan

4. Security Scan

5. Docker Image Build

6. Docker Image Push

7. Kubernetes Deployment

8. Health Check
🛠️ Technology Stack
Cloud
Microsoft Azure
Azure Kubernetes Service
Azure Container Registry
Application Gateway
Azure DNS
Containers & Orchestration
Docker
Kubernetes
AKS
DevOps
GitHub
GitHub Actions
Azure DevOps
Terraform
Backend
Python
FastAPI
REST APIs
Frontend
React
TypeScript
Vite
Database
PostgreSQL
📊 Monitoring & Observability

The platform can be extended with:

Prometheus
Grafana
Azure Monitor
Application Insights

For production environments, monitoring can provide visibility into:

Pod health
CPU utilization
Memory utilization
API response time
Database performance
Application errors
Telemetry processing
📁 Project Structure
AXION Platform
│
├── axion-ui
│
├── axion-data-simulator
│
├── axion-ingestion-service
│
├── axion-telemetry-query-service
│
└── kubernetes-manifests
    │
    ├── database
    │
    ├── ingestion
    │
    ├── telemetry-query
    │
    ├── simulator
    │
    ├── ui
    │
    └── ingress
🔐 Security Practices

The project follows DevOps security best practices.

Kubernetes Secrets for sensitive data
Environment-based configuration
Containerized workloads
Azure Managed Identity
Role-Based Access Control
Private service communication
Container image security scanning
🚧 Future Enhancements

Planned improvements:

 CI/CD automation
 GitOps using ArgoCD
 Prometheus monitoring
 Grafana dashboards
 Centralized logging
 AI-based anomaly detection
 Horizontal Pod Autoscaling
 Blue-Green Deployment
 Infrastructure as Code using Terraform
 Azure Key Vault integration
🖥️ AXION Dashboard

The AXION Intelligence Platform provides a modern industrial dashboard with:

✔ Asset Hierarchy
✔ Live Telemetry
✔ Digital Twin Visualization
✔ Temperature Monitoring
✔ Vibration Monitoring
✔ Current Monitoring
✔ Asset Diagnostics
✔ Live Camera Monitoring
✔ AI Assistant Integration
👨‍💻 Author

Bhawani Bid

DevOps | Azure | Kubernetes | Terraform | Cloud Automation

⭐ Support

If you like this project, please consider giving the repositories a ⭐ Star.