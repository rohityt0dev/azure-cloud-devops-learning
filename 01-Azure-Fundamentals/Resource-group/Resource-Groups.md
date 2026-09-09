# 🏢 Azure Resource Groups

An **Azure Resource Group** is a logical container used to organize and manage related Azure resources.

Resources such as **Virtual Machines, Storage Accounts, Virtual Networks, Databases, and other Azure services** can be organized within a resource group.

Resource groups are an important part of Azure resource management and administration.

---

## 📚 Topics Covered

* What is an Azure Resource Group?
* Resource Organization
* Resource Lifecycle
* Resource Management
* Access and Permissions
* Resource Group Best Practices
* Resource Group Location
* Resource Dependencies
* Resource Deletion

---

# 📦 What is an Azure Resource Group?

A **Resource Group (RG)** is a logical container that holds related Azure resources.

For example, an application may have:

```text id="x5q8qy"
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

Instead of managing every resource individually, related resources can be managed together through the resource group.

---

# 🎯 Why Use Resource Groups?

Resource groups help organizations organize and manage Azure resources efficiently.

### Common Uses

* Organize related resources
* Manage resources together
* Control access
* Monitor resources
* Apply policies
* Manage resource lifecycle
* Simplify administration

---

# 🔄 Resource Group Lifecycle

A resource group can be used to manage the lifecycle of an application.

For example:

```text id="7t4q3a"
Create Resource Group
        |
        v
Create Resources
        |
        v
Configure Application
        |
        v
Run Application
        |
        v
Monitor Resources
        |
        v
Delete Resource Group
        |
        v
Resources Deleted
```

⚠️ **Important:** Deleting a resource group deletes the resources contained within it. Always verify what resources are inside a resource group before deleting it.

---

# 🗂️ Resource Organization

A good resource group structure makes Azure environments easier to manage.

For example:

```text id="5t9xg1"
Production Resource Group
        |
        +-- Web Server
        +-- Application Server
        +-- Database
        +-- Storage
        +-- Network Resources
```

You can also organize resources based on application, environment, or workload.

### Example Environment Structure

```text id="0n4b4w"
Azure Subscription
       |
       +-- RG-Development
       |      |
       |      +-- VM
       |      +-- Storage
       |
       +-- RG-Testing
       |      |
       |      +-- VM
       |      +-- Database
       |
       +-- RG-Production
              |
              +-- VM
              +-- Database
              +-- Storage
```

---

# 📍 Resource Group Location

When creating a resource group, you select a **region/location for the resource group's metadata**.

This does **not** mean that all resources inside the resource group must be deployed in the same region.

For example:

```text id="2q1y9c"
Resource Group
Location: Region A
       |
       +-- VM → Region A
       |
       +-- Storage → Region B
       |
       +-- Database → Region A
```

However, for operational simplicity and resilience planning, organizations should choose resource group locations thoughtfully.

---

# 🔐 Access and Permissions

Azure Resource Groups can be used with **Azure Role-Based Access Control (RBAC)** to control who can access and manage resources.

Permissions can be assigned at different scopes, including:

```text id="j9xv8p"
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

For example, a user could be given permissions to manage resources within a specific resource group without giving them access to every resource in the subscription.

---

# 🏷️ Resource Tags

**Tags** are name-value pairs that help organize and identify Azure resources.

Example:

```text id="n3q0g4"
Environment = Production
Application = WebApp
Owner       = DevOps
Department  = IT
```

Tags can help with:

* Resource organization
* Cost analysis
* Resource identification
* Automation
* Governance

> 💡 Tags are applied to resources and can also be used on resource groups, depending on the Azure resource and management scenario.

---

# 🔗 Resource Dependencies

Azure resources can depend on other resources.

For example:

```text id="n9a4j7"
Virtual Machine
      |
      +-- Virtual Network
      |
      +-- Network Interface
      |
      +-- Disk
      |
      +-- Public IP
```

Resource groups help keep related resources organized, but they do not themselves create dependencies between resources.

---

# 🧹 Resource Group Deletion

Deleting a resource group can delete the resources contained within it.

For example:

```text id="c4f7k2"
Resource Group
      |
      +-- VM
      +-- Storage
      +-- Database
      |
      |
      +-- Delete Resource Group
                  |
                  v
          Resources Deleted
```

Therefore, resource group deletion should be performed carefully, especially in production environments.

---

# 🏗️ Resource Group Design Best Practices

When designing resource groups, consider the **lifecycle of the resources**.

### 1. Group Resources with Similar Lifecycles

If resources are created, managed, and deleted together, they are good candidates for the same resource group.

