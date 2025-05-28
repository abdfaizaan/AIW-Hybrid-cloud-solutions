# Exercise 2: Deploying Azure Local in Azure Portal

### Estimated Duration: 180 minutes

In this exercise, you will be deploying an Azure Local solution using a generated ARM template. You can deploy it either through the Azure portal by uploading the template and specifying deployment parameters or using PowerShell for automated deployment, offering flexibility and control over the deployment process. Here, you will be deploying Azure Local using PowerShell commands.

## Lab Objectives

You will be able to complete the following tasks:

- Task 1: Create and review the generated ARM template
- Task 2: Validate and deploy the Azure Local using PowerShell


## Task 1: Review the already generated ARM template


    
3. Open **File Explorer** on HCIBox-Client and navigate to the **C:\HCIBox** folder. Right-click on the **folder** and open it in **VSCode**.

4. Open and review the **hci.json** and **hci.parameters.json files** in **VSCode**. Verify that the **hci.parameters.json file** looks correct without **"-staging"** placeholder parameter values. This has been already generated with script available in Localbox folder.

    ![](./media/hci24-5.png)

## Task 2: Validate and deploy the Azure Local using PowerShell

1. Open PowerShell ISE window and run the below command to validate you Azure Local deployment and cluster.

   ```
   $TemplateFile = Join-Path -Path $env:LocalBoxDir -ChildPath "azlocal.json"
   $TemplateParameterFile = Join-Path -Path $env:LocalBoxDir -ChildPath "azlocal.parameters.json"

   New-AzResourceGroupDeployment -Name 'localcluster-validate' -ResourceGroupName $env:resourceGroup -TemplateFile $TemplateFile -TemplateParameterFile $TemplateParameterFile -OutVariable ClusterValidationDeployment -ErrorAction Stop


   ```

1. The above command will take approx. 45 mintues to get you deployment validated and showing you Azure Local cluster on Azure Portal.

1. You can navigate to Azure Portal and can see a new Azure Local resource created in your resource group.
   

1. Once the validation is completed, run the below command to start the creation of Azure Local. This command will take approx. 3 hrs to deploy your cluster. 

   ```
   New-AzResourceGroupDeployment -Name 'localcluster-deploy' -ResourceGroupName $env:resourceGroup -TemplateFile $TemplateFile -deploymentMode "Deploy" -TemplateParameterFile $TemplateParameterFile -OutVariable ClusterDeployment -ErrorAction Stop

   ```

11. Once the deployment starts, you can navigate to Azure Portal, Select you Azure Local resource and select **Deployment** tab from the left side to see your deployment status.

     ![](./media/deploymentstarted.png)
   
12. Azure Local may take 3 to 5 hours to get deployed. If you navigate elsewhere in the Azure Portal, you can return to monitor progress on the Deployments tab of the cluster resource. Click **Refresh** to get the latest status on deployment.

     ![](./media/deplomentstatehci.png)

## Summary

In this exercise, you assigned Azure Arc permission to the Azure Stack HCI resource provider, created and reviewed the generated ARM template and validated and deployed the Azure Local cluster using the Azure portal.

### You have successfully completed the lab. Click on Next >> to proceed with next exercise.
