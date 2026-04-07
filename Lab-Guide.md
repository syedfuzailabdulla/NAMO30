# Lab: Deploy Azure Infrastructure with ARM Templates and RBAC

## Overview

In this lab, you will deploy a pre-built ARM template that creates a basic Azure network with two Virtual Machines. Then you will verify that a custom RBAC role was assigned to your user — giving limited permissions to manage VMs and network resources.

**Duration:** 45 minutes

---

## Getting Started

1. Open a browser and go to [https://portal.azure.com](https://portal.azure.com)

2. Sign in with:
   - **Username:** <inject key="AzureAdUserEmail" enableCopy="true" style="color:blue"></inject>
   - **Password:** <inject key="AzureAdUserPassword" enableCopy="true" style="color:blue"></inject>

3. Click **No** if asked to stay signed in. Click **Cancel** on the Welcome popup.

---

## Exercise 1: Deploy the ARM Template

### Task 1: Open Cloud Shell

1. In the Azure Portal, click the **Cloud Shell icon** (>_) in the top toolbar.

2. If prompted to create storage, click **Create storage**. This takes about **2 minutes**.

3. Make sure the shell is set to **PowerShell** (check the dropdown at the top-left of the shell panel).

---

### Task 2: Deploy the Template

1. In Cloud Shell, run the following command to deploy all resources:

   ```powershell
   New-AzResourceGroupDeployment `
     -Name "LabDeployment" `
     -ResourceGroupName "<inject key="resourceGroupName" enableCopy="true"></inject>" `
     -TemplateUri "https://raw.githubusercontent.com/your-org/arm-lab/main/azuredeploy.json" `
     -TemplateParameterUri "https://raw.githubusercontent.com/your-org/arm-lab/main/azuredeploy.parameters.json"
   ```

   > **Note:** This will take approximately **10–15 minutes**. Wait until you see `ProvisioningState : Succeeded` before moving on.

2. Once complete, you will see two VM DNS names in the output — copy them for later.

---

### Task 3: Verify the Resources Were Created

1. In the Azure Portal, go to **Resource groups** and click on your resource group:
   **<inject key="resourceGroupName" enableCopy="true"></inject>**

2. Confirm you can see these resources:

   | Resource | Type |
   |---|---|
   | `nsg1` | Network Security Group |
   | `vnet1` | Virtual Network |
   | `WindowsVM1` | Virtual Machine |
   | `WindowsVM2` | Virtual Machine |

3. Click on **vnet1** → then click **Subnets** in the left menu. Confirm there are **2 subnets**: `subnet1` and `subnet2`.

4. Click on **WindowsVM1** → click **Networking** in the left menu. Confirm it is connected to `subnet1`.

5. Click on **WindowsVM2** → click **Networking** in the left menu. Confirm it is connected to `subnet2`.

   > **Note:** Each VM must be in a different subnet. This is the expected architecture.

---

### Task 4: Verify the RBAC Role Assignment

A custom role called **"Custom VM and Network Operator"** was automatically assigned to your account during deployment. Let's verify it.

1. In your Resource Group, click **Access control (IAM)** in the left menu.

2. Click the **Role assignments** tab.

3. Look for your username **<inject key="AzureAdUserEmail"></inject>** in the list.

4. Confirm the **Role** column shows: **Custom VM and Network Operator**

   > **Note:** If you don't see it immediately, wait 1–2 minutes and refresh the page.

---

### Task 5: Check What the Custom Role Allows

1. Still on the **Access control (IAM)** page, click the **Roles** tab.

2. In the search box, type **Custom VM and Network Operator** and click on it.

3. Click **View** to see the permissions.

4. Confirm the role includes **only** these permissions:

   | Permission | What It Allows |
   |---|---|
   | `virtualMachines/start/action` | Start a VM |
   | `virtualMachines/deallocate/action` | Stop a VM |
   | `virtualNetworks/write` | Update VNet DNS settings |
   | `networkSecurityGroups/write` | Update NSG rules |

   > **Important:** Notice that the role does **NOT** allow deleting VMs, creating new resources, or accessing subscriptions. This is the principle of **least privilege** — users only get the permissions they need.

---

### Task 6: Test the Role — Start and Stop a VM

Let's confirm the role works by starting and stopping a VM.

1. Go to **Resource groups** → your resource group → click **WindowsVM1**.

2. If the VM status is **Running**, click **Stop** at the top. Click **Yes** to confirm.
   - Wait about **2 minutes** for the VM to stop.

3. Once the status shows **Stopped (deallocated)**, click **Start** at the top.
   - Wait about **2 minutes** for the VM to start again.

4. Confirm the status returns to **Running**.

   > **Note:** You were able to do this because the custom RBAC role grants Start/Stop permissions. If you had a role without these permissions, the buttons would be greyed out or return an error.

---

## Summary

You have successfully completed the lab! Here is what you did:

| Task | Done |
|---|---|
| Deployed an ARM template with 2 VMs and a VNet | ✅ |
| Verified both VMs are in separate subnets | ✅ |
| Confirmed a custom RBAC role was assigned to your account | ✅ |
| Reviewed the limited permissions in the custom role | ✅ |
| Tested Start/Stop VM using the assigned role | ✅ |

---

## Assessment

**Q1. What is the purpose of RBAC in Azure?**

- A) To encrypt virtual machine disks
- B) To control who can access Azure resources and what they can do with them
- C) To monitor network traffic
- D) To create virtual networks automatically

**✅ Answer: B**

---

**Q2. The custom role in this lab allows which actions?**

- A) Delete VMs and create new resource groups
- B) Start/Stop VMs, update VNet DNS, and update NSG rules
- C) Full access to all Azure resources
- D) Read-only access to the subscription

**✅ Answer: B**

---

**Q3. Why were the two VMs placed in different subnets?**

- A) To reduce VM cost
- B) To allow network-level isolation and segmentation between the two machines
- C) Because Azure does not allow two VMs in the same subnet
- D) To improve VM boot speed

**✅ Answer: B**

---

**Q4. What does "least privilege" mean in the context of RBAC?**

- A) Always assign the Owner role to all users
- B) Give users only the minimum permissions they need to do their job
- C) Restrict users from accessing the Azure Portal
- D) Assign roles at the subscription level only

**✅ Answer: B**

---

**Q5. What happens if you try to delete a VM with the "Custom VM and Network Operator" role?**

- A) The VM gets deleted successfully
- B) The VM is moved to another resource group
- C) The action is denied because delete permission is not included in the role
- D) A warning is shown but the delete proceeds

**✅ Answer: C**

---

**Q6. What is a nested ARM template used for in this lab?**

- A) To deploy a second VNet
- B) To install software on the VMs
- C) To create the custom RBAC role and assign it to the user
- D) To configure the NSG inbound rules

**✅ Answer: C**
