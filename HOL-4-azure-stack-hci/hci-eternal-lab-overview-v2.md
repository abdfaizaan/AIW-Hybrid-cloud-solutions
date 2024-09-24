# Hybrid Cloud Solution - Azure Stack HCI

### Overall Estimated Duration: 8 hours

## Overview

HCIBox is a turnkey solution that provides a complete sandbox for exploring Azure Stack HCI capabilities and hybrid cloud integration in a virtualized environment. HCIBox is designed to be completely self-contained within a single Azure subscription and resource group, which will make it easy for a user to get hands-on with Azure Stack HCI and Azure Arc technology without the need for physical hardware.

Azure Stack HCI 23H2 is now generally available. 23H2 simplifies the configuration and deployment of HCI clusters and related workloads, like VM management for VM self-service management in the Azure portal. HCIBox has also been updated and now offers clusters built on the new 23H2 OS, and prior Azure Stack HCI releases are no longer part of HCIBox or supported by the Jumpstart team. If you've used earlier versions of HCIBox, you should read this guide thoroughly to understand the new HCIBox deployment process.

### Azure Stack HCI capabilities are available in HCIBox

**2-node Azure Stack HCI cluster**

HCIBox automatically creates and configures a two-node Azure Stack HCI cluster using nested virtualization with Hyper-V running on an Azure Virtual Machine. This Hyper-V host creates three guest virtual machines: two Azure Stack HCI nodes (AzSHost1, AzSHost2), and one nested Hyper-V host (AzSMGMT). AzSMGMT itself hosts two guest VMs: an Active Directory domain controller and a Routing and Remote Access Server acting as a virtual router.

  ![](./media/hci24-overview-3.png)

**Virtual machine management**: HCIBox comes with guest VM management in the Azure portal. The HCIBox documentation will walk you through how to use this feature, including configuring VM images from Azure Marketplace and creating VMs on your cluster.

**Azure Kubernetes Service on Azure Stack HCI**: Azure Stack HCI includes Azure Kubernetes Services on Azure Stack HCI (AKS hybrid) as part of the default configuration. A user script is provided that can be used to create a workload cluster.

## Objective

To create a flexible and cost-effective hybrid cloud environment that seamlessly integrates on-premises and cloud resources, enabling organizations to optimize performance, streamline management, and enhance scalability while ensuring security and compliance. This approach allows businesses to leverage existing investments, modernize applications, and improve disaster recovery and backup capabilities, ultimately driving innovation and agility in a rapidly evolving digital landscape.

- **Preparing env with the prerequisites to deploy Azure Stack HCI:** Ensure the infrastructure meets all necessary requirements for a successful Azure Stack HCI deployment, enabling efficient resource utilization and performance.
  
- **Deploying JumpStart-HCIBox in Azure Portal:** Quickly provision a ready-to-use Azure Stack HCI environment using JumpStart-HCIBox for streamlined setup, accelerating time to value for cloud initiatives.

- **Verify the JumpStart HCI Box deployment:** Confirm the successful deployment of the JumpStart HCI Box to ensure readiness for subsequent configurations, minimizing potential issues during production rollout.
  
- **Configure and monitor cluster performance from the Windows Admin Center dashboard:** Set up and track cluster performance metrics through the Windows Admin Center for effective resource management, allowing proactive identification of performance bottlenecks.
  
- **Azure Backup Server on Azure Stack:** Implement Azure Backup Server to enhance data protection and recovery capabilities within Azure Stack HCI, ensuring business continuity and compliance with data retention policies.
  
- **Managing AKS on Azure Stack HCI:** Oversee and optimize Azure Kubernetes Service (AKS) deployments on Azure Stack HCI for efficient container orchestration, facilitating rapid application development and deployment.
  
- **Azure Stack HCI VM Provisioning:** Facilitate the rapid creation and deployment of virtual machines within the Azure Stack HCI environment, enhancing operational efficiency and resource allocation.
  
- **Azure Stack HCI Update management using Azure Portal:** Streamline the update management process for Azure Stack HCI through the Azure Portal for improved system reliability and security, ensuring the infrastructure is always up-to-date with the latest features and patches.

## Prerequisites

Participants should have:

- **Basic Cloud Knowledge:** Understanding of cloud computing concepts, including IaaS, PaaS, and SaaS.
- **Familiarity with Azure Services:** Basic knowledge of Azure services and the Azure Portal interface.
- **Networking Fundamentals:** Understanding of networking concepts, such as IP addressing, subnets, and routing, which are crucial for configuring hybrid environments.
- **Windows Server Knowledge:** Proficiency with Windows Server, including installation, configuration, and management, as Azure Stack HCI runs on Windows Server technology.
- **Virtualization Concepts:** Familiarity with virtualization technologies, including Hyper-V, as Azure Stack HCI utilizes Hyper-Converged Infrastructure.
- **PowerShell Basics:** Basic knowledge of PowerShell for scripting and automation tasks in Azure and Azure Stack environments.
- **Storage Fundamentals:** Understanding of storage technologies and concepts, including SAN, NAS, and local storage, which are relevant to HCI setups.
- **Backup and Disaster Recovery Concepts:** Awareness of backup strategies and disaster recovery planning to effectively implement Azure Backup Server.
- **Kubernetes Basics:** Familiarity with containerization and Kubernetes concepts, especially for managing AKS on Azure Stack HCI.

