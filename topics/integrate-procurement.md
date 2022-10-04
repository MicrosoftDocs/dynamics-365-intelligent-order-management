---
author: anvenkat
description: This topic describes how to integrate procurement in Microsoft Dynamics 365 Supply Chain Management with Microsoft Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 09/16/2022
ms.topic: conceptual
ms.author: anvenkat

title: Integrate procurement in Supply Chain Management with Intelligent Order Management

---

# Integrate procurement in Supply Chain Management with Intelligent Order Management

This topic describes how to integrate procurement in Microsoft Dynamics 365 Supply Chain Management with Microsoft Dynamics 365 Intelligent Order Management.

For more information on the general overview of **Purchase Orders** please refer to [Purchase order overview](/dynamics365/supply-chain/procurement).

To extend support for inbound transactions and provide transaction visibility alongside inventory visibility, a **Purchase Orders** entity has been introduced within Intelligent Order Management. The **Purchase Orders** entity includes the following features: 

- Dual-write support for purchase orders is available so that purchase order data seamlessly flows from Microsoft Dataverse into Intelligent Order Management and is visible in real or near real time.
- Create Purchase Orders: Users can create a Purchase Order (PO) from Intelligent Order Management. This will be processed  in Supply Chain Management via Dual write- support
- **Purchase Order** entity user interface fields have been designed to meet the specific needs of support for sales order fulfillment scenarios.
- Transaction status and visibility of purchase orders from Supply Chain Management is directly available to view within Intelligent Order Management.
- The **Purchase Order product** view is available within the **Sales Order** products tab, which provides visibility to the incoming inventory from individual purchase order transactions.
- The **Purchase Order Products** view on the site map for easy access to the individual **purchase order line status** at product level.

## Dual-write support for purchase orders

 The following prerequisites must be met to activate dual-write support for purchase orders:

- It is important to have the following dual-write packages installed or updated to ensure that you have the latest versions.
    - Dual-write core solution package
    - Dual-write Application Core package
    - Dual-write Finance package
    - Dual-write Human Resources package
- If your environment already has dual-write for sales orders installed, ensure that it is up-to-date.
- If you have an older version of Intelligent Order Management running in your instance which already has dual-write installed, ensure that you import the UX solution package for Purchase Orders and Transfer Orders.

### General guidelines for installing the add-on UX package for new users

- If you are installing Intelligent Order Management first, you should install the dual-write solution before importing the UX package solution.
- If you are installing the dual-write solution first, the UX package solution will be imported as part of the install. Intelligent Order Management can then be installed afterwards.

### Initial sync of prerequisite tables

After all of the prerequisites above have been met, you must do an initial synchronization of the prerequisite and dependent master data and tables so that existing purchase orders are available in both Supply Chain Management and Intelligent Order Management. For instructions on what tables to sync and how to sync them, see [Integrate procurement between Supply Chain Management and Field Service](/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/scm-field-service-procurement).

### Dual-write mapping reference

For information on dual-write purchase order mapping, see [Mapping reference](/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/mapping-reference#183).

## Create a purchase order 

To create a purchase order in Intelligent Order Management, follow these steps.

1. Go to **Purchase orders** in site map.
1. Select **+New**. and enter mandatory fields   and **Save**
1. On the **Purchase Order** header entity, enter values for the **Name**, **Receiving Warehouse**,**Site**,**Vendor**, and **Company** fields.
   Note that the **Name** is used to denote the **Purchase Order** number that will be assigned in Supply Chain Management. 
   Note that if you save the header without entering any of the fields , and would like immediately edit them saving, you will have to first confirm the header in
   Supply Chain management before you can update any of the fields on the **Purchase Order** form.
3. Select **Save**.
4. Select **New Purchase Order Product** and then select **Existing Product**, **Line number**, **Associate to Warehouse**, **Quantity**, and **Unit of measure**. 
5. Select **Save**. If the transaction saves successfully, this means that the dual-write operations was successful and the purchase order was created and updated within Dynamics Supply Chain Management.

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

- Purchase orders can be created and updated by Dataverse users, but the process and data are controlled by Supply Chain Management. The constraints on updates to purchase order columns in Supply Chain Management apply when updates come from Intelligent Order Management. For example, you can't update a purchase order if it has been finalized. You can't make updates on a purchase order created in Intelligent Order Management until the purchase order is confirmed in Supply Chain Management.
- Several columns are only managed by Supply Chain Management and can't be updated in Intelligent Order Management. To learn which columns can't be updated, review the mapping tables in the product. Most of these columns are set to read-only on Dataverse pages.

    For example, the columns for price information are managed by Supply Chain Management. Supply Chain Management has trade agreements in place and columns such as **Unit price**, **Discount**, and **Net amount** come only from Supply Chain Management. To ensure that a price is synced to Intelligent Order Management, in Dataverse you should use the **Sync** feature on the **Purchase Order** and **Purchase Order Product** pages after purchase order data has been entered. For more information, see [Sync with the Dynamics 365 Supply Chain Management procurement data on demand](/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/scm-field-service-procurement#sync-procurement).
- Product receipts (also known as purchase order receipts in Dataverse) are managed by Supply Chain Management and can't be created from Dataverse if Supply Chain Management is installed. The product receipts from Supply Chain Management are synced from Supply Chain Management to Dataverse.
- Under-delivery is allowed in Supply Chain Management. The OneFSSCM solution adds logic so that when a product receipt line (or purchase order receipt product in Dataverse) is created or updated, an inventory journal row is created in Dataverse to adjust the remaining quantity that is on order for under-delivery scenarios.

## Transaction status and visibility of purchase orders from Supply Chain Management directly within Intelligent Order Management

As a purchase order progresses in Supply Chain Management, status updates flow back to Intelligent Order Management for tracking and visibility. Open purchase order lines and **purchase order line status** can be viewed by accessing the site map entry **Purchase Order products** to stay informed on incoming inventory. Purchase order product fields such as **Expected date** and **Confirmed delivery date** provide insights to the in-transit purchase orders.

The **Purchase Order Receipt** entity and **Purchase Order Receipt products** entity provides visibility to the **Received inventory quantity** and **Remaaining inventory quanitty**, along with the **Product receipt date** and **Purchased quantity**. The **Purchase Order Receipt** entity within a purchase order can be accessed via a separate tab on the purchase order form. Fields on this form can provide insights on under-receivals and over-receivals. Below is a screenshot of the **New Purchase Order Receipt Product** page.

![Screenshot of the **New Purchase Order Receipt Product** page](media/goods-receipt.png)

For information on detailed mapping between Supply Chain Management purchase order and purchase order line statuses, see [Integrate procurement between Supply Chain Management and Field Service](/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/scm-field-service-procurement).

## Purchase order product view within sales order products

 The **Purchase Orders** tab available within the **Sales order products** page lists all of the open purchase order lines for the product, as in the screenshot below.
 
![Screenshot of the **Purchase Orders** tab.](media/po-view-sp.png)

