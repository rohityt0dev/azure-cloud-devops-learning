# 🖥️ Azure Virtual Machines

Azure Virtual Machines (VMs) are one of the fundamental **compute services** provided by Microsoft Azure.

An Azure VM provides a virtualized computer that can run an operating system and applications in the cloud.

Azure VMs are useful when you need more control over the operating system, software, networking, and compute environment.

---

## 📚 Topics Covered

* What is Azure VM?
* VM Architecture
* Important VM Components
* VM Sizes
* OS Disk
* Data Disks
* Network Interface
* Public IP
* Network Security Group
* Virtual Network
* Subnet
* VM Authentication
* Create VM Using Azure Portal
* Create VM Using Azure CLI
* Connect to Azure VM
* Start / Stop / Restart VM
* Delete Azure VM
* VM Cost Considerations
* DevOps Use Cases

---

# 📌 What is Azure VM?

**Azure Virtual Machine** is an Infrastructure as a Service (IaaS) offering that allows you to create and run virtual computers in Azure.

A VM can run operating systems such as:

* Linux
* Windows Server

You can install and configure applications, packages, services, and other software on the VM.

### Simple Example

```text
User
  |
  v
Azure Virtual Machine
  |
  +-- Operating System
  +-- Applications
  +-- CPU
  +-- Memory
  +-- Storage
  +-- Networking
```

---

# 🏗️ VM Architecture

An Azure VM works together with several Azure resources.

```text
                         Azure VM
                            |
          +-----------------+-----------------+
          |                 |                 |
          v                 v                 v
      Compute           Storage           Networking
          |                 |                 |
      VM Size            OS Disk          Virtual Network
          |              Data Disk             |
          |                                    v
          |                                  Subnet
          |                                    |
          |                                    v
          |                              Network Interface
          |                                    |
          |                                    v
          |                               Public IP
          |                                    |
          |                                    v
          |                             Network Security
          |                                 Group
```

---

# 🔑 Important VM Components

## 1️⃣ VM Size

The **VM size** determines the compute capacity available to the virtual machine.

It affects resources such as:

* vCPUs
* Memory
* Network performance
* Temporary storage
* Supported disk configurations

Example:

```text
VM Size
   |
   +-- vCPU
   +-- RAM
   +-- Network Performance
   +-- Temporary Storage
```

For learning purposes, choose a small, low-cost VM size that is available in your selected region and subscription.

> 💡 VM sizes and availability can vary by region and subscription.

---

# 💾 2️⃣ OS Disk

The **OS disk** contains the operating system used by the VM.

Examples:

* Ubuntu Linux
* Debian
* Red Hat Enterprise Linux
* Windows Server

Example:

```text
Azure VM
   |
   v
OS Disk
   |
   +-- Operating System
   +-- System Files
   +-- Installed Software
```

The OS disk is required for the VM to boot.

---

# 💽 3️⃣ Data Disk

A **data disk** is used to store application or user data separately from the operating system.

Example:

```text
Azure VM
   |
   +-- OS Disk
   |      |
   |      +-- Operating System
   |
   +-- Data Disk
          |
          +-- Application Data
          +-- Database Data
          +-- Files
```

Data disks are useful when applications require additional persistent storage.

---

# 🌐 4️⃣ Network Interface

A **Network Interface (NIC)** connects the VM to an Azure Virtual Network.

The NIC handles network connectivity for the VM.

```text
Virtual Machine
      |
      v
Network Interface
      |
      v
Subnet
      |
      v
Virtual Network
```

A VM can have one or more network interfaces depending on its configuration and VM capabilities.

---

# 🌍 5️⃣ Public IP

A **Public IP address** allows a resource to communicate with the internet when the architecture requires public connectivity.

For example, you might use a public IP to connect to a VM from the internet.

```text
Internet
    |
    v
Public IP
    |
    v
Network Interface
    |
    v
Azure VM
```

> ⚠️ A public IP is not automatically required for every VM. Private connectivity, VPN, Bastion, or other architectures can be used instead.

---

# 🛡️ 6️⃣ Network Security Group

A **Network Security Group (NSG)** contains rules that allow or deny network traffic.

NSGs can control inbound and outbound traffic.

