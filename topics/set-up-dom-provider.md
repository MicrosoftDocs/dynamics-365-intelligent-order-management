---
author: v-chgri
description: This topic describes how to orchestrate orders using a distributed order management (DOM) provider in Microsoft Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 07/08/2021
ms.topic: conceptual
ms.author: josaw

title: Set up Distributed Order Management provider

---

# Set up Distributed Order Management provider

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic describes how to set up Distributed Order Management (DOM) provider in Microsoft Dynamics 365 Intelligent Order Management. For information about DOM, refer to the [Distributed Order Management (Preview)](dom.md) topic.

> [!NOTE]
> To orchestrate orders using DOM provider, you will need to use external DOM providers to bring orders into the system.


## Add DOM provider

1. Go to **Providers \>Catalog** and select **Add Provider** on the **Dynamics 365 Distributed Order Management** tile.
1. Select **Connections**. The **Dynamics 365 Distributed Order Management Dataverse (current environment) Connection** connection reference page appears.
1. Select **Retrieve Connection Link**, and then copy the connection URL.
1. Select **New connection**.
1. In the search box on the top right corner, enter "Dataverse" to filter for Dataverse connections. 
1. Select the plus symbol ("+") next to the new Dataverse connection.
1. A **Microsoft Dataverse** dialog box appears. Select **Create** to create the connection.  
1. On the **Connections in IOM** page, you should now see the new connection in the list with status **Connected**. Select the new connection and paste the copied URL into the **Connection URL** field.
1. Go to the **Dynamics 365 Distributed Order Management Dataverse (current environment) Connection** connection reference page, select **Save**, and then select **Activate**.  
1. Select **Save and Close**.
1. Go to **Catalog \> Add Provider** and select **Dynamics 365 Distributed Order Management**.
1. Select **Activate**. It will take some time to activate. The provider action is created automatically. 


## Configure and publish the orchestration

To configure and publish your orchestration, follow these steps.

1. Go to **Order Orchestration Journey** and add a **Send to DOM** node with following details:
    - **Name**: "Send to DOM" 
    - **Action Type**: "Fulfillment Determination"
    - **Input Events**: "New Order"
    - **Provider Action**: "Send Order to Retail DOM"
    - **Output Events**: "Send Order to Fulfillment Determination"
1. Publish your orchestration. This will help you orchestrate orders imported from different providers. It will not run for orders that are created within Intelligent Order Management or within Dataverse directly. 

## Additional resources
[Distributed Order Management (Preview)](dom.md) 
[Orchestration flows](orchestration-flows.md)

