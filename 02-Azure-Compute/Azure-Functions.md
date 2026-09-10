# ⚡ Azure Functions

## 📌 What is Azure Functions?

**Azure Functions** is a serverless compute service from Microsoft Azure that allows you to run small pieces of code in response to events without managing servers.

You write the function, define a trigger, and Azure manages the underlying infrastructure and scaling.

### Simple Example

```text
Event
  │
  ▼
Trigger
  │
  ▼
Azure Function
  │
  ▼
Execute Code
  │
  ▼
Result
```

---

# 🎯 Why Use Azure Functions?

Azure Functions is useful for:

* Event-driven applications
* Serverless APIs
* Automation
* Scheduled jobs
* File processing
* Background tasks
* Data processing
* Notifications
* Integration workflows

---

# 🏗️ Azure Functions Architecture

```text
             🌐 Client
                 │
                 ▼
          ⚡ Azure Function
                 │
        ┌────────┼────────┐
        ▼        ▼        ▼
     Database  Storage   API
```

Another example:

```text
             Azure Blob Storage
                    │
               File Uploaded
                    │
                    ▼
              Blob Trigger
                    │
                    ▼
             Azure Function
                    │
                    ▼
             Process File
```

---

# 🔑 Important Azure Functions Concepts

## 1. Function App

A **Function App** is the Azure resource that hosts one or more functions.

```text
Function App
     │
     ├── Function 1
     ├── Function 2
     └── Function 3
```

The functions in a Function App share certain configuration and hosting resources.

---

# 2. Function

A function contains the code that performs a specific task.

Example:

```python
def main(req):
    return "Hello Azure!"
```

---

# 3. Trigger

A trigger determines **when a function runs**.

Examples:

* HTTP Trigger
* Timer Trigger
* Blob Trigger
* Queue Trigger
* Event Grid Trigger
* Service Bus Trigger

---

# ⏰ Timer Trigger

A Timer Trigger runs a function according to a schedule.

Example:

```text
Every 5 minutes
```

```text
Timer
  │
  ▼
Azure Function
  │
  ▼
Execute Task
```

Useful for:

* Scheduled cleanup
* Reports
* Automation
* Scheduled data processing

---

# 🌐 HTTP Trigger

An HTTP trigger executes a function when an HTTP request is received.

```text
Client
  │
  │ HTTP Request
  ▼
Azure Function
  │
  ▼
HTTP Response
```

Example:

```text
GET /api/hello
```

Response:

```text
Hello from Azure Functions!
```

---

# 📦 Blob Trigger

A Blob Trigger runs when changes occur in Azure Blob Storage according to the trigger configuration.

Example:

```text
User uploads file
       │
       ▼
Azure Blob Storage
       │
       ▼
Blob Trigger
       │
       ▼
Azure Function
       │
       ▼
Process File
```

Common use cases:

* Image processing
* Document processing
* Data transformation
* File validation

---

# 📨 Queue Trigger

A Queue Trigger executes a function when messages are available in an Azure Storage Queue.

```text
Application
    │
    ▼
Storage Queue
    │
    ▼
Queue Trigger
    │
    ▼
Azure Function
```

Useful for asynchronous processing.

---

# 📊 Event-Driven Architecture

Azure Functions are commonly used in event-driven architectures.

```text
Event
  │
  ├── HTTP Request
  ├── File Upload
  ├── Queue Message
  ├── Timer
  └── Event
       │
       ▼
Azure Function
       │
       ▼
Business Logic
```

---

# 🛠️ Create Azure Function Using Azure Portal

## Step 1 — Open Azure Portal

Search for:

```text
Function App
```

Select:

```text
Create → Function App
```

---

# Step 2 — Select Subscription

Choose your Azure subscription.

---

# Step 3 — Create Resource Group

Example:

```text
rg-functions-demo
```

---

# Step 4 — Enter Function App Name

Example:

```text
rohit-function-demo
```

The name must be globally unique.

---

# Step 5 — Select Runtime

Examples:

```text
Python
Node.js
.NET
Java
```

Choose the runtime required by your application.

---

# Step 6 — Select Region

Example:

```text
Central India
```

---

# ⚙️ Step 7 — Select Hosting / Plan

Azure Functions provides different hosting options.

Common options include:

* Flex Consumption
* Consumption
* Premium
* Dedicated/App Service
* Container-based options

The available options and capabilities can change over time, so choose based on the current workload and Azure offering.

---

# Step 8 — Storage

Azure Functions commonly uses an Azure Storage account for platform operations.

Example:

