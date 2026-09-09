# ☁️ 01 - Azure Fundamentals

This section covers the fundamental concepts of **Microsoft Azure** and **Cloud Computing**.

The goal is to understand how Azure is organized, how cloud resources are managed, and how organizations use Azure to build **scalable, reliable, secure, and manageable cloud solutions**.

---

## 📚 Topics Covered

* 🌍 Azure Regions
* 🏢 Azure Resource Groups
* 💳 Azure Subscriptions
* 🖥️ Azure Portal
* ☁️ Cloud Computing Fundamentals
* 📈 Scalability
* 🛠️ Azure Management Tools
* 🔐 High Availability & Reliability
* 💰 Cost and Resource Management

---

# 🌍 1. Azure Regions

An **Azure Region** is a geographic area containing one or more Azure datacenters.

Azure has a global infrastructure that allows organizations to deploy applications and services closer to their users.

### Topics

* Azure Regions
* Availability Zones
* Region Selection
* Paired Regions
* High Availability
* Reliability
* Disaster Recovery

### Why Regions Matter

Choosing the appropriate Azure region can help with:

* Lower latency
* Regulatory and compliance requirements
* Data residency
* Availability
* Disaster recovery
* Performance

### Example

```text
Users
  |
  v
Azure Region
  |
  +-- Availability Zone 1
  |
  +-- Availability Zone 2
  |
  +-- Availability Zone 3
```

📄 Detailed notes: `Azure-Regions.md`

---

# 🏢 2. Azure Resource Groups

An **Azure Resource Group** is a logical container used to organize and manage related Azure resources.

Resources such as virtual machines, storage accounts, databases, and networks can be grouped together.

### Topics

* What is a Resource Group?
* Resource Organization
* Resource Lifecycle
* Resource Management
* Access and Permissions
* Resource Group Best Practices

### Example

```text
Resource Group
      |
      +-- Virtual Machine
      |
      +-- Storage Account
      |
      +-- Virtual Network
      |
      +-- Database
```

### Benefits

* Organize related resources
* Manage resources together
* Apply access control
* Simplify resource lifecycle management
* Improve administration

📄 Detailed notes: `Resource-Groups.md`

---

# 💳 3. Azure Subscriptions

An **Azure Subscription** provides a logical boundary for Azure resources and is also associated with billing and access management.

A subscription can contain multiple resource groups and resources.

### Topics

* What is an Azure Subscription?
* Subscription Management
* Resource Organization
* Billing and Cost Management
* Access Control
* Subscription Boundaries

### Example

```text
Azure Account
      |
      +-- Subscription 1
      |      |
      |      +-- Resource Group
      |      +-- Resource Group
      |
      +-- Subscription 2
             |
             +-- Resource Group
             +-- Resource Group
```

### Why Subscriptions Matter

Subscriptions help organizations manage:

* Billing
* Access control
* Resource organization
* Governance
* Cost management
* Administrative boundaries

📄 Detailed notes: `Azure-Subscriptions.md`

---

# 🖥️ 4. Azure Portal

The **Azure Portal** is a web-based graphical interface used to create, configure, monitor, and manage Azure resources.

### Topics

* Azure Portal Overview
* Portal Dashboard
* Resource Creation
* Resource Management
* Azure Monitor
* Portal Navigation
* Cloud Resource Management

### Azure Portal Workflow

```text
Azure Portal
     |
     +-- Create Resources
     |
     +-- Configure Resources
     |
     +-- Monitor Resources
     |
     +-- Manage Resources
```

The portal provides a visual interface that is especially useful for beginners and administrators.

📄 Detailed notes: `Azure-Portal.md`

---

# ☁️ 5. Cloud Computing Fundamentals

**Cloud computing** is the delivery of computing resources and services over the internet on demand.

Cloud providers such as Microsoft Azure provide services including:

* Compute
* Storage
* Databases
* Networking
* AI
* IoT

Instead of purchasing and maintaining physical infrastructure, organizations can consume cloud resources when they need them.

---

## 🔑 Key Characteristics of Cloud Computing

| Characteristic                    | Description                                    |
| --------------------------------- | ---------------------------------------------- |
| On-Demand Access                  | Resources can be provisioned when required     |
| Internet Delivery                 | Services are accessed over networks            |
| Scalability                       | Resources can be increased or decreased        |
| Pay-As-You-Go                     | Pay based on resource consumption              |
| Flexibility                       | Choose services based on requirements          |
| Reduced Infrastructure Management | Cloud provider manages physical infrastructure |

