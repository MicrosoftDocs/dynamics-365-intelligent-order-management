---
author: anvenkat
description: Learn how to integrate procurement in Microsoft Dynamics 365 Supply Chain Management with Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 01/28/2026
ms.custom: 
  - bap-template
ms.topic: how-to
ms.author: anvenkat
title: Integrate Supply Chain Management procurement with Intelligent Order Management
---

# Integrate Supply Chain Management procurement with Intelligent Order Management

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This article describes how to integrate procurement in Microsoft Dynamics 365 Supply Chain Management with Dynamics 365 Intelligent Order Management.

To extend support for inbound transactions and provide transaction visibility alongside inventory visibility, Intelligent Order Management introduces a **Purchase Orders** entity. The **Purchase Orders** entity includes the following features:

- Dual-write support for purchase orders, so that purchase order data flows seamlessly from Dataverse into Intelligent Order Management and is visible in real or near-real time.
- The ability to create purchase orders in Intelligent Order Management. The system then processes the purchase orders in Supply Chain Management via dual-write support.
- User interface (UI) fields for the **Purchase Orders** entity that support sales order fulfillment scenarios.
- Transaction status and visibility of purchase orders from Supply Chain Management are available directly in Intelligent Order Management.
- The **Purchase Order products** view on the **Sales Order** products tab provides visibility into incoming inventory from individual purchase order transactions. The **Purchase Order products** view is also available on the site map, for easy access to the status of individual purchase order lines at the product level.

For more information about purchase orders, see [Purchase order overview](/dynamics365/supply-chain/procurement/purchase-order-overview).

## Dual-write support for purchase orders

Before you activate dual-write support for purchase orders, make sure you meet the following prerequisites:

- Install or update the following dual-write packages to ensure that you have the latest versions:

  - Dual-write core solution package
  - Dual-write Application Core package
  - Dual-write finance package
  - Dual-write Human Resources package

- If dual-write for sales orders is already installed in your environment, make sure it's up to date.
- If an older version of Intelligent Order Management is running in your instance, and dual-write is already installed there, make sure you import the user experience (UX) solution package for purchase orders and transfer orders.

## General guidelines for installing the add-on UX package for new users

- If you're installing Intelligent Order Management first, install the dual-write solution before you import the UX package solution.
- If you're installing the dual-write solution first, the UX package solution is imported as part of the installation. You can then install Intelligent Order Management.

## Initial synchronization of prerequisite tables

After you meet all the preceding prerequisites, you must perform an initial synchronization of the prerequisite and dependent master data and tables. This synchronization makes existing purchase orders available in both Supply Chain Management and Intelligent Order Management. For information about which tables you must sync and how to sync them, see [Integrate procurement between Supply Chain Management and Field Service](/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/scm-field-service-procurement).

## Dual-write purchase order mapping reference