```text
Function App
     │
     ▼
Storage Account
```

---

# Step 9 — Review + Create

Click:

```text
Review + create
```

Then:

```text
Create
```

---

# ⚡ Create a Function

After creating the Function App:

```text
Function App
     │
     ▼
Functions
     │
     ▼
Create
```

Select a trigger.

For example:

```text
HTTP Trigger
```

---

# 🌐 HTTP Function Example

Example Python function:

```python
import azure.functions as func

app = func.FunctionApp()

@app.route(route="hello")
def hello(req: func.HttpRequest) -> func.HttpResponse:
    return func.HttpResponse(
        "Hello from Azure Functions!"
    )
```

A request to the function endpoint can return:

```text
Hello from Azure Functions!
```

---

# 💻 Azure Functions Using Azure CLI

Login:

```bash
az login
```

Create a resource group:

```bash
az group create \
  --name rg-functions-demo \
  --location centralindia
```

Create a storage account:

```bash
az storage account create \
  --name <unique-storage-name> \
  --resource-group rg-functions-demo \
  --location centralindia \
  --sku Standard_LRS
```

Create a Function App using an appropriate current Azure Functions hosting/runtime configuration.

> Azure CLI syntax, supported runtime versions, and hosting options change over time. Use the current Azure CLI documentation when creating production resources.

---

# 🔐 Azure Functions Security

Important security practices include:

* HTTPS
* Authentication
* Authorization
* Managed Identity
* Azure Key Vault
* Access restrictions
* Private endpoints where appropriate
* Least-privilege RBAC

Avoid storing secrets directly inside source code.

---

# 🔑 Application Settings

Configuration values can be stored as application settings.

Example:

```text
ENVIRONMENT=production
DATABASE_NAME=mydb
API_URL=https://example.com
```

For secrets:

```text
Azure Key Vault
       │
       ▼
Managed Identity
       │
       ▼
Function App
```

---

# 📈 Scaling

One of the main advantages of serverless computing is automatic scaling.

Example:

```text
Low traffic
    │
    ▼
Few function executions
```

During high traffic:

```text
High traffic
    │
    ▼
More function executions
    │
    ▼
Platform scales resources
```

The exact scaling behavior depends on the hosting plan and workload.

---

# 💰 Serverless Cost Model

Serverless services can be attractive because you don't have to continuously manage traditional VM infrastructure.

Depending on the hosting plan, billing can consider factors such as:

* Executions
* Execution duration
* Memory/resources
* Hosting resources
* Other associated Azure services

Always check the current Azure pricing model for the selected hosting plan.

---

# 📊 Monitoring Azure Functions

Use:

* Azure Monitor
* Application Insights
* Log Analytics
* Function logs
* Metrics
* Alerts

Monitor:

* Function executions
* Failures
* Duration
* Requests
* Exceptions
* Dependencies

---

# 🔄 CI/CD with GitHub Actions

Azure Functions can be deployed through GitHub Actions.

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
    Azure Function App
```

Example workflow structure:

```yaml
name: Deploy Azure Function

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

      - name: Install Dependencies
        run: |
          pip install -r requirements.txt

      - name: Run Tests
        run: |
          pytest

      - name: Deploy
        run: |
          echo "Deploy Azure Function"
```

> For a real deployment, configure Azure authentication and use the appropriate Azure Functions deployment action.

---

# 🧪 Hands-On Lab

## Lab: Create an HTTP Trigger Function

### Objective

Create a serverless HTTP API using Azure Functions.

### Tasks

* [ ] Create Resource Group
* [ ] Create Storage Account
* [ ] Create Function App
* [ ] Select runtime
* [ ] Create HTTP Trigger
* [ ] Write function code
* [ ] Deploy function
* [ ] Test HTTP endpoint
* [ ] Configure application settings
* [ ] Enable Application Insights
* [ ] Configure GitHub Actions
* [ ] Test CI/CD deployment

---

# 🧪 Advanced Lab: Blob Processing

Create an automated file-processing system.

```text
                👤 User
                   │
                   ▼
            Upload File
                   │
                   ▼
          Azure Blob Storage
                   │
                   ▼
             Blob Trigger
                   │
                   ▼
          ⚡ Azure Function
                   │
          ┌────────┴────────┐
          ▼                 ▼
      Process File      Save Result
                              │
                              ▼
                         Blob Storage