---

# 🚀 6. Benefits of Cloud Computing

Azure and cloud computing provide several important benefits.

| Benefit                        | Description                                                  |
| ------------------------------ | ------------------------------------------------------------ |
| Scalability                    | Increase or decrease resources according to demand           |
| Global Reach                   | Deploy applications across different geographic locations    |
| Faster Deployment              | Deploy services faster than traditional infrastructure       |
| Flexibility                    | Choose from many cloud services                              |
| Less Infrastructure Management | Cloud provider manages physical infrastructure               |
| High Availability              | Design applications to remain available during failures      |
| Reliability                    | Use redundant infrastructure and recovery mechanisms         |
| Predictability                 | Improve forecasting of performance and costs                 |
| Security                       | Protect resources and data using cloud security capabilities |
| Governance                     | Apply organizational policies and compliance controls        |
| Manageability                  | Manage resources using centralized tools                     |
| Sustainability                 | Optimize resource usage and reduce unnecessary waste         |

---

# 📈 7. Scalability

**Scalability** means adjusting computing resources according to workload demand.

There are two common approaches:

* Vertical Scaling
* Horizontal Scaling

---

## ⬆️ Vertical Scaling

Vertical scaling means increasing or decreasing the capacity of an existing resource.

### Example

```text
Before:

2 vCPU
4 GB RAM

      |
      | Scale Up
      v

After:

8 vCPU
32 GB RAM
```

This is also commonly called **scaling up** or **scaling down**.

---

## ↔️ Horizontal Scaling

Horizontal scaling means adding or removing instances of a resource.

### Example

```text
Before:

Application
    |
    +-- Server 1


       Scale Out
          |
          v

After:

Application
    |
    +-- Server 1
    +-- Server 2
    +-- Server 3
```

Horizontal scaling is also called **scaling out** or **scaling in**.

### Vertical vs Horizontal Scaling

| Scaling Type | Meaning                                   | Example         |
| ------------ | ----------------------------------------- | --------------- |
| Vertical     | Increase capacity of an existing resource | 2 vCPU → 8 vCPU |
| Horizontal   | Add more resource instances               | 1 VM → 3 VMs    |

---

# 🛠️ 8. Azure Management Tools

Azure provides multiple tools for managing and automating cloud resources.

---

## 🖥️ Azure Portal

The **Azure Portal** is a graphical web-based interface for managing Azure resources.

```text
Azure Portal
     |
     +-- Create Resources
     +-- Configure Resources
     +-- Monitor Resources
     +-- Manage Resources
```

It is useful for:

* Learning Azure
* Creating resources
* Viewing resource configuration
* Monitoring services
* Managing subscriptions

---

## ⌨️ Azure CLI

**Azure CLI** is a command-line tool used to manage Azure resources through commands and scripts.

Example:

```bash
az login
```

List resource groups:

```bash
az group list
```

Azure CLI is useful for:

* Automation
* Scripting
* DevOps pipelines
* Resource management

---

## 💻 Azure PowerShell

**Azure PowerShell** provides PowerShell cmdlets for managing and automating Azure resources.

Example:

```powershell
Connect-AzAccount
```

Azure PowerShell is particularly useful in environments that already use PowerShell for administration and automation.

---

## 🏗️ ARM Templates & Bicep

**Azure Resource Manager (ARM) templates** and **Bicep** are Infrastructure as Code (IaC) technologies used to define and deploy Azure infrastructure.

Instead of manually creating resources, infrastructure can be described as code.

### IaC Concept

```text
Infrastructure Code
        |
        v
Azure Resource Manager
        |
        v
Azure Resources
```

Benefits include:

* Repeatable deployments
* Consistent infrastructure
* Automation
* Version control
* Reduced manual configuration

---

## 📊 Azure Monitor

**Azure Monitor** is used to monitor Azure resources and applications.

It can collect and analyze monitoring data and help identify issues and performance problems.

```text
Azure Resources
      |
      v
Azure Monitor
      |
      +-- Metrics
      +-- Logs
      +-- Alerts
      +-- Insights
```

---

