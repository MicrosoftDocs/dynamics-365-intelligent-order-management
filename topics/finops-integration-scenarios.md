---
author: anush6121 
description: The topic describes how the Microsoft Dynamics 365 Finance + Operations (on-premises) integration solution integrates with Microsoft Dynamics 365 Intelligent Order Management.
ms.date: 04/12/2024
ms.custom: 
  - bap-template
ms.topic: overview
ms.author: anvenkat

title: Finance + Operations integration solution
---

# Finance + Operations integration solution

[!include [banner](includes/banner.md)]

The topic describes how the Microsoft Dynamics 365 Finance + Operations (on-premises) integration solution integrates with Microsoft Dynamics 365 Intelligent Order Management.

## Prerequisites

You must set up Finance + Operations as a provider and enable dual-write in Dataverse and Intelligent Order Management. For more information, see [Set up the Dynamics 365 Finance + Operations provider](set-up-finops-provider.md).

## Finance + Operations integration solution with Intelligent Order Management

The Finance + Operations high-level solution for integration with Intelligent Order Management works in the following ways:

- Intelligent Order Management uses dual-write for data synchronization between Finance + Operations and Intelligent Order Management.
- E-commerce orders that come into Intelligent Order Management won't have company codes. Before synchronization to Finance + Operations, a policy will be used to assign company codes.
- The Finance + Operations provider action will send an order from Intelligent Order Management to Finance + Operations fulfillment or billing when the order is ready for synchronization. 
- The Finance + Operations data assignment policy and provider actions will be called in the designed orchestration flow.
- The Finance + Operations order status event handler will monitor and raise business events in Intelligent Order Management when the order status is updated in Finance + Operations.

## Finance + Operations provider integration scenarios with Intelligent Order Management

Following scenarios outline the processes for integration of Finance + Operations with Intelligent Order Management.

### BigCommerce (new order) \> Intelligent Order Management \> Finance + Operations (fulfillment) \> Finance + Operations (accounting)

1. An order is created in BigCommerce.
1. The order is pulled from BigCommerce into Intelligent Order Management.
1. The order is validated in Intelligent Order Management.
1. A company, site, and warehouse are assigned in Intelligent Order Management.
1. The Finance + Operations provider action sends the order to Finance + Operations (Use **Action** = **Send order to fulfillment**).
1. The order is picked in Finance + Operations.
1. The order state in Intelligent Order Management is updated to **Fulfillment in Process** with status reason **Picked**.
1. The order is packed and delivered in Finance + Operations. 
1. An "order shipped" event is raised in Intelligent Order Management that updates the Order state to **Fulfillment in Process** and status reason as **Packed**
1. The provider action updates the order status in BigCommerce.
1. The order is invoiced in Finance + Operations.
1. An "order invoiced" event is raised in Intelligent Order Management that updates the order state to **Completed** and status reason to **Fulfilled**
1. The provider action updates the order status in BigCommerce.

### BigCommerce (new order) \> Intelligent Order Management \> Flexe (fulfillment) \> Finance + Operations (accounting)

1. An order is created in BigCommerce.
1. The order is pulled from BigCommerce into Intelligent Order Management.
1. The order is validated in Intelligent Order Management.
1. The Flexe provider action sends the order to Flexe for fulfillment.
1. Flexe ships the order.
1. Site warehouses and a company are assigned in Intelligent Order Management.
1. The Finance + Operations provider action sends the order to Finance + Operations.
1. The order is invoiced in Finance + Operations.
1. An "order invoiced" event is raised in Intelligent Order Management.
1. The provider action updates the order status in BigCommerce.

### Finance + Operations (new order) \> Intelligent Order Management \> Flexe (fulfillment) \> Finance + Operations (accounting)

1. An order is created in Finance + Operations.
1. Dual-write sends the Finance + Operations order to Intelligent Order Management.
1. The order is confirmed in Finance + Operations.
1. The order is validated in Intelligent Order Management.
1. The Flexe provider action sends the order to Flexe for fulfillment.
1. Flexe ships the order.
1. The Finance + Operations provider action sends the order status to Finance + Operations.
1. The order is invoiced in Finance + Operations.
1. An "order invoiced" event is raised in Intelligent Order Management.

### Finance + Operations (new order) \> Intelligent Order Management \> Finance + Operations (fulfillment) \> Finance + Operations (accounting)

1. An order is created in Finance + Operations.
1. Dual-write sends the Finance + Operations order to Intelligent Order Management.
1. The order is confirmed in Finance + Operations.
1. The order is validated in Intelligent Order Management.
1. The order is shipped in Finance + Operations.
1. An "order shipped" event is raised in Intelligent Order Management.
1. The order is invoiced in Finance + Operations.
1. An "order invoiced" event is received in Intelligent Order Management.

### Finance + Operations (new order) \> Intelligent Order Management \> Flexe (fulfillment) \> SAP (accounting)

1. An order is created in Finance + Operations.
1. Dual-write sends the Finance + Operations order to Intelligent Order Management.
1. The order is confirmed in Finance + Operations.
1. The order is validated in Intelligent Order Management.
1. The Flexe provider action sends the order to Flexe for fulfillment.
1. An "order shipped" event is raised in Intelligent Order Management.
1. The order is invoiced in SAP.
1. An "order invoiced" event is received in Intelligent Order Management.

### BigCommerce (new order) \> Intelligent Order Management with DOM for source determination \> Finance + Operations (fulfillment) \> Finance + Operations (accounting)

1. An order is created in BigCommerce.
1. The order is pulled from BigCommerce into Intelligent Order Management.
1. The order is validated in Intelligent Order Management.
1. A company, and site are assigned in Intelligent Order Management.
1. The order is passed through the provider action **Send to Fulfillment Optimization**.
1. A fulfillment order is created for each of the fulfillment sources determined for the sales order lines.
1. The sales order lines are passed to Finance + Operations through the provider action **Send sales order lines to billing**. This action also updates the sales order lines with the shipping warehouse before the synchronization to Finance + Operations. Note that all of the sales order lines that have a shipping warehouse on them are selected for synchronization. 
1. If Fulfillment optimization fails to create a fulfillment order due to lack of inventory, those sales order lines aren't synchronized to Finance + Operations.
1. If **Backorder** is enabled in **General settings** \> **Order handling preferences** , the sales order line is set to a state **Backorder hold** until a backorder job runs and finds the inventory and releases that line to fulfillment and then to Finance + Operations.
1. The order is picked in Finance + Operations.
1. The order state in Intelligent Order Management is updated to **Fulfillment in Process** with status reason **Picked**.
1. The order is packed and delivered in Finance + Operations.  
1. An "order shipped" event is raised in Intelligent Order Management that updates the Order state to **Fulfillment in process** and status reason as **Packed**
1. The provider action updates the order status in BigCommerce.
1. The order is invoiced in Finance + Operations that updates the order state to **Completed** and status reason as **Fulfilled**
1. The provider action updates the order status in BigCommerce.
