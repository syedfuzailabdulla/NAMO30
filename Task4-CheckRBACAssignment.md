# Task 4: Check RBAC Role Assignment in IAM

## Overview
In this task, you will verify that a custom RBAC role was automatically assigned to your user account during the ARM template deployment.

---

## Steps

1. In the Azure Portal, go to your resource group:
   **<inject key="resourceGroupName" enableCopy="true"></inject>**

2. Click **Access control (IAM)** in the left menu.

3. Click the **Role assignments** tab.

4. In the list, look for your username:
   **<inject key="AzureAdUserEmail"></inject>**

5. Confirm the **Role** column shows: **Custom-VM-Network-Storage-Role**

   > **Note:** If you do not see the role assignment immediately, wait **1–2 minutes** and click the **Refresh** button at the top of the page.

6. Confirm the **Scope** column shows your resource group name — this means the role is limited to this resource group only and does not apply to the full subscription.

---

## Summary

You have successfully:
- ✅ Opened the IAM (Access Control) page
- ✅ Found your user in the Role assignments list
- ✅ Confirmed the custom role is assigned at resource group scope

Click **Next** to proceed to Task 5.
