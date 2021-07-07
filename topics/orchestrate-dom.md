---
author: v-chgri
description: This topic describes how to orchestrate orders using a distributed order management (DOM) provider in Microsoft Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 07/06/2021
ms.topic: conceptual
ms.author: josaw

title: Set up a Distributed Order Management (DOM) provider

---

# Set up a Distributed Order Management (DOM) provider

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic describes how to set up distributed order management (DOM) providers in Microsoft Dynamics 365 Intelligent Order Management.

> [!NOTE]
> To orchestrate orders using a DOM provider, you will need to use external DOM providers to bring orders into the system.

## Create the connections

To configure Intelligent Order Management so that you can orchestrate orders using a DOM provider, you will first need to create three Dataverse connections, one IOM Data Transformer connection, and one Power Automate Management connection. 

To create the connections, follow these steps. 

1. Go to **Getting Started \> Configure Settings**. 
1. On the **Active IOM Platform Connection References** page, select **IOM Data Transformer**. 
1. Under **Connections**, select **Retrieve Connection Link** to open Microsoft Power Automate in a new tab. If it your first time setting up a connection, you will need to sign up for Microsoft Power Automate. Ensure that you are in right Dataverse environment.  
1. Go to **Data \> Connections**. Select **New Connection**, and in the search bar on the top right enter "IOM Data Transformer" and create a new connection. 
1. When the connection dialog box appears, accept it and then copy the browser link to the connection.
1. Select **Save and Close**. 
1. On the **Active IOM Platform Connection References** page, select **Microsoft Dataverse**, and then build a connector for Dataverse similar to how you built the connector for **IOM Data Transformer**. 
1. Go to **Providers \>Catalog** and select **Add Provider** on the **Dynamics 365 Distributed Order Management** tile.
1. Select **Connections**. The connection reference page appears.
1. Select **Retrieve Connection Link**, and then provide a new Dataverse connection link.
1. Select **New connection**.
1. In the search box on the top right corner, enter "Dataverse" to filter for Dataverse connections. 
1. For the new Dataverse connection, select the plus symbol ("+").
1. A **Microsoft Dataverse** dialog box appears. Select **Create** to create the connection.  
1. On the **Connections in IOM** page, you should see the new connection in the list with staus **Connected**. Select the new connection and retrieve the link to the URL for your connection.
1. Go to the **IOM Provider** page, select **Save**, and then select **Activate**.  
1. Select **Save and Close**.

## Activate the provider

Next, you must activate the provider. To activate the provider, follow these steps.

1. Go to **Catalog \> Add Provider** and select **Dynamics 365 Distributed Order Management**.
1. Select **Activate**. It will take some time to activate. The provider action is created automatically. 

## Configure and publish the orchestration

After the provider is activated, you can add the **Send to Retail DOM** node to the orchestration journey and publish.

To configure and publish your orchestration, follow these steps.

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


