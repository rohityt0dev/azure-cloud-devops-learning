# 🌐 Azure App Service

## 📌 What is Azure App Service?

**Azure App Service** is a fully managed **Platform as a Service (PaaS)** offered by Microsoft Azure.

It allows you to build, deploy, and host web applications, REST APIs, and backend services without managing the underlying servers.

### Simple Example

```text
Developer
    │
    ▼
GitHub Repository
    │
    ▼
CI/CD Pipeline
    │
    ▼
Azure App Service
    │
    ▼
🌐 Web Application
```

---

# 🎯 Why Use Azure App Service?

Azure App Service is useful when you want to:

* Host web applications
* Deploy REST APIs
* Run backend applications
* Configure automatic scaling
* Enable HTTPS
* Connect applications to databases
* Deploy directly from GitHub
* Implement CI/CD
* Monitor applications
* Avoid managing operating systems and servers

---

# 🏗️ App Service Architecture

```text
                         🌐 Users
                            │
                            ▼
                     🔒 HTTPS / TLS
                            │
                            ▼
                    Azure App Service
                            │
              ┌─────────────┼─────────────┐
              ▼             ▼             ▼
          Web App         REST API      Backend
              │             │             │
              └─────────────┼─────────────┘
                            │
              ┌─────────────┴─────────────┐
              ▼                           ▼
          Azure SQL                    Storage
```

---

# 🔑 Important App Service Components

## 1. App Service App

The application that you deploy to Azure.

Examples:

* Node.js application
* Python application
* Java application
* .NET application
* PHP application
* Static web application

---

## 2. App Service Plan

An **App Service Plan** defines the compute resources used by your App Service applications.

It determines:

* Region
* Operating system
* VM size
* Number of instances
* Pricing tier
* Scaling capabilities

### Example

```text
App Service Plan
       │
       ├── Web App 1
       ├── Web App 2
       └── API App
```

Multiple apps can share the same App Service Plan.

---

# 💰 App Service Pricing Tiers

Azure App Service provides different pricing tiers.

Common categories include:

```text
Free
Shared
Basic
Standard
Premium
Isolated
```

Higher tiers generally provide more features, resources, scaling, and networking capabilities.

> Always check current Azure pricing and feature availability before deploying production workloads.

---

# 🚀 Create App Service Using Azure Portal

## Step 1 — Open Azure Portal

Search for:

```text
App Services
```

Select:

```text
Create → Web App
```

---

## Step 2 — Select Subscription

Choose your Azure subscription.

Example:

```text
Subscription:
Azure Subscription
```

---

## Step 3 — Create Resource Group

Example:

```text
Resource Group:
rg-appservice-demo
```

---

## Step 4 — Enter Application Name

Example:

```text
Name:
rohit-demo-webapp
```

The name must be globally unique because it becomes part of the default application hostname.

---

# 🖥️ Step 5 — Select Deployment Options

Select:

```text
Publish:
Code
```

or an appropriate container-based deployment option if your application is containerized.

---

# 💻 Step 6 — Select Runtime Stack

Examples:

```text
.NET
Java
Node
Python
PHP
```

Choose the runtime required by your application.

---

# 🌍 Step 7 — Select Region

Example:

```text
Region:
Central India
```

Choose a region close to your users when practical.

---

# ⚙️ Step 8 — Configure App Service Plan

Example:

```text
App Service Plan:
ASP-demo

Pricing Tier:
Basic / Standard
```

For learning, use a suitable low-cost tier available in your subscription.

---

# 🔎 Step 9 — Review + Create

Click:

```text
Review + create
```

Then:

```text
Create
```

Azure will provision your App Service.

---

# 🌐 Access the Web Application

After deployment, Azure provides a default hostname.

Example:

```text
https://<app-name>.azurewebsites.net
```

Open the hostname in a browser to access the application.

---

# 💻 Create App Service Using Azure CLI

## Login

```bash
az login
```

---

## Create Resource Group

```bash
az group create \
  --name rg-appservice-demo \
  --location centralindia
```

---

## Create App Service Plan

```bash
az appservice plan create \
  --name asp-demo \
  --resource-group rg-appservice-demo \
  --location centralindia \
  --sku B1 \
  --is-linux
```

---

## Create Web App

For example, for a Python application:

```bash
az webapp create \
  --resource-group rg-appservice-demo \
  --plan asp-demo \
  --name <unique-app-name> \
  --runtime "PYTHON:3.12"
```

> Runtime names and supported versions can change. Use `az webapp list-runtimes` to see the currently supported runtime values in your environment.

---

# 🚀 Deploy Application

Azure App Service supports several deployment methods.

### GitHub

```text
GitHub
   │
   ▼
GitHub Actions
   │
   ▼
Azure App Service
```

### ZIP Deployment

```text
Application
     │
     ▼
ZIP Package
     │
     ▼
Azure App Service
```

### Container

```text
Docker Image
     │
     ▼
Azure Container Registry
     │
     ▼
Azure App Service
```

---

# 🔄 CI/CD with GitHub Actions

App Service integrates well with GitHub Actions.

Example pipeline:

```text
Developer
    │
    ▼
Git Push
    │
    ▼
GitHub
    │
    ▼
GitHub Actions
    │
    ├── Build
    ├── Test
    └── Deploy
          │
          ▼
    Azure App Service
```

Example GitHub Actions workflow:

