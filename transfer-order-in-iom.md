---
title: Integrate transfer orders in Supply Chain Management with Intelligent Order Management
description: This article describes how to integrate transfer orders in Microsoft Dynamics 365 Supply Chain Management with Dynamics 365 Intelligent Order Management.
author: anvenkat
ms.author: anvenkat
ms.topic: how-to
ms.date: 02/23/2023
ms.custom: bap-template
---

# Integrate transfer orders in Supply Chain Management with Intelligent Order Management

This article describes how to integrate transfer orders in Microsoft Dynamics 365 Supply Chain Management with Dynamics 365 Intelligent Order Management.

Warehouse workers create transfer orders to transfer products from one warehouse or location to another. Here are some typical scenarios where a transfer order might be needed:

- Product transfers from manufacturing to a distribution facility
- Stock replenishment in a store from a distribution center
- Ad-hoc transfers from one warehouse to another to meet a spike in demand
- Transfers between warehouses for service purposes, such as packaging and customization requirements

A **Transfer Order** entity has been introduced in Intelligent Order Management to extend support for, and provide visibility into, the enterprise transactions. The **Transfer Order** entity supports the following features:

- Dual-write support for transfer orders is available, so that transfer order data can flow seamlessly from Dataverse into Intelligent Order Management and is visible in real or near-real time.
- Transfer orders can be created in Intelligent Order Management. This action will be processed in Supply Chain Management via dual-write support.
- **Transfer Order** entity user interface fields have been designed to support sales order fulfillment scenarios.
- Transaction status and transfer orders from Supply Chain Management can be viewed directly in Intelligent Order Management.
- The **Transfer Order product** view is available on the **Sales Order products** tab and provides visibility into the transfers from individual transfer order transactions.

## Dual-write support for transfer orders

The following prerequisites must be met before you can activate dual-write support for purchase orders:

- Install the following dual-write packages, or update to the latest versions:

    - Dual-write core solution package
    - Dual-write Application Core package
    - Dual-write Finance package
    - Dual-write Human Resources package

- If dual-write for sales orders is already installed in your environment, ensure that it's up to date. If an older version of Intelligent Order Management is running in your instance, and dual-write is installed for it, ensure that you import the user experience (UX) package solution for purchase orders and transfer orders.

## General guidelines for installing the add-on UX package for new users

If you're installing Intelligent Order Management first, you should install the dual-write solution before you import the UX package solution.

If you're installing the dual-write solution first, the UX package solution will be imported as part of the installation. Intelligent Order Management can then be installed afterward.

## Initial synchronization of prerequisite tables

To create new transfer orders and work with existing transfer orders, you must sync the reference data between Supply Chain Management and Dataverse. You use the initial write functionality to detect the table relationships and find the tables that you must enable for a given map.

In the dual-write synchronization settings, you will see the prerequisite tables for both the transfer order header and transfer order products.

The following tables must be synced for the header:

- Sites
- Worker
- Modes of delivery
- Terms of delivery
- Warehouses

![Prerequisite tables for the transfer order header in the Initial writes and related table map(s) dialog box.](media/Transferheader.png)

The following tables must be synced for products:

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

![Prerequisite tables for transfer order products in the Initial writes and related table map(s) dialog box.](media/Tolines.png)

For dual-write mapping reference, see [Dual write mapping reference](/fin-ops-core/dev-itpro/data-entities/dual-write/mapping-reference).

## Create a transfer order

To create a transfer order, follow these steps.

1. Go to **Orders**, and select the **Transfer orders** site map entry.
1. Select **New**, and enter information into the required fields. Here are some examples:

    - In the **Name** field, specify the transfer order ID. (Supply Chain Management uses the same ID.)
    - In the **Company** field, specify the company.
    - In the **From Warehouse** field, specify the warehouse that you want to transfer from.
    - In the **To warehouse** field, specify the warehouse that you want to transfer to. 

1. Optional: If you know when the transfer will be shipped out, specify the date in the **Ship date** field. If you know when the transfer will be received, specify the date in the **Receive date** field. You can also leave both these fields blank.
1. To create a transfer order product, select **New Transfer Order product**, and then enter the product details in the **Line number** and **Transfer quantity** fields. Notice that several other fields are locked. These fields are filled with values from Supply Chain Management as part of dual-write synchronization.
1. If you specified **Ship date** and **Receive date** values on the header, those values are entered by default on the lines. However, you can override the default values on the lines.
1. After you save the transfer order product, it's synced to Supply Chain Management for further processing.

## Processing of transfer order and status updates

As the transfer order is processed in Supply Chain Management, status updates are reflected in Dataverse via dual-write, and they become visible in Intelligent Order Management. When a transfer order is shipped, the status is updated to **Shipped** on the header and lines. The shipped quantity is reflected on the **Transfer Order product** page. When the transfer order is received in Supply Chain Management, the status is updated to **Received** on the header. After the item is received, the line status is **None**.

## View of transfer order products in sales order products

A view of transfer orders is available on a separate **Transfer Orders** tab on the page for the sales order product. This tab shows the list of transfers for the order product, together with the shipping warehouse and receiving warehouse. Therefore, it provides visibility into incoming inventory for the warehouse that's assigned to the sales order product. 

[Transfer order view.](media/TO.png)