Example:

```text
Internet
    |
    v
NSG
    |
    +-- Allow SSH 22
    +-- Allow HTTP 80
    +-- Allow HTTPS 443
    +-- Deny Other Traffic
    |
    v
VM
```

### Example Rule

```text
Protocol: TCP
Port: 22
Source: Your IP
Action: Allow
```

For Windows administration, Remote Desktop commonly uses:

```text
TCP Port: 3389
```

> 🔐 For production environments, avoid opening administrative ports to the entire internet whenever possible. Restrict access to trusted sources or use secure access mechanisms such as Azure Bastion.

---

# ☁️ 7️⃣ Virtual Network

An **Azure Virtual Network (VNet)** provides private networking for Azure resources.

Example:

```text
Virtual Network
      |
      +-- Subnet 1
      |      |
      |      +-- VM
      |
      +-- Subnet 2
             |
             +-- Application
```

A VNet allows Azure resources to communicate securely within a network architecture.

---

# 📡 8️⃣ Subnet

A **Subnet** is a smaller network segment inside a Virtual Network.

Example:

```text
VNet: 10.0.0.0/16
       |
       +-- Subnet: 10.0.1.0/24
       |       |
       |       +-- VM
       |
       +-- Subnet: 10.0.2.0/24
               |
               +-- Application
```

Subnets are commonly used to organize workloads and apply networking controls.

---

# 🔐 VM Authentication

When creating an Azure VM, you need a way to authenticate.

For Linux VMs, **SSH keys** are generally preferred over passwords.

```text
Linux VM
   |
   v
SSH
   |
   +-- Username
   +-- Private Key
   +-- Public Key
```

For Windows VMs, username/password authentication is commonly available, depending on the configuration.

> 🔐 Never commit private SSH keys, passwords, or other secrets to GitHub.

---

# 🛠️ Create VM Using Azure Portal

## Step 1 — Open Azure Portal

Open the Azure Portal:

