# Task 3: Verify VMs and Subnets in the Portal

## Overview
In this task, you will verify that both Virtual Machines were deployed correctly into separate subnets inside the Virtual Network.

---

## Steps

1. In the Azure Portal, click **Resource groups** in the left menu and select your resource group:
   **<inject key="resourceGroupName" enableCopy="true"></inject>**

2. Confirm you can see the following resources in the list:

   | Resource Name | Type |
   |---|---|
   | `nsg1` | Network Security Group |
   | `vnet1` | Virtual Network |
   | `WindowsVM1` | Virtual Machine |
   | `WindowsVM2` | Virtual Machine |

3. Click on **vnet1** → then click **Subnets** in the left menu.

4. Confirm there are **2 subnets** listed: `subnet1` and `subnet2`.

5. Go back to the resource group and click on **WindowsVM1**.

6. Click **Networking** in the left menu and confirm the **Subnet** shows `subnet1`.

7. Go back and click on **WindowsVM2**.

8. Click **Networking** in the left menu and confirm the **Subnet** shows `subnet2`.

   > **Note:** Each VM must be in a different subnet. This provides network-level isolation between the two machines.

---

## Summary

You have successfully:
- ✅ Verified all resources were created in the resource group
- ✅ Confirmed VNet has 2 subnets
- ✅ Confirmed WindowsVM1 is in `subnet1`
- ✅ Confirmed WindowsVM2 is in `subnet2`

Click **Next** to proceed to Task 4.
