# 🖥️ Azure Portal

The **Azure Portal** is a web-based graphical user interface (GUI) provided by Microsoft for creating, configuring, monitoring, and managing Azure resources.

It provides a centralized interface where users can work with Azure services without needing to use command-line tools.

The Azure Portal is especially useful for **beginners, developers, cloud administrators, and DevOps engineers**.

---

## 📚 Topics Covered

* Azure Portal Overview
* Portal Dashboard
* Portal Navigation
* Resource Creation
* Resource Management
* Azure Monitor
* Cloud Resource Management
* Access Control
* Cost Management
* Cloud Shell

---

# 💡 What is Azure Portal?

Azure Portal is a web-based management interface for Microsoft Azure.

From the portal, you can:

* Create Azure resources
* Configure resources
* View resource properties
* Monitor applications
* Manage access permissions
* View costs
* Manage subscriptions
* Delete resources
* Run Azure CLI or PowerShell commands using Cloud Shell

### Basic Workflow

```text id="v6f5p4"
Azure Portal
     |
     +-- Create Resources
     |
     +-- Configure Resources
     |
     +-- Monitor Resources
     |
     +-- Manage Resources
     |
     +-- Delete Resources
```

---

# 🏠 Azure Portal Dashboard

The Azure Portal provides a customizable dashboard.

The dashboard can contain tiles and shortcuts for commonly used resources and services.

### Example

```text id="zj6f31"
+------------------------------------------------+
|                 Azure Portal                   |
+------------------------------------------------+
| Search Azure                                   |
+------------------------------------------------+
| Dashboard                                      |
|                                                |
|  Virtual Machines     Storage     Networks     |
|                                                |
|  Resource Groups      Monitor     Subscriptions|
|                                                |
+------------------------------------------------+
```

You can customize the dashboard according to your requirements.

---

# 🧭 Azure Portal Navigation

The Azure Portal provides multiple ways to find and manage services.

Common navigation areas include:

* Home
* Dashboard
* Resource Groups
* All Resources
* Subscriptions
* Azure Services
* Monitor
* Cost Management
* Microsoft Entra ID
* Help and Support
* Cloud Shell

### Navigation Flow

```text id="2b1u3c"
Azure Portal
      |
      +-- Home
      |
      +-- Resource Groups
      |
      +-- All Resources
      |
      +-- Subscriptions
      |
      +-- Monitor
      |
      +-- Cost Management
      |
      +-- Cloud Shell
```

---

# 🔍 Azure Portal Search

The portal provides a search bar that allows you to quickly find:

* Azure services
* Resources
* Resource groups
* Subscriptions
* Documentation
* Marketplace offerings

Example:

```text id="o5q6zi"
Search
  |
  +-- Virtual Machines
  +-- Storage Accounts
  +-- Resource Groups
  +-- Virtual Networks
  +-- Azure Monitor
```

---

# 🏗️ Create Azure Resources

Azure Portal can be used to create many different Azure resources.

Examples include:

* Virtual Machines
* Storage Accounts
* Virtual Networks
* Databases
* App Services
* Container resources
* Azure Kubernetes Service
* Monitoring resources

### General Resource Creation Workflow

```text id="7u3b9e"
Azure Portal
      |
      v
Create a Resource
      |
      v
Select Azure Service
      |
      v
Select Subscription
      |
      v
Select/Create Resource Group
      |
      v
Configure Resource
      |
      v
Review + Create
      |
      v
Resource Deployed
```

---

# 🏢 Resource Groups

The Azure Portal provides a graphical interface for managing Resource Groups.

From a Resource Group, you can:

* View resources
* Create resources
* Configure resources
* Manage access
* View activity
* Add tags
* Monitor resources
* Delete resources

Example:

```text id="1k6rzi"
Resource Group
      |
      +-- Virtual Machine
      +-- Storage Account
      +-- Virtual Network
      +-- Database
```

---

# 💳 Manage Azure Subscriptions

The portal can be used to view and manage Azure subscriptions.

You can review information such as:

* Subscription name
* Subscription ID
* Subscription status
* Resource groups
* Resource usage
* Cost information
* Access control

### Navigation

```text id="tq1b0n"
Azure Portal
      |
      v
Subscriptions
      |
      +-- Overview
      +-- Resource Groups
      +-- Access Control (IAM)
      +-- Cost Management
      +-- Properties
```

---

# 📊 Azure Monitor

**Azure Monitor** helps you monitor the performance and health of Azure resources and applications.

You can access monitoring capabilities from the Azure Portal.

Examples include:

* Metrics
* Logs
* Alerts
* Application Insights
* Resource health

### Monitoring Workflow

```text id="5d2y6v"
Azure Resources
       |
       v
Azure Monitor
       |
       +-- Metrics
       +-- Logs
       +-- Alerts
       +-- Insights
       |
       v
Troubleshooting / Analysis
```