[Azure Portal](https://portal.azure.com/?utm_source=chatgpt.com)

Sign in with your Microsoft/Azure account.

---

## Step 2 — Search for Virtual Machines

At the top of the portal:

1. Click **Search**.
2. Type:

```text
Virtual machines
```

3. Select **Virtual machines**.
4. Click **+ Create**.
5. Select **Azure virtual machine**.

---

## Step 3 — Configure Basics

Under the **Basics** tab, configure:

### Project Details

```text
Subscription:
Azure subscription 1

Resource Group:
rg-azure-learning
```

You can use the Resource Group created in your previous Azure Fundamentals lab.

---

## Step 4 — Configure VM Details

Example learning configuration:

```text
Virtual machine name:
vm-azure-learning

Region:
Central India

Image:
Ubuntu Server

VM architecture:
x64

Size:
Select an available small/low-cost size
```

> 💡 The exact VM sizes and images available to you may vary by region and subscription.

---

# 🔐 Step 5 — Configure Administrator Account

For a Linux VM, select:

```text
Authentication type:
SSH public key
```

Provide:

```text
Username:
azureuser

SSH public key:
<your-public-key>
```

For learning, SSH key authentication is recommended.

---

# 🌐 Step 6 — Configure Networking

Configure the networking settings.

Example:

```text
Virtual Network:
vnet-azure-learning

Subnet:
subnet-vm

Public IP:
Create new

NIC network security group:
Basic
```

For a learning VM, you may allow SSH access from your current IP rather than from all internet addresses.

---

# 💾 Step 7 — Configure Disks

Review the disk configuration.

Example:

```text
OS Disk:
Managed Disk

OS Disk Type:
Standard SSD
```

For learning environments, use an economical disk configuration that meets your needs.

---

# 🔍 Step 8 — Review + Create

Click:

**Review + create**

Azure will validate the configuration.

If validation succeeds:

```text
Validation passed
```

Click:

**Create**

Azure will deploy the VM and associated resources.

---

# 🎉 Step 9 — Verify the VM

After deployment:

```text
Azure Portal
     |
     v
Virtual Machines
     |
     v
vm-azure-learning
```

Check:

* VM Status
* Public IP
* Private IP
* VM Size
* Operating System
* Disks
* Networking
* Activity Log

---

# 💻 Connect to Linux VM Using SSH

After the VM is running, copy its public IP address.

Example:

```bash
ssh azureuser@<public-ip>
```

If your SSH private key is stored locally:

```bash
ssh -i ~/.ssh/id_rsa azureuser@<public-ip>
```

Example:

```bash
ssh -i ~/.ssh/azure_vm_key azureuser@20.x.x.x
```

Once connected:

```text
azureuser@vm-azure-learning
```

You are now connected to the Azure Linux VM.

---

# 💻 Create VM Using Azure CLI

Azure CLI can be used to create a VM from the command line.

## Step 1 — Login

```bash
az login
```

---

## Step 2 — Select Subscription

List subscriptions:

```bash
az account list
```

Set the desired subscription:

```bash
az account set --subscription "<subscription-name-or-id>"
```

---

## Step 3 — Create Resource Group

If you don't already have one:

```bash
az group create \
  --name rg-azure-learning \
  --location centralindia
```

---

## Step 4 — Create Virtual Machine

Example:

```bash
az vm create \
  --resource-group rg-azure-learning \
  --name vm-azure-learning \
  --image Ubuntu2204 \
  --admin-username azureuser \
  --generate-ssh-keys
```

This command creates a Linux VM and generates SSH keys if required.

> 💡 The available image identifier can change over time. If `Ubuntu2204` is unavailable, check the currently available images in your region.

---

# 🔐 Allow SSH Access

If SSH access is not already configured as expected, you can add an NSG rule.

Example:

```bash
az vm open-port \
  --resource-group rg-azure-learning \
  --name vm-azure-learning \
  --port 22
```

For production workloads, restrict administrative access rather than exposing SSH broadly.

---

# 🌐 Get VM Public IP

Use:

```bash
az vm show \
  --resource-group rg-azure-learning \
  --name vm-azure-learning \
  --show-details \
  --query publicIps \
  --output tsv
```

Example output:

```text
20.x.x.x
```

---

# 💻 Connect Using SSH

```bash
ssh azureuser@<public-ip>
```

Example:

```bash
ssh azureuser@20.x.x.x
```

---

# ▶️ Start a VM

To start a stopped VM:

```bash
az vm start \
  --resource-group rg-azure-learning \
  --name vm-azure-learning
```

---

# ⏹️ Stop a VM

```bash
az vm stop \
  --resource-group rg-azure-learning \
  --name vm-azure-learning
```

> 💡 Stopping a VM and deallocating it are not exactly the same. For cost control, deallocation is often important because compute billing can continue for some stopped-but-not-deallocated states.

To deallocate:

```bash
az vm deallocate \
  --resource-group rg-azure-learning \
  --name vm-azure-learning
```

---

# 🔄 Restart a VM

```bash
az vm restart \
  --resource-group rg-azure-learning \
  --name vm-azure-learning
```

---

# 📋 View VM Information

```bash
az vm show \
  --resource-group rg-azure-learning \
  --name vm-azure-learning
```

For a simpler overview:

```bash
az vm show \
  --resource-group rg-azure-learning \
  --name vm-azure-learning \
  --show-details
```

---

# 🗑️ Delete Azure VM

To delete the VM:

```bash
az vm delete \
  --resource-group rg-azure-learning \
  --name vm-azure-learning
```

You will be asked to confirm the deletion unless you provide the appropriate confirmation option.

> ⚠️ Deleting a VM does not necessarily delete every separately managed resource associated with it, such as disks, public IPs, or NICs. Review the resources before deleting them if your goal is to remove all associated resources.

---

# 💰 VM Cost Considerations

Azure VMs are generally charged based on resource usage and configuration.

Costs can come from:

* VM compute
* Managed disks
* Public IP
* Network traffic
* Other attached resources

For learning environments:

```text
Create VM
    |
    v
Practice
    |
    v
Stop / Deallocate
    |
    v
Delete When Finished
```

> 💡 Always check the current Azure pricing for your selected VM size, region, disks, and related resources.

---

# 🔄 Azure VM Lifecycle

```text
Create
  |
  v
Start
  |
  v
Running
  |
  +------> Restart
  |
  +------> Stop
  |
  +------> Deallocate
  |
  v
Delete
```

---

# 🏗️ Complete VM Architecture

```text
                         Internet
                            |
                            v
                       Public IP
                            |
                            v
                   Network Security Group
                            |
                            v
                    Network Interface
                            |
                            v
                    Azure Virtual Network
                            |
                            v
                         Subnet
                            |
                            v
                    Azure Virtual Machine
                       /           \
                      /             \
                     v               v
                 OS Disk         Data Disk
                     |
                     v
                Operating System
```

---

# 🧑‍💻 Azure VM DevOps Use Cases

Azure VMs are commonly used for:

* Jenkins servers
* GitLab runners
* Build servers
* Application servers
* Web servers
* Docker hosts
* Development environments
* Testing environments
* Self-hosted CI/CD agents
* Monitoring servers

### Example DevOps Architecture

```text
Developer
    |
    v
GitHub
    |
    v
CI/CD Pipeline
    |
    v
Azure VM
    |
    +-- Docker
    +-- Jenkins
    +-- Application
    +-- Monitoring
```

---

# 📊 Important Components Summary

| Component         | Purpose                                            |
| ----------------- | -------------------------------------------------- |
| VM Size           | Defines compute capacity                           |
| OS Disk           | Stores operating system                            |
| Data Disk         | Stores application/user data                       |
| Network Interface | Connects VM to VNet                                |
| Public IP         | Provides public network connectivity when required |
| NSG               | Controls network traffic                           |
| Virtual Network   | Provides private network infrastructure            |
| Subnet            | Divides a VNet into network segments               |

---

# 🧪 Practical Lab

## Lab Objective

Create a Linux Azure VM and connect to it using SSH.

### Architecture

```text
Resource Group
      |
      +-- Virtual Network
      |       |
      |       +-- Subnet
      |
      +-- Network Security Group
      |
      +-- Public IP
      |
      +-- Network Interface
      |
      +-- Linux Virtual Machine
              |
              +-- OS Disk
```

### Tasks

* [ ] Create Resource Group
* [ ] Create Virtual Network
* [ ] Create Subnet
* [ ] Create Linux VM
* [ ] Configure SSH authentication
* [ ] Configure NSG
* [ ] Get Public IP
* [ ] Connect using SSH
* [ ] Run Linux commands
* [ ] Stop/Deallocate VM
* [ ] Delete resources after practice

---

# 🧠 What I Learned

After completing this topic, I learned:

* What an Azure Virtual Machine is.
* How Azure VMs provide IaaS compute.
* How VM size affects compute capacity.
* The difference between OS disks and data disks.
* How NICs connect VMs to VNets.
* The purpose of Public IP addresses.
* How NSGs control network traffic.
* How VNets and subnets provide network connectivity.
* How to create a VM using Azure Portal.
* How to create a VM using Azure CLI.
* How to connect to a Linux VM using SSH.
* How to start, stop, restart, and deallocate VMs.
* Basic Azure VM cost considerations.

---

# 🎯 Key Takeaways

* 🖥️ Azure VM is an **IaaS compute service**.
* ⚙️ VM size determines available compute capacity.
* 💾 OS disks contain the operating system.
* 💽 Data disks provide additional persistent storage.
* 🌐 NIC connects the VM to an Azure VNet.
* 🛡️ NSGs control inbound and outbound network traffic.
* ☁️ VNets provide private networking.
* 📡 Subnets divide a VNet into smaller network segments.
* 🔐 SSH keys are recommended for Linux VM authentication.
* 💻 Azure VMs can be created using Portal, CLI, PowerShell, or IaC tools.
* 💰 VM and associated resource costs should be monitored carefully.
* 🚀 Azure VMs are widely used in DevOps for servers, CI/CD, Docker, and testing environments.

---

# 🚀 Next Step

After learning Azure Virtual Machines, continue with:

```text
Azure Compute
     |
     +-- Virtual Machines
     |
     +-- VM Scale Sets
     |
     +-- App Service
     |
     +-- Azure Functions
```

The next recommended topic is **Azure Virtual Machine Scale Sets (VMSS)** to understand how Azure can automatically scale multiple VM instances.
