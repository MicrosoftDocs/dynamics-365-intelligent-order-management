---
author: rinitha-reddy
description: This article describes how to set up the Fulfillment and Returns Optimization provider in Microsoft Dynamics 365 Intelligent Order Management.
ms.date: 10/19/2021
ms.topic: conceptual
ms.author: rikothap

title: Set up Fulfillment and Returns Optimization provider

---

# Set up Fulfillment and Returns Optimization provider

[!include [banner](includes/banner.md)]

This article describes how to set up the Fulfillment and Returns Optimization provider in Microsoft Dynamics 365 Intelligent Order Management. For more information, see [Fulfillment and Returns Optimization provider](fulfillment-returns-optimization.md).

## Add Fulfillment and Returns Optimization provider

To add the Fulfillment and Returns Optimization provider, follow these steps.
 
1. In Intelligent Order Management, go to **Providers \> Library**.
2. Select the tile and then **Activate Provider** on the top right corner of the page. 
3. In the flyout menu on the left, accept the Terms and Conditions.
1. Leave the mapping group as **Default mapping group**.
1. For **Transformations**, select **Next**.
1. Select **Edit** to add **Dataverse connection for IOM**. 
1. Sign into Dataverse using your credentials. You should have already created a Dataverse connection in Microsoft Power Automate by following the instructions in [Create connections](setup.md#create-connections).
1. Go to the [Power Automate portal](https://us.flow.microsoft.com/) and copy the URL following the instructions in [Set up platform connection references](setup.md#create-connections). 
1. Select **Save**, and then select **Next**.
1. When the steps above have been completed successfully, select **Activate**.
 
## Configure provider action

Customers typically add the **Send to Fulfillment and Returns Optimization** provider action after an order is validated. When added to an orchestration flow, the properties on the **Send to Fulfillment and Returns Optimization** tile should have the following values:

- **Name**: "Send to fulfillment and returns optimization" 
- **Input Events**: "Validation of Order Lines has Succeeded"
- **Provider Action**: "Send to fulfillment determination"

## Additional resources

[Intelligent Fulfillment Optimization](ifo.md) 

[Intelligent Fulfillment Optimization architecture](ifo-arch.md)

[Orchestration flows](orchestration-flows.md)
