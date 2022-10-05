---
author: anvenkat
description: This topic describes how to integrate procurement in Microsoft Dynamics 365 Supply Chain Management with Microsoft Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 10/05/2022
ms.topic: conceptual
ms.author: anvenkat

title: Integrate procurement in Supply Chain Management with Intelligent Order Management

---

# Integrate procurement in Supply Chain Management with Intelligent Order Management

This topic describes how to integrate procurement in Microsoft Dynamics 365 Supply Chain Management with Microsoft Dynamics 365 Intelligent Order Management.

To extend support for inbound transactions and provide transaction visibility alongside inventory visibility, a **Purchase Orders** entity has been introduced within Intelligent Order Management. The **Purchase Orders** entity includes the following features: 

- Dual-write support for purchase orders is available so that purchase order data seamlessly flows from Microsoft Dataverse into Intelligent Order Management and is visible in real or near real time.
- Users can create purchase orders from within Intelligent Order Management. Purchase order are then processed in Supply Chain Management via dual-write support.
- The **Purchase Order** entity user interface (UI) fields have been designed to meet the specific needs of support for sales order fulfillment scenarios.
- Transaction status and visibility of purchase orders from Supply Chain Management is directly available to view within Intelligent Order Management.
- The **Purchase Order products** view is available on the **Sales Order** products tab, which provides visibility to incoming inventory from individual purchase order transactions. The **Purchase Order products** view is also available on the site map for easy access to individual purchase order line status at the product level.

For more information on purchase orders, see [Purchase order overview](/dynamics365/supply-chain/procurement).

## Dual-write support for purchase orders

 The following prerequisites must be met to activate dual-write support for purchase orders:

- You must have the following dual-write packages installed or updated to ensure that you have the latest versions:
    - Dual-write core solution package
    - Dual-write Application Core package
    - Dual-write finance package
    - Dual-write Human Resources package
- If your environment already has dual-write for sales orders installed, ensure that it's up to date.
- If you have an older version of Intelligent Order Management running in your instance which already has dual-write installed, ensure that you import the user experience (UX) solution package for purchase orders and transfer orders.

### General guidelines for installing the add-on UX package for new users

- If you're installing Intelligent Order Management first, you should install the dual-write solution before importing the UX package solution.
- If you're installing the dual-write solution first, the UX package solution will be imported as part of the install. Intelligent Order Management can then be installed afterwards.

### Initial synchronization of prerequisite tables

After all of the prerequisites above have been met, you must do an initial synchronization of the prerequisite and dependent master data and tables so that existing purchase orders are available in both Supply Chain Management and Intelligent Order Management. For instructions on what tables to sync and how to sync them, see [Integrate procurement between Supply Chain Management and Field Service](/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/scm-field-service-procurement).

### Dual-write purchase order mapping reference

