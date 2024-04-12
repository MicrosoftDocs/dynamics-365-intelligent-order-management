---
title: Set up the Internal Application Service provider
description: This article describes how to set up the Internal Application Service provider in Microsoft Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 04/12/2024
ms.custom: 
  - bap-template
ms.topic: how-to
ms.author: anvenkat
author: anvenkat
ms.custom: bap-template

---

# Set up the Internal Application Service provider

This article describes how to set up the Internal Application Service provider in Microsoft Dynamics 365 Intelligent Order Management.

The Internal Application Service provider is an internal provider that supports various processes across different services in Intelligent Order Management. The following functionality is part of the provider. Therefore, setup of the provider is a prerequisite for it.

- Create and process return fulfillment orders.
- As part of the orchestration flow, split one order into multiple orders, based on the assignment of split groups via an execution policy.
- Create fulfillment orders for policy-based fulfillment.

To add the Internal Application Service provider, follow these steps.

1. In Intelligent Order Management, go to **Provider settings \> Library**.
1. Select the tile for the Internal Application Service provider, and then select **Activate Providers** in the upper-right corner of the page.
1. In the dialog box on the left, accept the terms and conditions.
1. Leave the mapping group set to **Default mapping group**.
1. For **Transformations**, select **Next**.
1. Follow the prompts, and then select **Activate**.

The following table shows the out-of-box provider actions that are available as part of the Internal Application Service Provider.

| Action | Description |
|--------|-------------|
| Create Fulfillment Return Orders | This provider action creates fulfillment plans for return orders and then processes the plans to generate fulfillment orders. |
| Create returns orders | This provider action processes return order request information and generates a Dataverse return order. |
| Send fulfillment process request | This provider action checks product inventory, and creates a fulfillment plan and fulfillment order for policy-based fulfillment. |
| Split order | This provider action splits a parent order into child orders, based on split groups that are assigned to order lines. |
