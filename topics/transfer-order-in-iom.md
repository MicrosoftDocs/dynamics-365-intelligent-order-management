---
author: anvenkat
description: This article describes how to integrate transfer orders in Microsoft Dynamics 365 Supply Chain Management with Microsoft Dynamics 365 Intelligent Order Management.
ms.date: 10/18/2022
ms.topic: overview
ms.author: anvenkat

title: Integrate Supply Chain Management transfer orders with Intelligent Order Management

---

# Integrate Supply Chain Management transfer orders with Intelligent Order Management

[!include [banner](includes/banner.md)]

This article describes how to integrate transfer orders in Microsoft Dynamics 365 Supply Chain Management with Microsoft Dynamics 365 Intelligent Order Management.

A transfer order is created by warehouse workers to transfer products from one warehouse or location to another. Some of the common reasons for transfer orders include (but aren't limited to) the following:
- Transfer of products from manufacturing to a distribution facility.
- Stock replenishment at a store from a distribution center.
- Ad hoc transfers to a warehouse from another warehouse to meet a spike in demand.
- Transfers between warehouses for service purposes such as packaging and customizing requirements.

As part of extending support and providing visibility to the enterprise transactions, a **Transfer Order** entity has been introduced in Dynamics 365 Intelligent Order Management. The **Transfer Order** entity includes the following features:
- Dual-write support for transfer orders is available, so that data flows seamlessly from Microsoft Dataverse into Intelligent Order Management and is visible in real time, or near real time.
- Creation of a **Transfer Orders** entity in Intelligent Order Management. This will be processed in Supply Chain Management with dual-write support.
- The user interface (UI) fields for the **Transfer Orders** entity have been designed to support sales order fulfillment scenarios.
- Transaction status and visibility of transfer orders from Supply Chain Management are available directly in Intelligent Order Management.
- The **Transfer Order product** view is available on the **Sales Order** products tab, which provides visibility to the transfers from individual transfer order transactions.

## Dual-write support for transfer orders

The following prerequisites must be met before you can activate dual-write support for transfer orders:

- Install or update the following dual-write packages to ensure that you have the latest versions:
    - Dual-write core solution package
    - Dual-write Application Core package
    - Dual-write Finance package
    - Dual-write Human Resources package
- If your environment already has dual-write for sales orders installed, ensure that it is up-to-date.
- If you have an older version of Intelligent Order Management running in your instance, which already has dual-write installed, ensure that you import the UX solution package for Purchase Orders and Transfer Orders.

## General guidelines for installing the add-on UX package for new users

- If you're installing Intelligent Order Management first, you should install the dual-write solution before you import the UX package solution.
- If you're installing the dual-write solution first, the UX package solution will be imported as part of the installation. You can then install Intelligent Order Management.

## Initial synchronization of prerequisite tables

To create new transfer orders and work with existing transfer orders, you must first synchronize the reference data between Supply Chain Management and Dataverse. You use the initial write functionality to detect the table relationships and find the tables that you must enable for a given map.

In the dual-write sync settings, you will see the prerequisite tables for both **Transfer Order Header** and **Transfer Order Products**.

The following tables must be synched for **Transfer Order Header**.

- Sites
- Worker
- Modes of delivery
- Terms of delivery
- Warehouses

![Transfer header](media/transfer-header.png)

The following tables must be synched for **Transfer Order Products**.

- Worker
- Modes of delivery
- Terms of delivery
- Styles
- Colors
- Configurations
- Sizes
- Currencies
- Units
- CDS released distinct products
- Sites
- Warehouses

![To lines](media/to-lines.png)

For more information about dual-write mapping references, see [Dual-write mapping reference](/fin-ops-core/dev-itpro/data-entities/dual-write/mapping-reference)

## Create a transfer order 

To create a transfer order, follow these steps.

1. In the left navigation pane, select **Orders \> Transfer orders**. 
1. Select **+New**. 
1. Enter values for the following mandatory fields: 

    1. **Name** to specify a transfer order ID (which should be the same ID used in Supply Chain Management).
    1. **Company**.  
    1. **From warehouse** to specify the warehouse to transfer from, and **To warehouse** to specify the warehouse to transfer to. 
    1. Optionally, enter a **Ship date** value if you know when the transfer will ship out, and a **Receive date** value specifying when it will be received. These two optional fields can also be left blank.
1. To create **Transfer Order Product**, select **New Transfer Order product**, and then enter values for **Product**, **Line number**, and **Transfer quantity**. If you see that several other fields are locked, this means that those values are populated from Supply Chain Management as part of dual-write synchronization.
1. If you entered a **Ship date** and **Receive date** on the header, those values would default to the lines and can be overridden.
1. Select **Save**. Once **Transfer Order Products** is saved, it will sync to Supply Chain Management to be processed further.

## Process transfer order and status updates.

As **Transfer Order** processes in Supply Chain Management the status updates are reflected via dual-write in Dataverse and becomes visible in Intelligent Order Management. When **Transfer Order** gets shipped, the status of **Shipped** is updated on the header and lines. **Shipped Quantity** is reflected on the **Transfer Order product** form. When the **Transfer Order** is received in supply chain management, the status of **Received** is updated on the header. The Line status reflects as **None** after the item is received.

## View of Transfer Order Products within Sales Order Products

A view of **Transfer orders** is available inside the **sales order product**  within a separate tab showing the list of Transfers for the order product along with the **shipping** and **receiving warehouse**. This would give visibility of incoming inventory for the assigned warehouse to the sales order product. 

![Transfer order view](media/transfer-order.png)




