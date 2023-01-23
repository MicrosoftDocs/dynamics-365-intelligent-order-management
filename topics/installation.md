---
author: raybennett-msft
description: This article describes how to create an environment and install Intelligent Order Management as a standalone application.
ms.author: bennettray
ms.date: 01/23/2023
ms.topic: conceptual

title: Dynamics 365 Intelligent Order Management Installation

---

# Install Dynamics 365 Intelligent Order Management

## Create an environment
Before you install Dynamics 365 Intelligent Order Management, you'll need to create an environment. If you're integrating with Dynamics 365 finance and operations apps and have set up Dual-write, an environment will already have been for you. After the environment is created, the instructions remain the same.

If you don't aleady have an environment, complete the following steps. 

1. Go to the [Power Platform admin center](https://admin.powerplatform.microsoft.com) and on the left navigation pane, select **Environments** > **New**.
2.	In the **Name** field, name the environment and in the **Type** field, select **Sandbox** or **Production**, depending on what you are deploying.
3.	Set the **Create a database for this environment** slider to **Yes** and then select **Next**.
4.	On the next screen, select your preferred options for language and currency.
5. Set the **Enable Dynamics 365 apps** to **Yes**. If you don't select this option, you'll need to recreate the environment because the key data model for Intelligent Order Management will be missing. 
6. Make sure that the **Automatically deploy these apps** field is set to **None**. Intelligent Order Management isn't a default app that can be deployed. 
7. Select **Save**. You'll get a message that your environment is **Preparing**, and the **State** will be **PreparingInstance**. Your environment will change to the **Ready** state when it's complete. Creating the environment should take less than one hour.

## Install Intelligent Order Management
Complete the following steps to install Dynamics 365 Intelligent Order Management into your environment.

1.	Select on the environment that you want to use.
2.	Go to **Resources** > **Dynamics 365 Apps**.
3.	Select **Install app**.
4.	In the list, find and select **Dynamics 365 Intelligent Order Management**. 
5.	Select **Next**, select to agree to the Terms of Service, and then select **Install**. Installation may take a few hours.
 
While it's installing, you can use the Refresh button to see when it has completed.

## Next Steps
[Configuring Intelligent Order Management](setup.md)
