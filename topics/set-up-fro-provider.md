---
author: rinitha-reddy
description: This article describes how to set up the Fulfillment and Returns Optimization provider in Microsoft Dynamics 365 Intelligent Order Management.
ms.date: 10/19/2021
ms.topic: conceptual
ms.author: rikothap

title: Set up the Fulfillment and Returns Optimization provider

---

# Set up the Fulfillment and Returns Optimization provider

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This article describes how to set up the Fulfillment and Returns Optimization provider in Microsoft Dynamics 365 Intelligent Order Management. For more information, see [Fulfillment and Returns Optimization provider](fulfillment-returns-optimization.md).

## Add the Fulfillment and Returns Optimization provider

To add the Fulfillment and Returns Optimization provider, follow these steps.

1. In Intelligent Order Management, go to **Providers \> Library**.
2. Select the tile for the Fulfillment and Returns Optimization provider, and then select **Activate Provider** in the upper-right corner of the page.
3. In the dialog box on the left, accept the terms and conditions.
1. Leave the mapping group set to **Default mapping group**.
1. For **Transformations**, select **Next**.
1. Select **Edit** to add **Dataverse connection for IOM**.
1. Select **Save**, and then select **Next**.
1. When all the preceding steps have been successfully completed, select **Activate**.

## Configure a provider action

Customers typically add the **Send to Fulfillment and Returns Optimization** provider action after an order is validated. When this provider action has been added to an orchestration flow, the properties on the **Send to Fulfillment and Returns Optimization** tile should have the following values:

- **Name:** Send to fulfillment and returns optimization
- **Input Events:** Validation of Order Lines has Succeeded
- **Provider Action:** Send to fulfillment optimization
- **Output Event:** Fulfillment optimization request succeeded, Fulfillment optimization request failed
- **Action Description** This provider action sends the order through fulfillment optimization and outputs a fulfillment plan and creates fulfillment order

## Sample orchestration flow with the provider

![Orchestration flow with FRO provider action.](media/flow-with-FRO-provider.png)


## Additional resources

[Intelligent Fulfillment Optimization](ifo.md)

[Intelligent Fulfillment Optimization architecture](ifo-arch.md)

[Orchestration flows](orchestration-flows.md)
