---
author: anush6121 
description: The document describes how the Finance + Operations integration solution works with Microsoft Dynamics Intelligent Order Management.
ms.date: 03/16/2022
ms.topic: overview
ms.author: anvenkat

title: Finance + Operations integration solution
---

# Finance + Operations integration solution

[!include [banner](includes/banner.md)]

The document describes how the Finance + Operations integration solution works with Microsoft Dynamics Intelligent Order Management.

## Prerequisites 

You will need to set up Finance + Operations as a provider and enable dual-write in Dataverse and Intelligent Order Management. For more information, see [Set up the Dynamics 365 Finance + Operations provider](set-up-finops-provider.md).

## Finance + Operations integration solution with Intelligent Order Management

The following points describe the Finance + Operations high-level solution for integration with Intelligent Order Management.

- Intelligent Order Management uses dual-write for data synchronization between Finance + Operations and Intelligent Order Management.
- E-commerce orders will be coming into Intelligent Order Management without company code. Company code will be assigned using a policy before synching to Finance + Operations.
- Finance + Operations provider action will send over order from Intelligent Order Management to Finance + Operations fulfillment or billing when order is ready to sync. 
- The Finance + Operations data assignment policy and provider actions will be called in designed orchestration flow.
- Finance + Operations order status event handler is introduced to monitor and raise business events in Intelligent Order Management when the order status is updated in Finance + Operations.
    
## Finance + Operations provider integration scenarios with Intelligent Order Management

The following scenarios describe the Finance + Operations integration scenarios with Intelligent Order Management.

#### BigCommerce (new order) \> Intelligent Order Management \> Finance + Operations (fulfillment) \> Finance + Operations (accounting)

1. Order created in BigCommerce
1. Order pulled into Intelligent Order Management from BigCommerce
1. Order validated in Intelligent Order Management
1. Company, site and warehouse assigned in Intelligent Order Management
1. Order sent to Finance + Operations by Finance + Operations provider action
    1.	Order sent to fulfillment successful event raised in Intelligent Order Management
1. Order shipped in Finance + Operations
    1.  Order shipped event raised in Intelligent Order Management
    1. Order status updated in BigCommerce by provider action
1. Order invoiced in Finance + Operations
    1.  Order invoiced event raised in Intelligent Order Management
    1. Order status updated in BigCommerce by provider action

#### BigCommerce (new order) \> Intelligent Order Management \>Flexe (fulfillment) \>Finance + Operations (accounting)

1. Order created in BigCommerce
1. Order pulled into Intelligent Order Management from BigCommerce
1. Order validated in Intelligent Order Management
1. Order sent to Flexe for fulfillment by Flexe provider action
1. Order shipped by Flexe
1. Assign site warehouses and company in Intelligent Order Management order
1. Order sent to Finance + Operations by Finance + Operations Provider action
1. Order invoiced in Finance + Operations
1. Order invoiced event raised in Intelligent Order Management.
1. Order status updated in BigCommerce by provider action

#### Finance + Operations (new order) \> Intelligent Order Management \> Flexe (fulfillment) \> Finance + Operations (accounting)

1. Order created in Finance + Operations
1. Finance + Operations order sent to Intelligent Order Management by DualWrite
1. Order confirmed in Finance + Operations
1. Order validated in Intelligent Order Management
1. Order sent to Flexe for fulfillment by Flexe provider action
1. Order shipped by Flexe
1. Order status update sent to Finance + Operations by Finance + Operations provider action
1. Order invoiced in Finance + Operations
1. Order invoiced event raised in Intelligent Order Management

#### Finance + Operations (new order) \> Intelligent Order Management \> Finance + Operations (fulfillment) \> Finance + Operations (accounting)

1. Order created in Finance + Operations
1. Finance + Operations order sent to Intelligent Order Management by DualWrite
1. Order confirmed in Finance + Operations
1. Order validated in Intelligent Order Management
1. Order shipped in Finance + Operations
    1. Order shipped event raised in Intelligent Order Management
1. Order invoiced in Finance + Operations
    1. Order invoiced event received in Intelligent Order Management

#### Finance + Operations (new order) \> Intelligent Order Management \> Flexe (fulfillment) \> SAP (accounting)

1. Order created in Finance + Operations
1. Finance + Operations order sent to Intelligent Order Management by DualWrite
1. Order confirmed in Finance + Operations
1. Order validated in Intelligent Order Management
1. Order sent to Flexe for fulfillment by provider action
1. Order shipped event raised in Intelligent Order Management
1. Order invoiced in SAP
1. Order invoiced event received in Intelligent Order Management
