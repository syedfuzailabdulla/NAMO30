# Task 6: Start and Stop a VM to Test the Role

## Overview
In this task, you will test the RBAC role in action by starting and stopping a Virtual Machine — confirming that your assigned role actually grants these permissions.

---

## Steps

1. In the Azure Portal, go to your resource group:
   **<inject key="resourceGroupName" enableCopy="true"></inject>**

2. Click on **WindowsVM1** from the resource list.

3. Check the current **Status** of the VM at the top of the Overview page.

**If the VM is Running — Stop it first:**

4. Click **Stop** in the top action bar.

5. Click **Yes** to confirm.

   > **Note:** This will take approximately **2 minutes**. Wait until the status shows **Stopped (deallocated)** before continuing.

**Now Start the VM:**

6. Click **Start** in the top action bar.

   > **Note:** This will take approximately **2 minutes**. Wait until the status shows **Running**.

7. Confirm the VM status returns to **Running**.

   > **Important:** You were able to Start and Stop the VM because the custom RBAC role grants `virtualMachines/start/action` and `virtualMachines/deallocate/action` permissions. If your role did not have these, the buttons would return an **Authorization Error**.

---

## Assessment

**Q1. What is the purpose of RBAC in Azure?**
- A) To encrypt virtual machine disks
- B) To control who can access Azure resources and what they can do
- C) To monitor network traffic
- D) To create virtual networks automatically

**✅ Answer: B**

---

**Q2. The custom role in this lab allows which actions?**
- A) Delete VMs and create new resource groups
- B) Start/Stop VMs, update VNet DNS, update NSG rules, and full Storage access
- C) Full access to all Azure resources
- D) Read-only access to the subscription

**✅ Answer: B**

---

**Q3. Why were the two VMs placed in different subnets?**
- A) To reduce VM cost
- B) To allow network-level isolation between the two machines
- C) Because Azure does not allow two VMs in the same subnet
- D) To improve VM boot speed

**✅ Answer: B**

---

**Q4. What does "Least Privilege" mean in RBAC?**
- A) Always assign the Owner role to all users
- B) Give users only the minimum permissions they need to do their job
- C) Restrict users from accessing the Azure Portal
- D) Assign roles at the subscription level only

**✅ Answer: B**

---

**Q5. What happens if you try to delete a VM with this custom role?**
- A) The VM gets deleted successfully
- B) The VM is moved to another resource group
- C) The action is denied because delete permission is not in the role
- D) A warning is shown but the delete proceeds

**✅ Answer: C**

---

**Q6. What is the nested ARM template used for in this lab?**
- A) To deploy a second VNet
- B) To install software on the VMs
- C) To create the custom RBAC role and assign it to the user
- D) To configure the NSG inbound rules

**✅ Answer: C**

---

## Lab Complete 🎉

**Congratulations!** You have completed the lab. Here is a summary of everything you accomplished:

| Task | Status |
|---|---|
| Opened Cloud Shell | ✅ |
| Deployed ARM template with 2 VMs and a VNet | ✅ |
| Verified VMs are in separate subnets | ✅ |
| Confirmed custom RBAC role assignment in IAM | ✅ |
| Reviewed the limited permissions in the custom role | ✅ |
| Tested Start/Stop VM using the assigned role | ✅ |