For information about dual-write purchase order mapping, see [Mapping reference](/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/mapping-reference#183).

## Create a purchase order

To create a purchase order in Intelligent Order Management, follow these steps:

1. In the site map, go to **Purchase orders**.
1. Select **New**, enter values for the mandatory fields, and then select **Save**.
1. On the **Purchase Order** header entity, enter values in the **Name**, **Receiving Warehouse**, **Site**, **Vendor**, and **Company** fields. The **Name** value represents the purchase order number that Supply Chain Management assigns.

    > [!NOTE]
    > If you save the header without entering any of the field values, and you then want to edit them immediately afterward, you must confirm the header in Supply Chain Management before you can update any of the fields on the **Purchase Order** page.

1. Select **Save**.
1. Select **New Purchase Order Product**, and then select values in the **Existing Product**, **Line number**, **Associate to Warehouse**, **Quantity**, and **Unit of measure** fields.
1. Select **Save**. If the transaction is successfully saved, the dual-write operation was successful, and the purchase order was created and updated in Supply Chain Management.

## UI fields for purchase order entities

The following sections list the UI fields that are available for purchase order entities.

### Purchase order header fields

- Name
- Purchase order ID
- Contact email
- Receiving warehouse
- Vendor
- Vendor reference
- Company
- Receiving site ID
- Reason code
- Reason comment
- Delivery terms
- Shipping via
- Expected date
- Confirmed delivery dates
- Delivery address

### Purchase order product fields

- Purchase order ID
- Existing product
- Description
- Line number
- Associate to warehouse
- Company
- Receiving site ID
- Quantity
- Unit cost
- Discount amount
- Discount percentage
- Total price
- Amount
- Purchase order line status

### Purchase Order Goods Receipt header fields

- Name
- Purchase Order
- Note
- Company
- Order Vendor
- Record ID
- Ship Via
- Date Received
- Requester Personnel
- Delivery Term
- Remaining Inventory Quantity
- Remaining Purchase Quantity

### Purchase Order Goods Receipt product fields

- Name
- Purchase order ID
- Purchase Order Product
- Quantity
- Product Receipt Number
- Product Receipt Date
- Company
- Expected Delivery Date
- Ordered Purchase Quantity
- Received Inventory Quantity

## Supported dual-write scenarios

The following dual-write scenarios are supported:

- Dataverse users can create and update purchase orders, but Supply Chain Management controls the process and data. The constraints on updates to purchase order columns in Supply Chain Management apply when updates come from Intelligent Order Management. For example, you can't update a purchase order if it's finalized, and you can't update a purchase order that was created in Intelligent Order Management until the purchase order is confirmed in Supply Chain Management.
- Several columns are managed only by Supply Chain Management and can't be updated in Intelligent Order Management. To learn which columns can't be updated, review the mapping tables in the product. Most of these columns are set to read-only on Dataverse pages.

    For example, Supply Chain Management manages the columns for price information. Supply Chain Management has trade agreements in place, and columns such as **Unit price**, **Discount**, and **Net amount** come only from Supply Chain Management. To ensure that a price is synced to Intelligent Order Management, use the **Sync** feature on the **Purchase Order** and **Purchase Order Product** pages in Dataverse after entering purchase order data. For more information, see [Sync with the Dynamics 365 Supply Chain Management procurement data on demand](/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/scm-field-service-procurement#sync-procurement).

- Supply Chain Management manages product receipts (which are known as purchase order receipts in Dataverse) and can't be created from Dataverse if Supply Chain Management is installed. Product receipts from Supply Chain Management are synced from Supply Chain Management to Dataverse.
- Supply Chain Management allows under-delivery. The OneFSSCM solution adds logic so that, when a product receipt line (known as a purchase order receipt product in Dataverse) is created or updated, an inventory journal row is created in Dataverse to adjust the remaining quantity that is on order for under-delivery scenarios.

## Transaction status and visibility of purchase orders from Supply Chain Management directly in Intelligent Order Management

As a purchase order progresses in Supply Chain Management, status updates flow back to Intelligent Order Management for tracking and visibility. You can view open purchase order lines and purchase order line status by going to **Purchase Order products** in the site map. In this way, you can stay informed about incoming inventory. Purchase order product fields such as **Expected date** and **Confirmed delivery date** provide insights into the in-transit purchase orders.

The **Purchase Order Receipt** and **Purchase Order Receipt products** entities provide visibility into the **Received inventory quantity**, **Remaining inventory quantity**, **Product receipt date**, and **Purchased quantity** values. The **Purchase Order Receipt** entity on a purchase order can be accessed via a separate tab on the purchase order page. Fields on the purchase order page can provide insights into under-receipts and over-receipts.

The following illustration shows an example of the **New Purchase Order Receipt Product** page.

:::image type="content" source="media/goods-receipt.png" alt-text="Screenshot of the New Purchase Order Receipt Product page.":::

For information about the detailed mapping between Supply Chain Management purchase order status and purchase order line status, see [Integrate procurement between Supply Chain Management and Field Service](/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/scm-field-service-procurement).

## Purchase order product view on the sales order products page

The **Purchase Orders** tab that is available on the sales order products page lists all the open purchase order lines for the product. The following illustration shows an example.

:::image type="content" source="media/po-view-sp.png" alt-text="Screenshot of the Purchase Orders tab on a sales order products page.":::
