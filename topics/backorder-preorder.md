---
author: sumanic
description: Learn how to set up and manage backorder and preorder functionality in Microsoft Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 01/27/2026
ms.custom: 
  - bap-template
ms.topic: how-to
ms.author: sumanic
title: Set up backorder and preorder functionality

---

# Set up backorder and preorder functionality

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This article describes how to set up and manage backorder and preorder functionality in Microsoft Dynamics 365 Intelligent Order Management. Management of backorders and preorders gives you the flexibility to optimize the handling of your inventory.

## Backorders

A backorder is an order that was placed for a product or service, but that can't immediately be fulfilled because of a lack of available supply. Customers who place an order for an item that isn't currently in stock might be informed that the product is on backorder. They might be told that they can still make a payment in return for a promise of future delivery. Items that are on backorder might indicate a date when they are back in stock.

Effective backorder management can provide the following benefits:

- Optimized use of inventory
- Regular inventory checks to fulfill backorders

### How backorder functionality works

When an order is created in Intelligent Order Management, an inventory check can be run as part of either the policy assignment process or the fulfillment and returns optimization process. In both these processes, inventory might not be found for the ordered product. In this case, the order line is updated with a **Status Reason** value of **Backorder Hold**.

If the [available-to-promise (ATP) settings are enabled](#enable-the-atp-settings), the **Inventory Availability Date** and **Estimated Shipment Date** values for the product are updated on the backordered lines.

The following illustration shows an example of an order orchestration journey that has a policy-based fulfillment assignment. 

:::image type="content" source="media/SampleOrch.png" alt-text="Screenshot of an orchestration journey with a policy-based fulfillment assignment.":::

The example in the following illustration highlights key updates that are made to sales order lines when they're backordered. The order line is updated with a **State** value of **Sale Order Product on Hold** and a **Status Reason** value of **Backorder Hold**. The **Estimated Shipment Date** and **Inventory Availability Date** values are also updated.

:::image type="content" source="media/BackorderHold.png" alt-text="Screenshot of key updates to backordered sales order lines.":::

After a product is backordered, a background job that is automatically run triggers an inventory check, based on the launch date, to determine whether the order lines can be moved to subsequent fulfillment. From the orchestration, Intelligent Order Management determines whether an inventory check should be triggered independently or through the fulfillment and returns optimization process.

A job log is available, where you can view the list of job runs, the status of each, and the number of records that have been successfully processed and moved to fulfillment. To open the job log, on the **Home** page, in the left navigation, under **Monitoring**, select **Background jobs**.

If a background job fails, you can manually run it by using the **Run** option on the upper toolbar. Select **Back-Order Job** to start a new instance of the background job.

To view the details of a background job run, select the job line.

## Preorders

A preorder is an order that is placed for a product before that product is released. The ability to handle preorders gives you more flexibility to handle inventory effectively.

Preorders provide the following benefits:

- **Manufacturers** can gauge how much demand there will be and how large initial production runs should be.
- **Sellers** can be assured of minimum sales. High preorder rates can also be used to further increase sales.
- **Customers** can be guaranteed immediate delivery when products are released.

### How preorder functionality works

When an order is created in Intelligent Order Management, if it contains products that are marked as **Preorder eligible** and that have a launch date, those lines on the sales order are updated with a **Status Reason** value of **Preorder Hold**. They're also updated with the product launch date, as defined in the prerequisite settings.

:::image type="content" source="media/PreOrderHold.png" alt-text="Screenshot of a sales order line updated with a Preorder Hold status and a launch date.":::

After a product is preordered, a background job that is automatically run triggers an inventory check, based on the launch date, to determine whether the order lines can be moved to subsequent fulfillment. From the orchestration, Intelligent Order Management determines whether an inventory check should be triggered independently or through the fulfillment and returns optimization process.

If an inventory check fails, and no inventory is found, the status of the order lines is updated to **Backorder Hold**.

A job log is available, where you can view the list of job runs, the status of each, and the number of records that were successfully processed and moved to fulfillment. To open the job log, on the **Home** page, in the left navigation, under **Monitoring**, select **Background Jobs**.

If a background job fails, you can manually run it by using the **Run** option on the upper toolbar. Select **Pre-Order Job** to start a new instance of the background job.

To view the details of a background job run, select the job line.

## Set up backorder and preorder functionality

To set up backorder and preorder functionality in Intelligent Order Management, complete the following procedures.

### Enable the ATP settings

First, you must enable the ATP settings.

1. Go to **Settings**.
1. In the left navigation, under **Inventory settings**, select **Index and Reservation**.
1. On the **Feature Management & Settings** tab, turn on the **OnHandChangeSchedule** option.

:::image type="content" source="media/ATP.png" alt-text="Screenshot of the OnHandChangeSchedule option turned on.":::

### Upload on-hand schedule changes

Next, you should upload on-hand schedule changes in case you want to provide an expected ship date to your customers. For instructions, see [Inventory Visibility on-hand change schedules and available to promise](/dynamics365/supply-chain/inventory/inventory-visibility-available-to-promise).

### Enable general app settings

Next, you must enable some general app settings.

1. Go to **Settings**. 
1. In the left navigation, under **App settings**, select **General app settings**.
1. Go to **Order handling preferences**, and then select **Manage**.
1. Set the **Backorders** option to **On**.
1. After you enable backorders, a **Cancellation SLA** section appears. Here, you can optionally enter the number of days that you want to try to fulfill the backorder. After that number of days has passed, the order will automatically be canceled.

:::image type="content" source="media/Backorder.png" alt-text="Screenshot of the Order handling preferences page.":::

### Enable preorder eligibility for products

Next, you must enable preorder eligibility for products.

To enable preorder eligibility for a product, follow these steps:

1. In the sitemap, go to **Demand Planning**, and then select **Products**.
1. Select a product.
1. If the product is preorder eligible, in the **Pre-order Eligible** field, select **Yes**.
1. In the **Launch Date** field, enter the date when the product is released.
1. Select **Save** or **Save & Close**.

:::image type="content" source="media/Preorder.png" alt-text="Screenshot of the Preorder Eligible and Launch Date fields on the Product page.":::