---

# 🔐 Access Control

Azure Portal provides access to **Access Control (IAM)** for managing permissions.

You can assign Azure RBAC roles to users, groups, service principals, and managed identities, depending on the scenario.

### Example

```text id="y0m6tq"
Resource Group
      |
      v
Access Control (IAM)
      |
      +-- Owner
      +-- Contributor
      +-- Reader
```

This helps organizations implement the **principle of least privilege**.

---

# 💰 Cost Management

Azure Portal provides access to **Cost Management** capabilities.

You can use it to understand and manage cloud spending.

Examples include:

* Cost analysis
* Budgets
* Cost alerts
* Usage analysis

### Cost Management Workflow

```text id="n5q3v2"
Azure Resources
       |
       v
Subscription
       |
       v
Cost Management
       |
       +-- Analyze Costs
       +-- Create Budgets
       +-- Monitor Spending
```

---

# ☁️ Cloud Shell

**Azure Cloud Shell** provides a browser-based command-line environment directly from the Azure Portal.

It supports:

* Azure CLI
* Azure PowerShell

### Example

```text id="p8c2jv"
Azure Portal
      |
      v
Cloud Shell
      |
      +-- Azure CLI
      |
      +-- Azure PowerShell
```

Example Azure CLI command:

```bash id="m7h8k2"
az group list
```

---

# 🛠️ Azure Portal vs Azure CLI vs PowerShell

Azure provides multiple management methods.

| Tool             | Interface    | Common Use                                 |
| ---------------- | ------------ | ------------------------------------------ |
| Azure Portal     | GUI          | Manual management and visualization        |
| Azure CLI        | Command Line | Automation and scripting                   |
| Azure PowerShell | PowerShell   | Administration and automation              |
| ARM Templates    | IaC          | Declarative infrastructure deployment      |
| Bicep            | IaC          | Simplified Azure infrastructure definition |

### Example

```text id="w8c7q1"
                  Azure
                    |
       +------------+------------+
       |            |            |
       v            v            v
     Portal       CLI       PowerShell
       |            |            |
       +------------+------------+
                    |
                    v
             Azure Resources
```

---

# 🧑‍💻 Azure Portal for DevOps

Although DevOps engineers frequently use CLI, PowerShell, Terraform, Bicep, and CI/CD pipelines, the Azure Portal is still useful for:

* Checking resource status
* Troubleshooting
* Viewing logs
* Checking metrics
* Inspecting networking
* Reviewing deployments
* Checking costs
* Managing access
* Verifying infrastructure created by automation

### DevOps Workflow

```text id="b7m3p2"
Infrastructure as Code
        |
        v
Azure Resources
        |
        v
Azure Portal
        |
        +-- Verify
        +-- Monitor
        +-- Troubleshoot
```

---

# 🔄 Azure Portal Workflow

A typical workflow can look like:

```text id="9e6q2x"
Login to Azure Portal
        |
        v
Select Subscription
        |
        v
Create Resource Group
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
Manage / Scale / Update
        |
        v
Delete When No Longer Required
```

---


# 🎯 Key Takeaways

* 🖥️ **Azure Portal** is a web-based GUI for managing Azure resources.
* 🏗️ You can create and configure Azure resources through the portal.
* 🏢 Resource Groups can be viewed and managed through the portal.
* 💳 Subscriptions provide access to billing, usage, and management information.
* 📊 Azure Monitor provides metrics, logs, alerts, and insights.
* 🔐 Access Control (IAM) allows you to manage Azure RBAC permissions.
* 💰 Cost Management helps analyze and control Azure spending.
* ☁️ Cloud Shell provides browser-based Azure CLI and PowerShell.
* 🛠️ DevOps engineers can use the portal for verification, monitoring, and troubleshooting.
* 🚀 Azure Portal is one of several ways to manage Azure infrastructure.

---

# 📊 Azure Management Methods

```text
                    Azure
                      |
       +--------------+--------------+
       |              |              |
       v              v              v
   Azure Portal    Azure CLI    PowerShell
       |              |              |
       +--------------+--------------+
                      |
                      v
               Azure Resources
                      |
            +---------+---------+
            |                   |
            v                   v
        Monitoring          Management
```

---

## 🚀 Learning Outcome

After completing this topic, you should be able to:

* Explain what the Azure Portal is.
* Navigate the Azure Portal.
* Create and manage Azure resources.
* Work with Resource Groups and Subscriptions.
* Understand Azure Monitor from the portal.
* Manage access using Azure RBAC.
* Explore Azure costs and usage.
* Use Cloud Shell from the Azure Portal.
* Understand the difference between Portal, CLI, and PowerShell.
* Use the Azure Portal for basic DevOps troubleshooting and verification.
