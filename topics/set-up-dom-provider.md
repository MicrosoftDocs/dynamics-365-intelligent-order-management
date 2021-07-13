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
 
1. In Intelligent Order Management, go to **Providers \> Catalog**.
2. Select **Add Provider** on the **Dynamics 365 Distributed Order Management** tile.
3. Select **Create** on the **Terms and Conditions** page.
4. On the **Connections** page, select **Dynamics 365 Distributed Order Management Dataverse (current environment) Connection**.
   1. You should have already created a Dataverse connection in Power Automate by following the instructions in the "Create connections" section of the [Set up an environment](setup.md#create-connections) topic. Go to the [Power Automate portal](https://us.flow.microsoft.com/) and copy the URL as described in the "Set up platform connection references" section of the [Set up an environment](setup.md#create-connections) topic.
   1. Go back to the corresponding **Dynamics 365 Distributed Order Management Dataverse connection** reference page in Intelligent Order Management and paste the copied URL in the **Connection URL** field.
   1. Select **Save**.
   1. Select **Activate**.
   1. Select **Save and close**.
5. On the **Dynamics 365 Distributed Order Management** provider page, select **Activate**.
6. Select **Save and close**.

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

