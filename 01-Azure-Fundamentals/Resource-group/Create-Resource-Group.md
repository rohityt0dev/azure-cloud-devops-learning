# 🏢 Method 1: Create Resource Group Using Azure Portal

This guide explains how to create an **Azure Resource Group** using the **Azure Portal**.

A Resource Group is a logical container used to organize and manage related Azure resources.

---

## 🎯 Objective

By completing this lab, you will learn how to:

* Access the Azure Portal
* Find Resource Groups
* Create a new Resource Group
* Select an Azure Subscription
* Select a region
* Verify the Resource Group

---

# 🖥️ Step 1 — Open Azure Portal

Go to the Azure Portal:

[Azure Portal](https://portal.azure.com/?utm_source=chatgpt.com)

Sign in using your Microsoft/Azure account.

After successful login, you will see the Azure Portal dashboard.

---

# 🔎 Step 2 — Search for Resource Groups

After logging in:

1. Click **Search** at the top of the Azure Portal.
2. Type:

```text
Resource groups
```

3. Select **Resource groups** from the search results.

You should see a page similar to:

```text
Resource groups

+ Create
```

---

# ➕ Step 3 — Click Create

Click:

**+ Create**

Azure will open the **Create a resource group** page.

The creation form contains configuration options such as:

* Subscription
* Resource group name
* Region

---

# 💳 Step 4 — Select Your Subscription

Under **Subscription**, select the Azure subscription that you want to use.

Example:

```text
Subscription:
Azure subscription 1
```

If you are using an Azure free or trial subscription, select the subscription available in your account.

> 💡 Make sure you are using the intended subscription before creating resources because resources created under a subscription contribute to that subscription's usage and costs.

---

# 🏷️ Step 5 — Enter Resource Group Name

Enter a meaningful and consistent Resource Group name.

For your Azure learning environment, I recommend:

```text
rg-azure-learning
```

Other examples:

```text
rg-devops-learning
rg-terraform-learning
rg-azure-project
rg-production
```

### Recommended Naming

For this lab, use:

```text
Resource Group:
rg-azure-learning
```

> 💡 Using a consistent naming convention makes your Azure environment easier to understand and manage.

---

# 🌍 Step 6 — Select Region

Select a region for the Resource Group.

For learning from India, you can consider:

```text
Central India
```

or:

```text
South India
```

For this lab, use:

```text
Central India
```

### Configuration

Your configuration should look similar to:

```text
Subscription:     Azure subscription 1
Resource group:   rg-azure-learning
Region:           Central India
```

> ⚠️ **Important:** The Resource Group's region is where its metadata is stored. Resources inside the Resource Group can be deployed in different Azure regions, subject to each service's capabilities and requirements.

---

# ✅ Step 7 — Review + Create

After entering all the required information:

Click:

**Review + create**

Azure will validate your configuration.

You should see:

```text
Validation passed
```

If validation succeeds, click:

**Create**

Azure will create the Resource Group.

---

# 🎉 Step 8 — Verify the Resource Group

After deployment completes, open the newly created Resource Group.

You should see:

```text
rg-azure-learning
```

The Resource Group will initially contain no resources unless you created resources as part of another deployment.

Example:

```text
rg-azure-learning
       |
       +-- Resources
              |
              +-- No resources yet
```

Later, you can add resources such as:

```text
rg-azure-learning
       |
       +-- Virtual Machine
       +-- Storage Account
       +-- Virtual Network
       +-- Public IP
       +-- Network Interface
```

---

# 🔄 Complete Workflow

```text
Azure Portal
     |
     v
Search "Resource Groups"
     |
     v
Resource Groups
     |
     v
+ Create
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
     |
     v
Validation Passed
     |
     v
Create
     |
     v
Resource Group Created
```

---

# 📋 Lab Configuration

| Setting         | Value                |
| --------------- | -------------------- |
| Subscription    | Azure subscription 1 |
| Resource Group  | `rg-azure-learning`  |
| Region          | Central India        |
| Creation Method | Azure Portal         |

---

# 🧪 Verification Checklist

After creating the Resource Group, verify:

* [ ] Resource Group exists
* [ ] Correct subscription selected
* [ ] Resource Group name is correct
* [ ] Region is correct
* [ ] Resource Group status is available
* [ ] Resource Group can be opened successfully

---

# 📸 Screenshot

Add your Azure Portal screenshot here after completing the lab.

```text
📸 Screenshot:
Azure Portal → Resource Groups → rg-azure-learning
```

Example Markdown:

```markdown
![Azure Resource Group](./images/resource-group-created.png)
```

---

# 🧠 What I Learned

After completing this lab, I learned how to:

* Access the Azure Portal.
* Find Resource Groups.
* Create a Resource Group.
* Select an Azure Subscription.
* Select a Resource Group region.
* Verify a newly created Resource Group.
* Understand the basic Azure resource organization workflow.

---

# 🚀 Next Step

After creating the Resource Group, the next step is to create an Azure resource inside it.

For example:

```text
Resource Group
      |
      v
Create Virtual Machine
      |
      v
Configure Networking
      |
      v
Deploy VM
      |
      v
Monitor Resource
```

This will help build practical Azure cloud administration skills.
