---
author: raybennett-msft
description: This article describes how to create an environment and install Intelligent Order Management as a standalone application.
ms.author: anvenkat
ms.date: 04/12/2024
ms.custom: 
  - bap-template
ms.topic: conceptual

title: Install Dynamics 365 Intelligent Order Management

---

# Install Dynamics 365 Intelligent Order Management

## Create an environment

Before you install Microsoft Dynamics 365 Intelligent Order Management, you must create an environment. If you're integrating with finance and operations apps, and you've set up dual-write, an environment will already have been created for you. After the environment is created, the instructions remain the same.

If you don't already have an environment, follow these steps to create one.

1. Go to the [Power Platform admin center](https://admin.powerplatform.microsoft.com).
2. In the left navigation pane, select **Environments** \> **New**.
3. In the **Name** field, enter a name for the environment.
4. In the **Type** field, select **Sandbox** or **Production**, depending on the type of environment that you're deploying.
5. Set the **Create a database for this environment** option to **Yes**, and then select **Next**.
6. On the next page, select your preferred options for language and currency.
7. Set the **Enable Dynamics 365 apps** option to **Yes**. If you skip this step, you'll have to re-create the environment, because the key data model for Intelligent Order Management will be missing.
8. Make sure that the **Automatically deploy these apps** field is set to **None**. Intelligent Order Management isn't a default app that can be deployed.
9. Select **Save**. You'll receive a message that your environment is being prepared, and the environment state will be **PreparingInstance**. When the environment has been created, the state will change to the **Ready**. Creation of the environment should take less than one hour.

## Install Intelligent Order Management

Follow these steps to install Intelligent Order Management in your environment.

1. Select the environment that you want to use.
2. Go to **Resources** \> **Dynamics 365 Apps**.
3. Select **Install app**.
4. In the list, find and select **Dynamics 365 Intelligent Order Management**.
5. Select **Next**, select to agree to the Terms of Service, and then select **Install**. Installation might take a few hours. You can use the **Refresh** button to see when it has been completed.

## Next steps

[Configuring Intelligent Order Management](setup.md)