```yaml
name: Deploy to Azure App Service

on:
  push:
    branches:
      - main

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Build Application
        run: |
          echo "Build application"

      - name: Test Application
        run: |
          echo "Run tests"

      - name: Deploy
        run: |
          echo "Deploy to Azure App Service"
```

> A real deployment workflow should use the appropriate Azure authentication and deployment action for your application.

---

# 📈 App Service Scaling

App Service supports scaling based on application requirements.

## Scale Up

Increase the resources of the App Service Plan.

```text
Small Plan
    ↓
Larger Plan
```

This provides more CPU, memory, and other capabilities depending on the selected tier.

---

## Scale Out

Increase the number of application instances.

```text
1 Instance
     ↓
2 Instances
     ↓
4 Instances
```

Example:

```text
                 App Service
                      │
          ┌───────────┼───────────┐
          ▼           ▼           ▼
       Instance 1  Instance 2  Instance 3
```

---

# 🔄 Deployment Slots

Deployment slots allow you to deploy different versions of an application into separate environments.

Example:

```text
Production
     │
     └── v1

Staging
     │
     └── v2
```

You can test the new version in staging and then swap the slot with production.

### Blue-Green Style Deployment

```text
              Azure App Service
                     │
             ┌───────┴───────┐
             ▼               ▼
         Production        Staging
            v1               v2
             │               │
             └────── Swap ───┘
                     │
                     ▼
                 Production
                     v2
```

Deployment slots are available only in supported App Service pricing tiers.

---

# 🔐 App Service Security

Important security features include:

* HTTPS
* TLS
* Authentication and authorization
* Managed Identity
* Access restrictions
* Private endpoints
* Application settings
* Azure Key Vault integration

---

# 🔑 Application Settings

Application configuration can be stored as App Service application settings.

Example:

```text
DATABASE_URL
API_URL
ENVIRONMENT
```

Avoid hardcoding secrets inside application source code.

For sensitive secrets, consider:

```text
Azure Key Vault
       │
       ▼
Managed Identity
       │
       ▼
App Service
```

---

# 📊 Monitoring

Azure App Service can be monitored using:

* Azure Monitor
* Application Insights
* Log Analytics
* App Service logs
* Metrics
* Alerts

Important metrics include:

* CPU
* Memory
* HTTP requests
* Response time
* HTTP errors
* Availability

---

# 🧪 Hands-On Lab

## Lab: Deploy a Web Application

### Objective

Deploy a simple web application to Azure App Service and configure CI/CD.

### Tasks

* [ ] Create Resource Group
* [ ] Create App Service Plan
* [ ] Create Web App
* [ ] Deploy application
* [ ] Configure application settings
* [ ] Enable HTTPS
* [ ] Configure GitHub Actions
* [ ] Create staging slot
* [ ] Deploy new version
* [ ] Test staging
* [ ] Swap staging with production
* [ ] Enable monitoring

---

# 🆚 Azure VM vs App Service

| Feature       | Azure VM                 | App Service              |
| ------------- | ------------------------ | ------------------------ |
| Service Model | IaaS                     | PaaS                     |
| OS Management | Customer                 | Azure                    |
| Server Access | Full                     | Limited/abstracted       |
| Scaling       | More infrastructure work | Built-in scaling options |
| Deployment    | Manual/automation        | Simplified               |
| Maintenance   | Higher                   | Lower                    |
| Best For      | Custom infrastructure    | Web apps/APIs            |

---

# 🆚 App Service vs Azure Functions

| Feature        | App Service              | Azure Functions          |
| -------------- | ------------------------ | ------------------------ |
| Model          | PaaS                     | Serverless / FaaS        |
| Main Use       | Web apps & APIs          | Event-driven functions   |
| Execution      | Long-running application | Function-based execution |
| Scaling        | App Service scaling      | Function scaling         |
| Infrastructure | Azure-managed            | Azure-managed            |
| Best For       | Websites/APIs            | Event-driven workloads   |

---

# ❓ Interview Questions

### Q1. What is Azure App Service?

Azure App Service is a managed PaaS service used to host web applications, APIs, and backend applications.

### Q2. What is an App Service Plan?

An App Service Plan defines the compute resources, region, operating system, pricing tier, and scaling capabilities used by App Service apps.

### Q3. What is the difference between Scale Up and Scale Out?

**Scale Up:** Increase resources of the existing App Service Plan.

**Scale Out:** Increase the number of application instances.

### Q4. What are deployment slots?

Deployment slots provide separate environments such as staging and production so application versions can be tested and swapped with reduced deployment risk.

### Q5. Can App Service integrate with GitHub?

Yes. Azure App Service can integrate with GitHub and GitHub Actions for CI/CD.

### Q6. Is Azure App Service IaaS or PaaS?

Azure App Service is a **PaaS** service.

### Q7. How do you store application secrets?

Use secure mechanisms such as Azure Key Vault and managed identities rather than hardcoding secrets.

### Q8. How can you monitor App Service?

Use Azure Monitor, Application Insights, Log Analytics, metrics, logs, and alerts.

---

# 📝 Key Takeaways

```text
Azure App Service
       │
       ├── PaaS
       ├── Web Applications
       ├── REST APIs
       ├── App Service Plan
       ├── Scale Up
       ├── Scale Out
       ├── Deployment Slots
       ├── CI/CD
       ├── HTTPS
       ├── Managed Identity
       └── Monitoring
```

> **App Service = Managed platform for hosting web applications and APIs without managing the underlying servers.**
