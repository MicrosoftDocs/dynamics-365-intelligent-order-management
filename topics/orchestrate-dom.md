---
author: v-chgri
description: This topic describes how to orchestrate orders using a distributed order management (DOM) provider in Microsoft Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 07/01/2021
ms.topic: conceptual
ms.author: josaw

title: Orchestrate orders using a Distributed Order Management (DOM) provider

---

# Orchestrate orders using a Distributed Order Management (DOM) provider

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic describes how to orchestrate orders using a distributed order management (DOM) provider in Microsoft Dynamics 365 Intelligent Order Management.

> [!NOTE]
> To orchestrate orders using a DOM provider, you will need to use external DOM providers to bring orders into the system.

## Get started orchestrating orders using a DOM provider

You will need to create three individual Dataverse Connector settings, one IOM Data Transformer, and one Power Automate Management connection. 

To get started orchestrating orders using a DOM provider in Dynamics 365 Intelligent Order Management, follow these steps.

1. Go to **Getting Started \> Configure Settings**. 
1. Select **IOM Data Transformer**. 
1. Under **Connections**, select **Retrieve Connection Link**. A new tab will open. 
1. If it your first time setting up a connection, you will need to sign up for Microsoft Power Automate. Ensure you are in right Dataverse environment.  
1. Go to **Data \> Connections** and select **New Connection** and in the search bar on the right. Enter "IOM Data Transformer" and create a new connection. 
1. When the connection dialog box appears, accept it and then copy the browser link to the connection and save it locally.
1. Select **Save and Close**. 
1. Select **Microsoft Dataverse**, and then build a connector for Dataverse similar to how you built the connector for **IOM Data Transformer**. 
1. Go to **Catalog \> Add Provider** and select **Dynamics 365 Distributed Order Management**.
1. Select **Connections**. The connection reference page appears.
1. Select **Retrieve Connection Link**, and then provide a new Dataverse connection link.
1. Select **New connection**.
1. In the search box on the top right corner, enter "Dataverse." 
1. Select the plus symbol ("+") for the new Dataverse connection.
1. A **Microsoft Dataverse** dialog box appears. Select **Create** to create the connection. Look at modified in the list. 
1. Open this and retrieve the link to the URL for your connection.
1. Go to the **IOM Provider** page, select **Save**, and then select **Activate**.  
1. Select **Save and Close**.
1. To activate the provider, select **Activate**. After the provider is activated, you can add **Send to Retail DOM** node to the Orchestration journey.
1. Go to **Active Action Types** and select **Fulfillment Determination**.
1. On the **Fulfillment Determination** page under **Action Type Input Business Events**, select **Fulfillment Determination**.
1. Change the **Business Event Definition** to **New Order**.
1. Select **Save and Close**. 
1. Go to **Order Orchestration Journey** and add a **Send to DOM** node with following details:
    - **Name**: "Send to DOM" 
    - **Action Type**: "Fulfillment Determination"
    - **Input Events**: "New Order"
    - **Provider Action**: "Send Order to Retail DOM"
    - **Output Events**: "Send Order to Fullfillment Determination"
1. Publish your orchestration. This will help you orchestrate orders imported from different providers. It will not run for orders that are created within Intelligent Order Management or within Dataverse directly. 


