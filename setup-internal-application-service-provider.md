---
title: Set up Internal Application Service Provider.
description: This article describes how to set up the Internal Application Service Provider in Microsoft Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 02/23/2023
ms.topic: how-to
ms.author: anvenkat
author: anvenkat
ms.custom: bap-template

---

# Set up Inventory Visibility provider

This article describes how to set up the Internal Application Service provider in Microsoft Dynamics 365 Intelligent Order Management.

The Internal Application Service provider is an internal provider that supports various processes across different services in Intelligent Order Management. The following functionalities are a part of the provider and hence setting up this provider becomes a pre-requisite for the following processes.

- Create and process return fulfillment orders.
- Split one order into multiple orders as part of the orchestration flow based on the assignment of split groups via an execution policy.
- Create fulfillment orders for policy-based fulfillment.

To add the Internal Application Service provider, follow these steps:

1. In Intelligent Order Management, go to **Provider settings \> Library**.
1. Select the tile for the Internal Application Service provider, and then select **Activate Providers** in the upper-right corner of the page.
1. In the dialog box on the left, accept the terms and conditions.
1. Leave the mapping group set to **Default mapping group**.
1. For **Transformations**, select **Next**.
1. Follow the prompts, and select **Activate**.

The table below shows the out of box provider actions are available as part of the Internal Application Service Provider.

| Action | Description |
| ---------- | ------- |
| Create Fulfillment Return Orders | This provider action creates Fulfillment plans for return orders and then processes these plans to generate Fulfillment Orders. |
| Create returns orders | This provider action processes the Return Order Request information and generates the Dataverse Return Order. |
| Send fulfillment process request | This provider action checks product inventory and creates fulfillment plan and fulfillment order for policy-based fulfillment. |
| Split order | This provider action splits a parent order into child orders based on split groups assigned to order lines. |


