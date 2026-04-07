# Task 2: Deploy the ARM Template

## Overview
In this task, you will run a single PowerShell command in Cloud Shell to deploy all Azure resources — VMs, VNet, NSG, and the RBAC role assignment.

---

## Steps

1. In Cloud Shell, run the following command to deploy all resources:

   ```powershell
   New-AzResourceGroupDeployment `
     -Name "LabDeployment" `
     -ResourceGroupName "<inject key="resourceGroupName" enableCopy="true"></inject>" `
     -TemplateUri "https://raw.githubusercontent.com/your-org/arm-lab/main/azuredeploy.json" `
     -TemplateParameterUri "https://raw.githubusercontent.com/your-org/arm-lab/main/azuredeploy.parameters.json"
   ```

   > **Note:** This will take approximately **10–15 minutes**. Wait until you see `ProvisioningState : Succeeded` before moving on.

2. Once the deployment is complete, you will see an output section in the terminal. It will show the **DNS names and IP addresses** of both VMs — copy these for later.

   Example output:
   ```
   DeploymentName     : LabDeployment
   ProvisioningState  : Succeeded
   Outputs:
     vm1PublicDNS     : vm1dns****.centralindia.cloudapp.azure.com
     vm2PublicDNS     : vm2dns****.centralindia.cloudapp.azure.com
   ```

---

## Summary

You have successfully:
- ✅ Deployed the full ARM template using one command
- ✅ Confirmed `ProvisioningState : Succeeded`

Click **Next** to proceed to Task 3.
