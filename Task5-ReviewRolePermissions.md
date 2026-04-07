# Task 5: Review What the Custom Role Allows

## Overview
In this task, you will explore the custom role definition to understand exactly what permissions it grants and why those specific permissions were chosen.

---

## Steps

1. In your resource group, click **Access control (IAM)** in the left menu.

2. Click the **Roles** tab at the top.

3. In the search box, type **Custom-VM-Network-Storage-Role** and press Enter.

4. Click on the role name in the results.

5. Click **View** to open the role permissions.

6. Under the **Permissions** section, confirm the role includes the following:

   | Permission | What It Allows |
   |---|---|
   | `virtualMachines/start/action` | Start a stopped VM |
   | `virtualMachines/deallocate/action` | Stop and deallocate a VM |
   | `virtualMachines/read` | View VM details |
   | `virtualNetworks/write` | Update VNet and DNS settings |
   | `networkSecurityGroups/write` | Modify NSG inbound/outbound rules |
   | `Microsoft.Storage/*` | Full access to Storage resources |

7. Confirm the **NotActions** section is empty — meaning nothing is explicitly blocked within the allowed actions.

   > **Important:** Notice that the role does **NOT** include `delete` for VMs or the ability to create new Resource Groups. This follows the principle of **Least Privilege** — users only get what they need, nothing more.

---

## Summary

You have successfully:
- ✅ Located the custom role in the Roles tab
- ✅ Reviewed all permissions granted by the role
- ✅ Understood what is NOT allowed by the role

Click **Next** to proceed to Task 6.
