# 💳 Azure Subscriptions

An **Azure Subscription** is a logical management and billing boundary within Microsoft Azure.

A subscription can contain multiple **Resource Groups**, and each resource group can contain multiple Azure resources.

Subscriptions are important for managing **billing, access control, governance, quotas, and resource organization**.

---

## 📚 Topics Covered

* What is an Azure Subscription?
* Subscription Management
* Resource Organization
* Billing and Cost Management
* Access Control
* Subscription Boundaries
* Subscription Limits and Quotas
* Governance
* Management Groups

---

# 💡 What is an Azure Subscription?

An Azure Subscription provides a boundary for managing Azure resources and their associated costs.

A simplified Azure hierarchy looks like this:

```text
Azure Tenant
     |
     +-- Subscription 1
     |       |
     |       +-- Resource Group
     |       |       |
     |       |       +-- Resources
     |       |
     |       +-- Resource Group
     |               |
     |               +-- Resources
     |
     +-- Subscription 2
             |
             +-- Resource Group
             |       |
             |       +-- Resources
             |
             +-- Resource Group
```

---

# 🏗️ Azure Subscription Structure

A subscription can contain:

* Resource Groups
* Virtual Machines
* Storage Accounts
* Virtual Networks
* Databases
* App Services
* Containers
* Monitoring resources
* Other Azure services

Example:

```text
Azure Subscription
        |
        +-- Resource Group: rg-web
        |       |
        |       +-- Virtual Machine
        |       +-- Virtual Network
        |       +-- Storage Account
        |
        +-- Resource Group: rg-database
                |
                +-- Database
                +-- Backup
```

---

# 🎯 Why Azure Subscriptions Matter

Subscriptions help organizations manage:

* 💰 Billing
* 🔐 Access Control
* 🗂️ Resource Organization
* 🏛️ Governance
* 📊 Cost Management
* 📏 Quotas and Limits
* 🏢 Administrative Boundaries

---

# 💰 Billing and Cost Management

Azure resources generate usage and associated costs.

The subscription provides an important boundary for tracking and managing these costs.

```text
Azure Resources
      |
      v
Resource Groups
      |
      v
Subscription
      |
      v
Billing & Cost Management
```

Azure provides tools such as **Cost Management** to analyze and control cloud spending.

### Example

An organization could have separate subscriptions for:

```text
Development
Testing
Production
```

This can make it easier to track spending by environment.

---

# 🔐 Access Control

Azure uses **Role-Based Access Control (RBAC)** to manage permissions.

Access can be assigned at different scopes.

```text
Management Group
       |
       v
Subscription
       |
       v
Resource Group
       |
       v
Resource
```

For example:

```text
Developer
   |
   +-- Access → Development Subscription
   |
   +-- No Access → Production Subscription
```

This allows organizations to follow the principle of **least privilege**.

---

# 🗂️ Resource Organization

Subscriptions can be used to separate resources based on:

* Environment
* Business unit
* Application
* Department
* Project
* Security requirements
* Billing requirements

### Example

```text
Azure Tenant
     |
     +-- Development Subscription
     |       |
     |       +-- RG-Dev-Web
     |       +-- RG-Dev-App
     |
     +-- Production Subscription
             |
             +-- RG-Prod-Web
             +-- RG-Prod-App
             +-- RG-Prod-Database
```

---

# 🌍 Multiple Azure Subscriptions

Organizations can have multiple Azure subscriptions.

For example:

```text
Azure Tenant
      |
      +-- Dev Subscription
      |
      +-- Test Subscription
      |
      +-- Production Subscription
      |
      +-- Security Subscription
      |
      +-- Shared Services Subscription
```

The exact subscription strategy depends on the organization's requirements.

---

# 🏢 Subscription Boundaries

A subscription creates an important management boundary.

It can be used to separate:

* Costs
* Access
* Governance
* Resource limits
* Administrative responsibilities

For example:

```text
Development Subscription
        |
        +-- Developers
        +-- Development Resources
        +-- Development Costs

Production Subscription
        |
        +-- Production Team
        +-- Production Resources
        +-- Production Costs
```

This separation can improve security and operational management.

---

# 📏 Quotas and Limits

Azure services have **quotas and limits** that can affect how many resources or how much capacity can be deployed.

Some quotas are associated with subscriptions or specific Azure services.

For example:

```text
Subscription
      |
      +-- VM Quotas
      +-- Network Quotas
      +-- Storage Limits
      +-- Service-specific Limits
```

If a workload reaches a quota, you may need to request an increase or use another design.

---

# 🏛️ Governance

Azure subscriptions can be managed using governance capabilities such as:

* Azure Policy
* Role-Based Access Control (RBAC)
* Resource Locks
* Management Groups
* Tags
* Cost Management

### Governance Example

```text
Management Group
       |
       +-- Subscription
              |
              +-- Azure Policy
              +-- RBAC
              +-- Resource Groups
              +-- Resources
```

These tools help organizations maintain consistent standards across their Azure environment.

---

# 🏢 Management Groups

**Management Groups** provide a level of organization above subscriptions.

They allow organizations to apply governance across multiple subscriptions.

### Example

