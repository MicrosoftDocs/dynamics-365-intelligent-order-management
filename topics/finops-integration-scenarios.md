---
author: anush6121 
description: The topic describes how the Microsoft Dynamics 365 Finance + Operations (on-premises) integration solution integrates with Microsoft Dynamics Intelligent Order Management.
ms.date: 03/17/2022
ms.topic: overview
ms.author: anvenkat

title: Finance + Operations integration solution
---

# Finance + Operations integration solution

[!include [banner](includes/banner.md)]

The topic describes how the Microsoft Dynamics 365 Finance + Operations (on-premises) integration solution integrates with Microsoft Dynamics Intelligent Order Management.

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
1. The Finance + Operations provider action sends the order to Finance + Operations.

    - An "order sent to fulfillment successful" event is raised in Intelligent Order Management.

1. The order is shipped in Finance + Operations.

    1. An "order shipped" event is raised in Intelligent Order Management.
    1. The provider action updates the order status in BigCommerce.

1. The order is invoiced in Finance + Operations.

    1. An "order invoiced" event is raised in Intelligent Order Management.
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

    - An "order shipped" event is raised in Intelligent Order Management.

1. The order is invoiced in Finance + Operations.

    - An "order invoiced" event is received in Intelligent Order Management.

### Finance + Operations (new order) \> Intelligent Order Management \> Flexe (fulfillment) \> SAP (accounting)

1. An order is created in Finance + Operations.
1. Dual-write sends the Finance + Operations order to Intelligent Order Management.
1. The order is confirmed in Finance + Operations.
1. The order is validated in Intelligent Order Management.
1. The provider action sends the order to Flexe for fulfillment.
1. An "order shipped" event is raised in Intelligent Order Management.
1. The order is invoiced in SAP.
1. An "order invoiced" event is received in Intelligent Order Management.