## Architechture

The architecture of a Hybrid Cloud Solution using Azure Stack HCI integrates on-premises infrastructure with Azure services, creating a cohesive and flexible environment. At the core, Azure Stack HCI utilizes a hyper-converged infrastructure powered by Windows Server and Hyper-V, enabling efficient virtualization and storage management through Storage Spaces Direct. This on-premises setup connects seamlessly to Azure services via the Azure Portal, allowing organizations to leverage cloud capabilities such as Azure Backup, Azure Kubernetes Service (AKS), and Azure Site Recovery. Management and monitoring are facilitated through Windows Admin Center, providing a unified interface for performance tracking and configuration. The architecture supports a hybrid model that ensures data locality, optimized workload placement, and enhanced disaster recovery, empowering businesses to scale their operations while maintaining control over their data and resources.

## Architechture Diagram

![](./media/hci24-overview-2.png)

## Explanation of Components

The architecture for this lab involves the following key components:

- **Azure Stack HCI:** The primary infrastructure service providing a hyper-converged environment that integrates with Azure.
- **Azure Backup:** A service that provides backup and disaster recovery capabilities for on-premises and cloud-based resources.
- **Azure Kubernetes Service (AKS):** A managed container orchestration service that can run on Azure Stack HCI for deploying and managing containerized applications.
- **Azure Monitor:** A service for monitoring application performance and infrastructure health, offering insights into the operation of Azure Stack HCI environments.
- **Azure Site Recovery:** A disaster recovery service that can be used to replicate on-premises workloads to Azure for business continuity.
- **Windows Server:** The underlying operating system that runs Azure Stack HCI, providing the necessary virtualization capabilities.
- **Hyper-V:** The virtualization technology used in Azure Stack HCI to host virtual machines.
- **Windows Admin Center:** A management tool for configuring and monitoring the Azure Stack HCI cluster and its resources.

## Getting Started with the Lab
 
Welcome to your Hybrid Cloud Solution - Azure Stack HCI Workshop! We've prepared a seamless environment for you to explore and learn about Azure services. Let's begin by making the most of this experience:
 
## Accessing Your Lab Environment

Once you're ready to dive in, your virtual machine and lab guide will be right at your fingertips within your web browser.

  ![](../media/labguide.png)

### Virtual Machine & Lab Guide
 
Your virtual machine is your workhorse throughout the workshop. The lab guide is your roadmap to success.
 
## Exploring Your Lab Resources
 
To get a better understanding of your lab resources and credentials, navigate to the **Environment** tab.
 
  ![](../media/env01.png)
 
## Utilizing the Split Window Feature
 
For convenience, you can open the lab guide in a separate window by selecting the **Split Window** button from the Top right corner.
 
  ![](../media/split01.png)
 
## Managing Your Virtual Machine
 
Feel free to start, stop, or restart your virtual machine as needed from the **Resources** tab. Your experience is in your hands!

  ![](../media/resourses.png)

## Login to the Azure portal

1. In the **HCIBox-Client** virtual machine, double-click on the Microsoft Edge browser shortcut that is provided on the desktop.
  
   ![](media/hci-env2.png "Select Azure Portal")
    
1. Navigate to Azure Portal using the URL provided here: `https://portal.azure.com/`. On the **Sign into Microsoft Azure** tab, you will see the login prompt. Enter the following **Email/Username**, and then click on **Next**. 
      
   * Email/Username: **<inject key="AzureAdUserEmail"></inject>**
   
1. Now, enter the **password** that you have already received for the above account.
      
   * Password: **<inject key="AzureAdUserPassword"></inject>**

1. On the **Action Required** pop-up click on **Ask later**.     

1. If you see the pop-up **Stay signed in?** Click **No**.

1. If you see the pop-up, **You have free Azure Advisor recommendations!** close the window to continue the lab.

1. If the **Welcome to Microsoft Azure** popup window appears, click **Cancel** to skip the tour.

1. Navigate to the Resource Group in the Azure portal navigation section.

   ![](.././media/navigate-resource-group.png "Select Resource Group from Navigate Option")

1. From the **Resource** groups pane, click on the **AzureStakHCI** resource group and verify the resources present in it.

   ![](media/azurestackhci-rg.png "Select Azure Stack HCI Resource Group")


## Support Contact
 
The CloudLabs support team is available 24/7, 365 days a year, via email and live chat to ensure seamless assistance at any time. We offer dedicated support channels tailored specifically for both learners and instructors, ensuring that all your needs are promptly and efficiently addressed.

Learner Support Contacts:
- Email Support: labs-support@spektrasystems.com
- Live Chat Support: https://cloudlabs.ai/labs-support

Now, click on **Next** from the lower right corner to move on to the next page.

![](../media/lab-next.png)

### Happy Learning!!
