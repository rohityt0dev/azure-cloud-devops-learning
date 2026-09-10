# 📈 Azure Virtual Machine Scale Sets (VMSS)

## 📌 What is Azure VM Scale Sets?

**Azure Virtual Machine Scale Sets (VMSS)** allow you to create and manage a group of identical Virtual Machines (VMs).

VM Scale Sets help applications handle changing workloads by automatically increasing or decreasing the number of VM instances based on demand.

### Simple Example

```text
                  🌐 Internet
                       │
                       ▼
                ⚖️ Load Balancer
                       │
          ┌────────────┼────────────┐
          ▼            ▼            ▼
       🖥️ VM 1       🖥️ VM 2       🖥️ VM 3
          │            │            │
          └────────────┼────────────┘
                       │
                    VM Scale Set
```

---

# 🎯 Why Use VM Scale Sets?

VMSS is useful when an application needs:

* High availability
* Automatic scaling
* Multiple VM instances
* Load balancing
* Fault tolerance
* Consistent VM configuration
* Better handling of traffic spikes

### Example

Suppose your website normally needs:

```text
2 VM instances
```

During a traffic spike:

```text
2 VMs → 5 VMs
```

When traffic decreases:

```text
5 VMs → 2 VMs
```

This process can be automated using **autoscaling**.

---

# 🏗️ VM Scale Set Architecture

```text
                         🌐 Users
                            │
                            ▼
                    ⚖️ Azure Load Balancer
                            │
              ┌─────────────┼─────────────┐
              ▼             ▼             ▼
           🖥️ VM1         🖥️ VM2         🖥️ VM3
              │             │             │
              └─────────────┼─────────────┘
                            │
                    📈 VM Scale Set
                            │
                     ⚙️ Autoscaling
                            │
              ┌─────────────┴─────────────┐
              ▼                           ▼
        Scale Out ↗                 Scale In ↘
        Add VMs                    Remove VMs
```

---

# 🔑 Important VMSS Components

## 1. VM Instances

VMSS manages multiple VM instances.

Example:

```text
VMSS
 ├── Instance 1
 ├── Instance 2
 ├── Instance 3
 └── Instance 4
```

---

## 2. VM Image

All VM instances can be created from the same image.

Examples:

* Ubuntu
* Debian
* Windows Server
* Azure Linux
* Custom images

---

## 3. VM Size

Defines the compute resources available to each VM.

Examples:

```text
Standard_B2s
Standard_D2s_v5
Standard_D4s_v5
```

Resources include:

* vCPU
* RAM
* Network performance
* Temporary storage

---

## 4. Instance Count

Defines how many VM instances should run.

Example:

```text
Minimum instances = 2
Maximum instances = 5
Current instances = 3
```

---

# 📈 Autoscaling

Autoscaling automatically adjusts the number of VM instances according to workload.

There are two major scaling operations.

### Scale Out

Adds more VM instances.

```text
2 VMs
 ↓
3 VMs
 ↓
4 VMs
```

Used when demand increases.

---

### Scale In

Removes VM instances.

```text
5 VMs
 ↓
4 VMs
 ↓
3 VMs
```

Used when demand decreases.

---

# 📊 Autoscaling Based on CPU

Example:

```text
CPU > 70%
     │
     ▼
Add VM instance
     │
     ▼
CPU decreases
```

Scale-in example:

```text
CPU < 30%
     │
     ▼
Remove VM instance
```

A real autoscaling configuration should also account for cooldown periods and appropriate minimum/maximum instance limits.

---

# ⚖️ Load Balancing

VM Scale Sets can work with Azure load-balancing services to distribute traffic across VM instances.

```text
                 🌐 Users
                    │
                    ▼
             ⚖️ Load Balancer
                    │
        ┌───────────┼───────────┐
        ▼           ▼           ▼
      VM 1        VM 2        VM 3
```

Benefits:

* Traffic distribution
* High availability
* Better performance
* Automatic handling of instance changes

---

# 🛠️ Create VM Scale Set Using Azure Portal

## Step 1 — Open Azure Portal

Go to the Azure Portal and search for:

```text
Virtual machine scale sets
```

Click:

```text
Create → Virtual machine scale set
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

Create or select a resource group.

Example:

```text
Resource Group:
rg-vmss-demo
```

---

## Step 4 — Enter VMSS Name

Example:

```text
VM Scale Set Name:
vmss-web-demo
```

Choose the appropriate region.

Example:

```text
Region:
Central India
```

---

## Step 5 — Select Orchestration Mode

Azure VM Scale Sets support orchestration options.

For many modern VMSS deployments, **Flexible orchestration** is useful when you need more flexibility in managing VM instances.

Choose the option appropriate for your workload.

---

# 🖥️ Step 6 — Select Image

Example:

```text
Image:
Ubuntu Server
```

Select the required OS image.

---

# ⚙️ Step 7 — Select VM Size

Example:

```text
VM Size:
Standard_B2s
```

Choose a size based on:

* CPU requirements
* Memory requirements
* Network requirements
* Workload
* Cost

---

# 🔐 Step 8 — Authentication

You can configure:

```text
SSH public key
```

for Linux VMs.

For Windows VMs, configure the appropriate administrator authentication method.

---

# 📈 Step 9 — Configure Scaling

Example:

```text
Initial instance count: 2
Minimum instances: 2
Maximum instances: 5
```

Example autoscaling:

```text
CPU > 70%
→ Add instance

