---
author: v-chgri
description: This topic describes how to orchestrate orders using Intelligent Fulfillment Optimization provider in Microsoft Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 08/02/2021
ms.topic: conceptual
ms.author: josaw

title: Set up Intelligent Fulfillment Optimization provider

---

# Set up Intelligent Fulfillment Optimization provider

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic describes how to set up Intelligent Fulfillment Optimization provider in Microsoft Dynamics 365 Intelligent Order Management. For information about Intelligent Fulfillment Optimization, refer to the [Intelligent Fulfillment Optimization (preview)](iof.md) topic.

> [!NOTE]
> To orchestrate orders using Intelligent Fulfillment Optimization provider, you will need to use external fulfillment optimization providers to bring orders into the system.


## Add Intelligent Fulfillment Optimization provider
 
1. In Intelligent Order Management, go to **Providers \> Catalog**.
2. Select **Add Provider** on the **Intelligent Fulfillment Optimization** tile.
3. Select **Create** on the **Terms and Conditions** page.
4. On the **Connections** page, select **Intelligent Fulfillment Optimization Dataverse (current environment) Connection**.
   1. You should have already created a Dataverse connection in Power Automate by following the instructions in the "Create connections" section of the [Set up an environment](setup.md#create-connections) topic. Go to the [Power Automate portal](https://us.flow.microsoft.com/) and copy the URL as described in the "Set up platform connection references" section of the [Set up an environment](setup.md#create-connections) topic.
   1. Go back to the corresponding **Intelligent Fulfillment Optimization Dataverse Connection** reference page in Intelligent Order Management and paste the copied URL in the **Connection URL** field.
   1. Select **Save**.
   1. Select **Activate**.
   1. Select **Save and close**.
5. On the **Intelligent Fulfillment Optimization** provider page, select **Activate**.
6. Select **Save and close**.

## Configure provider action

Customers typically add this provider action (**Send to Intelligent Fulfillment Optimization**) after an order is validated. When added to an orchestration flow, the **Send to Intelligent Fulfillment Optimization** tile should have the following properties.

-   **Name**: "Send to intelligent order fulfillment" 
-   **Input Events**: "Validation of Order Lines has Succeeded"
-   **Provider Action**: "Send to fulfillment determination"

## Additional resources

[Intelligent Fulfillment Optimization (preview)](ifo.md) 

[Orchestration flows](orchestration-flows.md)