```text
Azure Tenant
      |
      v
Management Group
      |
      +-- Production Subscription
      |
      +-- Development Subscription
      |
      +-- Testing Subscription
```

Policies and access controls can be applied at the management group level and inherited by lower scopes, depending on the configuration.

---

# 🔒 Subscription Security

Subscriptions can be protected using several Azure capabilities.

Common examples include:

* Microsoft Entra ID
* Azure RBAC
* Azure Policy
* Resource Locks
* Microsoft Defender for Cloud
* Azure Monitor

A secure subscription design should follow:

```text
Least Privilege
      +
Governance
      +
Monitoring
      +
Security Policies
      ↓
Secure Azure Environment
```

---

# 🔒 Resource Locks

Resource Locks can help prevent accidental deletion or modification of resources.

Common lock types include:

* **ReadOnly**
* **CanNotDelete**

Example:

```text
Production Resource
       |
       v
Resource Lock
       |
       v
Prevent Accidental Deletion
```

Resource locks can be applied at different scopes, including subscriptions and resource groups.

---

# 📊 Subscription vs Resource Group

| Feature    | Subscription                    | Resource Group                               |
| ---------- | ------------------------------- | -------------------------------------------- |
| Purpose    | Management and billing boundary | Logical container for resources              |
| Contains   | Resource Groups and resources   | Azure resources                              |
| Scope      | Larger                          | Smaller                                      |
| Billing    | Major billing boundary          | Resources contribute to subscription billing |
| RBAC       | Supported                       | Supported                                    |
| Governance | Supported                       | Supported                                    |
| Lifecycle  | Administrative boundary         | Resources can be managed together            |

---

# 📊 Subscription vs Resource Group vs Resource

```text
Azure Tenant
     |
     v
Subscription
     |
     v
Resource Group
     |
     v
Azure Resource
```

### Example

```text
Azure Tenant
     |
     +-- Subscription
             |
             +-- Resource Group
                     |
                     +-- Virtual Machine
                     +-- Storage Account
                     +-- Virtual Network
```

---

# 🧑‍💻 Azure CLI

You can use Azure CLI to work with subscriptions.

### Login

```bash
az login
```

### List Subscriptions

```bash
az account list
```

### Show Current Subscription

```bash
az account show
```

### Set Active Subscription

```bash
az account set --subscription "<subscription-name-or-id>"
```

After selecting a subscription, subsequent Azure CLI commands are generally executed against that active subscription context.

---

# 🖥️ View Subscription Using Azure Portal

Basic workflow:

```text
Azure Portal
      |
      v
Search "Subscriptions"
      |
      v
Select Subscription
      |
      +-- Overview
      +-- Resource Groups
      +-- Access Control (IAM)
      +-- Cost Management
      +-- Properties
      +-- Resource Usage
```

---

# 🧪 Practical Learning

## Exercise 1 — Explore Your Subscription

Open the Azure Portal and explore:

* Subscription name
* Subscription ID
* Subscription status
* Resource groups
* Cost Management
* Access Control (IAM)
* Resource usage

---

## Exercise 2 — Use Azure CLI

Login:

```bash
az login
```

List subscriptions:

```bash
az account list
```

Check the active subscription:

```bash
az account show
```

---

## Exercise 3 — Understand the Hierarchy

Create a simple diagram:

```text
Azure Tenant
     |
     v
Subscription
     |
     v
Resource Group
     |
     +-- Virtual Machine
     +-- Storage Account
     +-- Virtual Network
```

Explain the purpose of each level.

---

# 🧠 Real-World Example

Imagine a company has three environments:

```text
Azure Tenant
      |
      +-- Development Subscription
      |       |
      |       +-- RG-Web-Dev
      |       +-- RG-App-Dev
      |
      +-- Testing Subscription
      |       |
      |       +-- RG-Web-Test
      |       +-- RG-App-Test
      |
      +-- Production Subscription
              |
              +-- RG-Web-Prod
              +-- RG-App-Prod
              +-- RG-Database-Prod
```

This structure can help separate:

* Development resources
* Testing resources
* Production resources
* Access permissions
* Costs
* Governance requirements

---

# 📂 Related Documentation

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

# 🎯 Key Takeaways

* 💳 An **Azure Subscription** is an important management and billing boundary.
* 🏢 A subscription can contain multiple resource groups.
* 📦 Resource groups contain Azure resources.
* 💰 Subscription-level organization helps with cost management.
* 🔐 RBAC can be applied at the subscription scope.
* 🏛️ Azure Policy and other governance tools help enforce organizational standards.
* 📏 Azure services have quotas and limits.
* 🏢 Management Groups can organize multiple subscriptions.
* 🔒 Resource Locks can help prevent accidental deletion or modification.
* 🛠️ Azure Portal and Azure CLI can be used to manage subscriptions.

---

# 🚀 Learning Outcome

After completing this topic, you should be able to:

* Explain what an Azure Subscription is.
* Understand the relationship between tenants, subscriptions, resource groups, and resources.
* Explain why organizations use multiple subscriptions.
* Understand subscription billing and cost management.
* Understand subscription-level access control.
* Explain governance and subscription boundaries.
* Understand the purpose of Management Groups.
* Use Azure CLI to view and select subscriptions.
* Navigate subscription management through the Azure Portal.