CPU < 30%
→ Remove instance
```

---

# 🌐 Step 10 — Configure Networking

Select or create:

```text
Virtual Network
        │
        └── Subnet
```

Example:

```text
VNet:
vnet-prod

Subnet:
subnet-web
```

You can also configure:

* Load balancer
* Public IP
* Network Security Group
* Backend pool

---

# 🔎 Step 11 — Review + Create

Review the configuration.

Click:

```text
Review + create
```

Then:

```text
Create
```

Azure will create the VM Scale Set and its VM instances.

---

# 💻 Create VM Scale Set Using Azure CLI

First, log in:

```bash
az login
```

Set your subscription if required:

```bash
az account set --subscription "<SUBSCRIPTION_ID>"
```

---

## Create Resource Group

```bash
az group create \
  --name rg-vmss-demo \
  --location centralindia
```

---

## Create VM Scale Set

Example:

```bash
az vmss create \
  --resource-group rg-vmss-demo \
  --name vmss-web-demo \
  --image Ubuntu2204 \
  --instance-count 2 \
  --vm-sku Standard_B2s \
  --upgrade-policy-mode automatic \
  --admin-username azureuser \
  --generate-ssh-keys
```

> Azure CLI syntax and available image/SKU names can change. Check the current Azure CLI documentation when running commands in your subscription.

---

# 🔍 Check VM Scale Set

```bash
az vmss show \
  --resource-group rg-vmss-demo \
  --name vmss-web-demo
```

---

# 📋 List VMSS Instances

```bash
az vmss list-instances \
  --resource-group rg-vmss-demo \
  --name vmss-web-demo \
  --output table
```

Example output:

```text
InstanceId    ProvisioningState
-----------   -----------------
0             Succeeded
1             Succeeded
```

---

# 📈 Scale VMSS Manually

Increase instance count:

```bash
az vmss scale \
  --resource-group rg-vmss-demo \
  --name vmss-web-demo \
  --new-capacity 4
```

Now:

```text
Before:

VM1
VM2

After:

VM1
VM2
VM3
VM4
```

---

# 🔄 Configure Autoscaling

Autoscaling can be configured using Azure Monitor autoscale settings.

Conceptually:

```text
Minimum = 2
Default = 2
Maximum = 5
```

CPU rule:

```text
Average CPU > 70%
        ↓
Increase instance count
```

Scale-in rule:

```text
Average CPU < 30%
        ↓
Decrease instance count
```

---

# 📊 Monitoring VMSS

Azure Monitor can be used to monitor VM Scale Sets.

Important metrics include:

* CPU percentage
* Network traffic
* Disk activity
* Available memory where supported/configured
* Instance health
* Application metrics

You can also use:

```text
Azure Monitor
Log Analytics
Application Insights
```

for broader monitoring and troubleshooting.

---

# 🔐 VMSS Security

Important security practices:

### Network Security Group

Use NSGs to control inbound and outbound traffic.

Example:

```text
Internet
   │
   ▼
NSG
   │
   ▼
VMSS
```

---

### SSH Security

Avoid exposing SSH/RDP broadly to the internet.

Prefer:

* Restricted source IPs
* Azure Bastion
* Just-in-time access where appropriate
* SSH keys for Linux

---

### Managed Identity

Use managed identities when VM instances need to access Azure resources.

Example:

```text
VMSS
  │
  ▼
Managed Identity
  │
  ▼
Azure Storage
```

This avoids storing credentials directly inside applications.

---

# 🔄 VMSS Upgrade Policies

VMSS can update VM instances when the model/configuration changes.

Common upgrade approaches include:

```text
Automatic
Rolling
Manual
```

The appropriate strategy depends on the workload and availability requirements.

---

# 🚀 VMSS in DevOps

VM Scale Sets are useful in DevOps environments for:

* CI/CD infrastructure
* Web applications
* Application servers
* Auto-scaling workloads
* Self-hosted build agents
* High-availability applications

Example:

```text
GitHub
   │
   ▼
CI/CD Pipeline
   │
   ▼
Azure
   │
   ▼
VM Scale Set
   │
   ├── VM 1
   ├── VM 2
   └── VM 3
```

---

# 🧪 Hands-On Lab

## Lab: Deploy a Web Application on VMSS

### Objective

Create a VM Scale Set with multiple Linux VM instances and configure it to serve a web application.

### Architecture

```text
                         🌐 Internet
                              │
                              ▼
                       ⚖️ Load Balancer
                              │
                 ┌────────────┼────────────┐
                 ▼            ▼            ▼
              🖥️ VM1       🖥️ VM2       🖥️ VM3
                 │            │            │
                 └────────────┼────────────┘
                              │
                         VM Scale Set
                              │
                         📈 Autoscaling