```

### Tasks

* [ ] Create Storage Account
* [ ] Create Blob Container
* [ ] Create Function App
* [ ] Configure Blob Trigger
* [ ] Upload test file
* [ ] Verify function execution
* [ ] Check logs
* [ ] Configure monitoring

---

# 🆚 Azure Functions vs Azure VM

| Feature                | Azure VM         | Azure Functions        |
| ---------------------- | ---------------- | ---------------------- |
| Model                  | IaaS             | Serverless             |
| Server Management      | Customer         | Azure-managed          |
| Execution              | Continuous VM    | Function execution     |
| Scaling                | Manual/automated | Hosting-plan dependent |
| Infrastructure Control | High             | Lower                  |
| Best For               | Custom servers   | Event-driven workloads |

---

# 🆚 Azure Functions vs App Service

| Feature           | Azure Functions    | App Service           |
| ----------------- | ------------------ | --------------------- |
| Model             | Serverless         | PaaS                  |
| Main Purpose      | Functions/events   | Web apps/APIs         |
| Trigger Based     | Yes                | Not the primary model |
| Server Management | Azure              | Azure                 |
| Scaling           | Built-in options   | Built-in options      |
| Best For          | Event-driven tasks | Web applications      |

---

# 🧠 When Should You Use Azure Functions?

Use Azure Functions when:

```text
Event occurs
      │
      ▼
Run some code
      │
      ▼
Finish
```

Good examples:

### 1. Scheduled Automation

```text
Every night
    ↓
Function
    ↓
Backup / Cleanup
```

### 2. File Processing

```text
File Upload
    ↓
Function
    ↓
Process File
```

### 3. API Endpoint

```text
HTTP Request
    ↓
Function
    ↓
Response
```

### 4. Queue Processing

```text
Queue Message
    ↓
Function
    ↓
Process Message
```

---

# ❓ Interview Questions

## Q1. What is Azure Functions?

Azure Functions is a serverless compute service that executes code in response to events without requiring you to manage the underlying servers.

---

## Q2. What is a Function App?

A Function App is the Azure resource that provides the hosting environment and configuration for one or more functions.

---

## Q3. What is a trigger?

A trigger defines the event that causes a function to execute.

Examples:

* HTTP
* Timer
* Blob
* Queue
* Event Grid
* Service Bus

---

## Q4. What is an HTTP Trigger?

An HTTP Trigger executes a function when an HTTP request is received.

---

## Q5. What is a Timer Trigger?

A Timer Trigger executes a function according to a schedule.

---

## Q6. What is a Blob Trigger?

A Blob Trigger allows a function to respond to changes or new blobs according to the configured trigger behavior.

---

## Q7. What is serverless computing?

Serverless computing is a cloud execution model where the cloud provider manages the underlying infrastructure and automatically handles much of the operational scaling.

---

## Q8. Does serverless mean there are no servers?

No.

Servers still exist, but Azure manages the underlying infrastructure so the developer doesn't have to manage the servers directly.

---

## Q9. How do you secure Azure Functions?

Use:

* Authentication
* Authorization
* Managed Identity
* Key Vault
* RBAC
* HTTPS
* Access restrictions
* Private networking where required

---

## Q10. How do you monitor Azure Functions?

Use Azure Monitor, Application Insights, Log Analytics, metrics, logs, and alerts.

---

# 📝 Key Takeaways

```text
Azure Functions
       │
       ├── Serverless
       ├── Event Driven
       ├── Function App
       ├── Triggers
       │     ├── HTTP
       │     ├── Timer
       │     ├── Blob
       │     ├── Queue
       │     └── Events
       │
       ├── Automatic Scaling
       ├── CI/CD
       ├── Monitoring
       └── Managed Identity
```

> **Azure Functions = Run code in response to events without managing the underlying servers.**

---

# 🎯 DevOps Learning Path

```text
Azure VM
    ↓
VM Scale Sets
    ↓
App Service
    ↓
Azure Functions
    ↓
Azure Monitor
    ↓
GitHub Actions
    ↓
Terraform
    ↓
Production Azure Architecture
```

---

# 📚 Related Azure Services

* Azure Virtual Machines
* VM Scale Sets
* Azure App Service
* Azure Storage
* Azure Event Grid
* Azure Service Bus
* Azure API Management
* Azure Monitor
* Application Insights
* Azure Key Vault
* Microsoft Entra ID
* Azure DevOps
* GitHub Actions

---

## 📌 Summary

Azure Functions is a powerful **serverless compute service** for building event-driven applications, APIs, automation jobs, and background processing workloads.

For a DevOps engineer, understanding Functions is important for designing **serverless architectures, CI/CD pipelines, monitoring, security, and event-driven systems**.

