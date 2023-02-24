---
author: anvenkat
description: This article describes how to set up the Internal Application Service Provider in Microsoft Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 02/23/2023
ms.topic: how-to
ms.author: anvenkat
title: Set up Internal Application Service Provider.
---

# Set up Inventory Visibility provider

This article describes how to set up the Internal Application Service  provider in Microsoft Dynamics 365 Intelligent Order Management.

The Internal Application Service provider is an internal provider that provides functionalities to support various processes across different services of Intelligent Order Management.

To add the Internal Application Service provider follow these steps:

1. In Intelligent Order Management, go to **Provider settings \> Library**
2. Select the tile for the Internal Application Service provider, and then select **Activate Providers** in the upper-right corner of the page.
3. In the dialog box on the left, accept the terms and conditions.
4. Leave the mapping group set to **Default mapping group**.
5. For **Transformations**, select **Next**.
6. Follow the prompts and select **Activate**

Following functionalities are a part of the provider and hence setting up this provider becomes a pre-requisite for the following processes.

1. Creation and processing of return fulfillment orders
2. Split orders: Ability to split a single order into multiple orders as part of orchestration flow based on assignment of split groups via execution policy.
3. Creation of fulfillment orders for policy based fulfillment.


Following out of box provider actions are available as part of the Internal Application Service Provider.

| Action | Description |
| ---------- | ------- |
| Create Fulfillment Return Orders | This provider action Create Fulfillment Return Orders action creates Fulfillment plans for return orders and then processes these   plans to generate Fulfillment Orders. |
| Create returns orders | This provider action Create Return Orders action processes the Return Order Request information and generates the Dataverse Return Order. |
| Send fulfillment process request | This provider action checks product inventory and creates fulfillment plan and fulfillment order for policy based fulfillment. |
| Split order | This provider action splits a parent order into child orders on the basis of split groups assigned to order lines. |