For information on dual-write purchase order mapping, see [Mapping reference](/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/mapping-reference#183).

## Create a purchase order 

To create a purchase order in Intelligent Order Management, follow these steps.

1. Go to **Purchase orders** in the site map.
1. Select **+New**, enter values for the mandatory fields, and then select **Save**.
1. On the **Purchase Order** header entity, enter values for the **Name**, **Receiving Warehouse**,**Site**,**Vendor**, and **Company** fields. The **Name** value is used to denote the **Purchase Order** number that will be assigned in Supply Chain Management. 
    > [!NOTE] 
    > If you save the header without entering any of the field values, and then want to immediately edit them after saving, you must first confirm the header in Supply Chain management before you can update any of the fields on the **Purchase Order** form.
1. Select **Save**.
1. Select **New Purchase Order Product** and then select **Existing Product**, **Line number**, **Associate to Warehouse**, **Quantity**, and **Unit of measure**. 
1. Select **Save**. If the transaction saves successfully, this means that the dual-write operation was successful and the purchase order was created and updated within Supply Chain Management.

## User interface fields on the different entities of Purchase Order

|**Purchase Order header**| **Purchase Order product**| **Purchase Order Goods Receipt header** | **Purchase Order Goods Receipt product** |
|-----------------------------|----------------------------|---------------------------------------|-----------------------------------------|
| Name | Purchase Order ID | Name | Name |
| Purchase Order ID | Existing Product | Purchase Order | Purchase order ID |
| Contact email | Description | Note | Purchase Order Product |
| Receiving warehouse | Line number | Company | Quantity |
| Vendor | Associate to warehouse | Order Vendor  | Product Receipt Number |
| Vendor Reference | Company  | Record Id | Product Receipt Date |
| Company | Receiving Site Id | Ship via | Company |
| Receiving site ID | Quantity | Date received | Expected Delivery Date |
| Reason Code | Unit cost | Requester Personnel | Ordered Purchase Quantity
| Reason Comment | Discount amount | Delivery Term | Received Inventory Quantity
| Delivery Terms | Discount percentage | Remaining Inventory Quantity
| Shipping via | Total Price | Remaining Purchase Quantity
| Expected Date | Amount |
| Confirmed Delivery Date | Purchase Order line status |
| Delivery address |

### Supported dual-write scenarios

The following dual-write scenarios are supported:

- Purchase orders can be created and updated by Dataverse users, but the process and data are controlled by Supply Chain Management. The constraints on updates to purchase order columns in Supply Chain Management apply when updates come from Intelligent Order Management. For example, you can't update a purchase order if it has been finalized, and you can't make updates on a purchase order created in Intelligent Order Management until the purchase order is confirmed in Supply Chain Management.
- Several columns are only managed by Supply Chain Management and can't be updated in Intelligent Order Management. To learn which columns can't be updated, review the mapping tables in the product. Most of these columns are set to read-only on Dataverse pages.

    For example, the columns for price information are managed by Supply Chain Management. Supply Chain Management has trade agreements in place and columns such as **Unit price**, **Discount**, and **Net amount** come only from Supply Chain Management. To ensure that a price is synced to Intelligent Order Management, in Dataverse you should use the **Sync** feature on the **Purchase Order** and **Purchase Order Product** pages after purchase order data has been entered. For more information, see [Sync with the Dynamics 365 Supply Chain Management procurement data on demand](/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/scm-field-service-procurement#sync-procurement).
- Product receipts (also known as purchase order receipts in Dataverse) are managed by Supply Chain Management and can't be created from Dataverse if Supply Chain Management is installed. The product receipts from Supply Chain Management are synced from Supply Chain Management to Dataverse.
- Under-delivery is allowed in Supply Chain Management. The OneFSSCM solution adds logic so that when a product receipt line (or purchase order receipt product in Dataverse) is created or updated, an inventory journal row is created in Dataverse to adjust the remaining quantity that is on order for under-delivery scenarios.

## Transaction status and visibility of purchase orders from Supply Chain Management directly within Intelligent Order Management

As a purchase order progresses in Supply Chain Management, status updates flow back to Intelligent Order Management for tracking and visibility. Open purchase order lines and purchase order line status can be viewed by accessing the site map entry **Purchase Order products** to stay informed on incoming inventory. Purchase order product fields such as **Expected date** and **Confirmed delivery date** provide insights to the in-transit purchase orders.

The **Purchase Order Receipt** and **Purchase Order Receipt products** entities provide visibility to the **Received inventory quantity**, **Remaining inventory quantity**, **Product receipt date**, and **Purchased quantity**. The **Purchase Order Receipt** entity within a purchase order can be accessed via a separate tab on the purchase order form. Fields on the purchase order form can provide insights on under-receivals and over-receivals. 

The image shows an example of the **New Purchase Order Receipt Product** page.

![Screenshot of the New Purchase Order Receipt Product page](media/goods-receipt.png)

For information on detailed mapping between Supply Chain Management purchase order and purchase order line statuses, see [Integrate procurement between Supply Chain Management and Field Service](/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/scm-field-service-procurement).

## Purchase order product view within sales order products

 The **Purchase Orders** tab available within the **Sales order products** page lists all of the open purchase order lines for the product, as shown in the following example image.
 
![Screenshot of the **Purchase Orders** tab.](media/po-view-sp.png)