```text id="8j2q4e"
Application A
     |
     +-- Web
     +-- API
     +-- Storage
     +-- Database
```

---

### 2. Separate Environments

It is often useful to separate environments:

```text id="x5c9k2"
RG-Dev
RG-Test
RG-Stage
RG-Prod
```

This makes environment management clearer.

---

### 3. Use Meaningful Names

Use consistent naming conventions.

Example:

```text id="q8r1df"
rg-web-dev
rg-web-test
rg-web-prod
```

Good naming makes resources easier to identify.

---

### 4. Use Tags

Apply useful tags such as:

```text id="w8f4x2"
Environment = Production
Application = ECommerce
Owner       = DevOps
CostCenter  = IT
```

---

### 5. Consider Access Requirements

Resources requiring different access permissions may be better placed in separate resource groups.

---

# 📊 Resource Group vs Subscription

| Feature        | Resource Group                             | Subscription                    |
| -------------- | ------------------------------------------ | ------------------------------- |
| Purpose        | Organize related resources                 | Management and billing boundary |
| Contains       | Azure resources                            | Resource groups and resources   |
| Scope          | Smaller                                    | Larger                          |
| Billing        | Resources contribute to subscription costs | Billing boundary                |
| Access Control | Can assign RBAC                            | Can assign RBAC                 |
| Lifecycle      | Can manage related resources together      | Broader administrative boundary |

---

# 🧠 Example: Web Application

Imagine an organization has an e-commerce application.

A possible resource structure could be:

```text id="m6c1ps"
Azure Subscription
        |
        +-- rg-ecommerce-dev
        |       |
        |       +-- App Service
        |       +-- Storage
        |       +-- Database
        |
        +-- rg-ecommerce-prod
                |
                +-- App Service
                +-- Storage
                +-- Database
                +-- Application Insights
```

This structure separates development and production resources.

---

# 🛠️ Azure CLI

You can create a resource group using Azure CLI.

### Login

```bash id="4r9jv8"
az login
```

### Create Resource Group

```bash id="x8n5kc"
az group create \
  --name my-resource-group \
  --location centralindia
```

### List Resource Groups

```bash id="6s4jbf"
az group list
```

### Show a Resource Group

```bash id="k3m8dz"
az group show \
  --name my-resource-group
```

### Delete a Resource Group

```bash id="v9d2qa"
az group delete \
  --name my-resource-group
```

⚠️ Use the delete command carefully because it can remove the resources contained in the resource group.

---

# 🖥️ Create Resource Group Using Azure Portal

Basic workflow:

```text id="j5r0mz"
Azure Portal
     |
     v
Resource Groups
     |
     v
Create
     |
     v
Select Subscription
     |
     v
Enter Resource Group Name
     |
     v
Select Region
     |
     v
Review + Create
```

---

# 📊 Resource Group Example

```text
                 Azure Subscription
                        |
                        v
               Resource Group
               "rg-production"
                        |
          +-------------+-------------+
          |             |             |
          v             v             v
       Web App       Database       Storage
          |
          v
      Application
```

---

# 🎯 Key Takeaways

* 📦 A **Resource Group** is a logical container for Azure resources.
* 🗂️ Related resources can be organized into the same resource group.
* 🔄 Resources with similar lifecycles are often good candidates for the same resource group.
* 🔐 Azure RBAC can be assigned at the resource group scope.
* 🏷️ Tags help organize and identify resources.
* 📍 The resource group's location is associated with its metadata; resources can be in different regions.
* ⚠️ Deleting a resource group can delete its contained resources.
* 🏗️ Good resource group design improves administration and governance.
* 💳 Resource groups exist within Azure subscriptions.

---

# 🧪 Practical Learning

### Exercise 1 — Create a Resource Group

Create a resource group using the Azure Portal.

Example:

```text
Name: rg-learning-dev
Region: Central India
```

---

### Exercise 2 — Create Using Azure CLI

```bash
az login

az group create \
  --name rg-learning-dev \
  --location centralindia
```

Verify:

```bash
az group list
```

---

### Exercise 3 — Explore Resource Management

Inside your resource group:

* Create a resource.
* View the resource.
* Check resource dependencies.
* Explore Access Control (IAM).
* Add tags.
* Review activity logs.
* Delete the test resource.

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

## 🚀 Learning Outcome

After completing this topic, you should be able to:

* Explain what an Azure Resource Group is.
* Organize Azure resources using resource groups.
* Understand resource group lifecycle management.
* Understand resource group locations.
* Apply Azure RBAC at the resource group scope.
* Use tags for resource organization.
* Create and manage resource groups using Azure Portal and Azure CLI.
* Understand the relationship between subscriptions, resource groups, and resources.