# 🔐 9. High Availability & Reliability

Cloud applications should be designed to remain available even when individual components fail.

Azure provides capabilities such as:

* Availability Zones
* Redundant infrastructure
* Region-based deployment
* Monitoring
* Backup and recovery services

### High Availability Concept

```text
              Application
                   |
          +--------+--------+
          |        |        |
          v        v        v
       Zone 1   Zone 2   Zone 3
          |        |        |
       Server   Server   Server
```

If one component fails, redundant components can continue serving users depending on the architecture.

---

# 🌎 10. Disaster Recovery

**Disaster Recovery (DR)** is the process of restoring applications, services, and data after a major failure or disaster.

Examples of possible failures include:

* Datacenter failure
* Regional outage
* Hardware failure
* Application failure
* Data loss

A disaster recovery strategy may use multiple Azure regions and recovery services.

```text
Primary Region
      |
      | Replication / Recovery
      v
Secondary Region
      |
      v
Disaster Recovery
```

---

# 🧭 Azure Resource Hierarchy

A simplified Azure organization structure can be visualized as:

```text
Microsoft Entra ID / Tenant
          |
          +-------------------+
          |                   |
          v                   v
   Subscription 1       Subscription 2
          |                   |
          v                   v
   Resource Groups      Resource Groups
          |                   |
          v                   v
      Resources             Resources
```

Understanding this hierarchy is important for Azure administration, governance, security, and cost management.

---

# 🔄 Typical Azure Resource Workflow

A basic Azure workflow looks like this:

```text
Azure Account
     |
     v
Subscription
     |
     v
Resource Group
     |
     v
Create Azure Resource
     |
     v
Configure Resource
     |
     v
Monitor Resource
     |
     v
Manage / Scale / Delete
```

---

# 🧑‍💻 Practical Learning

As part of this section, practice the following tasks in the Azure Portal:

### Task 1 — Explore Azure Regions

* Open the Azure Portal
* Explore available regions
* Understand region locations
* Learn why region selection matters

### Task 2 — Create a Resource Group

Create a resource group and explore:

* Resource organization
* Access control
* Resource lifecycle

### Task 3 — Explore Subscriptions

Review:

* Subscription information
* Resource usage
* Cost management
* Access control

### Task 4 — Explore Azure Portal

Practice:

* Navigating the portal
* Searching for services
* Creating resources
* Viewing resource configuration
* Monitoring resources

---

# 📂 Directory Structure

```text
01-Azure-Fundamentals/
│
├── README.md
│
├── Azure-Regions.md
│
├── Resource-Groups.md
│
├── Azure-Subscriptions.md
│
└── Azure-Portal.md
```

---

# 📚 Key Takeaways

* ☁️ Cloud computing provides IT resources on demand over the internet.
* 🌍 Azure Regions provide geographically distributed infrastructure.
* 🏢 Resource Groups organize related Azure resources.
* 💳 Subscriptions provide management, billing, and administrative boundaries.
* 🖥️ Azure Portal provides a graphical interface for managing Azure.
* 📈 Scalability allows resources to adjust according to workload.
* 🛠️ Azure CLI and PowerShell support automation and administration.
* 🏗️ ARM templates and Bicep enable Infrastructure as Code.
* 📊 Azure Monitor helps monitor resources and applications.
* 🔐 High availability and reliability help build resilient cloud solutions.
* 🌎 Disaster recovery helps organizations recover from major failures.

---

# 🎯 Learning Outcome

After completing **Azure Fundamentals**, you should be able to:

* Explain basic cloud computing concepts.
* Understand Azure's global infrastructure.
* Explain Azure Regions and Availability Zones.
* Understand Resource Groups and their purpose.
* Explain Azure Subscriptions.
* Navigate the Azure Portal.
* Understand Azure scalability.
* Identify common Azure management tools.
* Understand the basics of Infrastructure as Code.
* Explain high availability, reliability, and disaster recovery concepts.

---

## 🚀 Next Step

After completing Azure Fundamentals, continue with the next Azure topics and begin deploying real Azure resources using the **Azure Portal, Azure CLI, and Infrastructure as Code**.

---

### 👨‍💻 Author

**Rohit Tambadkar**

🌱 Aspiring DevOps Engineer | ☁️ Cloud Enthusiast | 🚀 Continuous Learner