```

### Tasks

* [ ] Create Resource Group
* [ ] Create Virtual Network
* [ ] Create Subnet
* [ ] Create VM Scale Set
* [ ] Configure Linux image
* [ ] Configure VM instances
* [ ] Configure NSG
* [ ] Configure load balancing
* [ ] Deploy a web server
* [ ] Test application access
* [ ] Configure autoscaling
* [ ] Generate CPU load
* [ ] Observe scale-out
* [ ] Reduce workload
* [ ] Observe scale-in

---

# 🧠 VM vs VMSS

| Feature           | Azure VM                | VM Scale Set                         |
| ----------------- | ----------------------- | ------------------------------------ |
| Number of VMs     | Usually individual      | Multiple instances                   |
| Scaling           | Mostly manual           | Manual + automatic                   |
| High Availability | Must design separately  | Built for multi-instance deployments |
| Load Balancing    | Optional                | Commonly integrated                  |
| Autoscaling       | Not the primary feature | Supported                            |
| Use Case          | Single server/workload  | Scalable applications                |

---

# 🆚 VMSS vs App Service

| Feature                   | VMSS                  | App Service         |
| ------------------------- | --------------------- | ------------------- |
| Service Model             | IaaS                  | PaaS                |
| OS Management             | Customer-managed      | Azure-managed       |
| VM Access                 | Yes                   | Limited/abstracted  |
| Scaling                   | Autoscale             | Autoscale           |
| OS Control                | High                  | Lower               |
| Infrastructure Management | More responsibility   | Less responsibility |
| Best For                  | Custom infrastructure | Web apps/APIs       |

---

# 💡 Real-World Example

Imagine an e-commerce website.

Normal traffic:

```text
2 VM instances
```

During a sale:

```text
Traffic ↑
   ↓
CPU ↑
   ↓
Autoscale triggered
   ↓
2 VMs → 5 VMs
```

After the sale:

```text
Traffic ↓
   ↓
CPU ↓
   ↓
Autoscale triggered
   ↓
5 VMs → 2 VMs
```

This allows the application to handle changing demand without permanently running the maximum number of instances.

---

# ❓ Interview Questions

## Q1. What is Azure VM Scale Set?

Azure VM Scale Set is an Azure compute service that allows you to deploy and manage a group of VMs that can scale based on workload.

---

## Q2. What is the main benefit of VMSS?

The main benefits are:

* Automatic scaling
* High availability
* Load balancing
* Centralized VM management
* Better handling of changing workloads

---

## Q3. What is scale-out?

**Scale-out** means increasing the number of VM instances.

```text
2 VMs → 4 VMs
```

---

## Q4. What is scale-in?

**Scale-in** means decreasing the number of VM instances.

```text
5 VMs → 2 VMs
```

---

## Q5. How does VMSS perform autoscaling?

VMSS autoscaling can use monitoring metrics such as CPU utilization and configured rules to increase or decrease the number of VM instances.

---

## Q6. Can VMSS work with a Load Balancer?

Yes. VMSS can be integrated with Azure load-balancing services to distribute incoming traffic across instances.

---

## Q7. What is the difference between VM and VMSS?

An Azure VM normally represents an individual virtual machine, while VMSS is designed to manage multiple VM instances as a scalable group.

---

## Q8. What happens when an instance fails?

Depending on the configuration and health mechanisms, Azure can detect unhealthy instances and maintain the desired VMSS capacity by replacing or recovering instances.

---

## Q9. What is the minimum and maximum instance count?

They define the lower and upper boundaries for autoscaling.

Example:

```text
Minimum = 2
Maximum = 10
```

The VMSS should not scale below 2 or above 10 instances under that autoscaling configuration.

---

## Q10. Is VMSS IaaS or PaaS?

VMSS is primarily an **IaaS compute service** because you manage VM-level infrastructure such as the operating system and installed software.

---

# 📝 Key Takeaways

```text
VMSS
 │
 ├── Multiple VM Instances
 │
 ├── Autoscaling
 │      ├── Scale Out
 │      └── Scale In
 │
 ├── Load Balancing
 │
 ├── High Availability
 │
 ├── Monitoring
 │
 └── DevOps Integration
```

### Remember

> **VM = Individual Virtual Machine**

> **VMSS = Group of Virtual Machines that can scale**

---

# 📚 Azure Services Related to VMSS

* Azure Virtual Machines
* Azure Load Balancer
* Azure Virtual Network
* Network Security Groups
* Azure Monitor
* Azure Autoscale
* Azure Managed Identity
* Azure Bastion
* Azure Image Gallery

---

# 🎯 DevOps Learning Path

After learning VM Scale Sets, practice these topics:

```text
Azure VM
   ↓
VM Scale Sets
   ↓
Load Balancer
   ↓
Azure Monitor
   ↓
Autoscaling
   ↓
Terraform
   ↓
CI/CD
   ↓
Production Architecture
```

---

## 📌 Summary

Azure VM Scale Sets provide a scalable way to run multiple VM instances for applications that require **high availability, load balancing, and automatic scaling**.

For a DevOps engineer, VMSS is particularly useful for understanding how infrastructure can automatically adapt to changing application workloads.
