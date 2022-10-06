---
author: sumanic
description: This article describes backorder and preorder management in Microsoft Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 10/06/2022
ms.topic: how-to
ms.author: sumanic
title: Backorder and Preorder management

---

# Backorder and Preorder management with Dynamics 365 Intelligent Order Management

[!include [banner](includes/banner.md)]

This article describes backorder and preorder management in Microsoft Dynamics 365 Intelligent Order Management. Managing backorders and preorders gives you the flexibility to optimize the handling of your inventory.

## Backorders

A backorder is an order placed for a product or service that can't immediately be fulfilled due to a lack of available supply. When a customer places an order for an item that is not currently in stock, the customer may be informed the product is on backorder and that they can still make payment with the promise of future delivery. Items available on backorder may indicate a date when they'll be back in stock.

Effective backorder management can provide you with the following benefits:

- Optimized use of inventory.
- Regular inventory checks to fulfill backorders.

## Preorders

A preorder is an order placed for a product before that product is released. The ability to handle preorders provides greater flexibility to handle inventory effectively.

Preorders allow customers to guarantee immediate delivery on release, manufacturers to gauge how much demand there will be (and how large initial production runs should be), and sellers to be assured of minimum sales. High preorder rates can also be used to further increase sales.

## Prerequisites

### Enable available to promise (ATP) settings

First, you should enable available to promise (ATP) settings. For this follow the below steps:

To enable available to promise (ATP) settings, follow these steps.

1. Go to **Settings**. 
1. Select **Index and Reservation**.
1. Select the **Feature Management and Settings** tab.
1. Turn on the **OnHandChangeSchedule** option.

![Enable available to promise (ATP) settings](media/ATP.png)

### Upload on-hand schedule changes

Next, on-hand schedule changes should be uploaded in case you want to provide your customers with an expected ship date. For instructions, see [Inventory Visibility on-hand change schedules and available to promise](/dynamics365/supply-chain/inventory/inventory-visibility-available-to-promise).

### Enable general app settings

Next, you must enable some general app settings.

To enable general app settings, follow these steps.

1. Go to **Settings**. 
1. Select **General app settings**.
1. Go to **Order handling preferences**, and then select **Manage**.
1. Set the **Backorders** option to **On**.
1. After enabling backorders, a **Cancellation SLA** section appears. Optionally, here you can enter the number of days up to which you want to try fulfilling the backorder. After that number of days, the order will automatically be canceled.
        
![Backorder Product](media/Backorder.png)
   
### Enable preorder eligibility for products

Next, you must enable preorder eligibility for products. 

To enable preorder eligibility for a product, follow these steps.
  
1. In the sitemap, go to **Demand Planning**, and then select **Products**.
1. Select a product.
1. If the product is preorder eligible, then for **Pre-order Eligible**, select **Yes**.
1. For **Launch Date**, enter the date when the product will be released.
1. Select **Save**, or select **Save & Close**.

![Preorder Product.](media/Preorder.png)

## How backorder works

When an order is created in Intelligent Order Management, an inventory check can be initiated as part of either the policy assignment or fulfillment and returns optimization processes. In either of these two processes, inventory may not be found for the ordered product. In such cases the order line is then updated with a **Status Reason** of **Backorder Hold**.

When **ATP Settings** is enabled, backordered lines will have the **Inventory Availability Date** and **Estimated Shipment Date** values updated for the product.

The following image shows an example order orchestration journey with a policy-based fulfillment assignment.

![Orchestration journey with a policy-based fulfillment assignment](media/SampleOrch.png)

The following example image highlights key updates that happen to a sales order line when the order lines are backordered.

![Backorder key updates](media/BackorderHold.png)

Once a product is backordered, based on the initial prerequisite settings a background job will run automatically to trigger a daily inventory check to determine if inventory is found and the order lines can be moved to subsequent fulfillment. Intelligent Order Management will determine from the orchestration if an inventory check should be triggered independently or triggered through the fulfillment and returns optimization process.

A job log will then be available to show the list of job runs and their statuses. The job log (named **Background Jobs**) is located on the **Home Page** left navigation pane under **Monitoring**. Selecting **Background Jobs** will show you the list of job runs, their statuses, and the number of records that have been successfully processed and moved to fulfillment.

![Active Background Order Processing Job Runs page](media/Job.png)

If a background job fails, you'll also be able to manually run the job using the **Run** option on the upper menu. Select **Back-Order Job** to start a new instance of the background job.

If you select the job line, you'll be able to see the details of the background job run.

![New Background Order Processing Job Run page](media/Jobdetails.png)

## How preorder works

When an order is created in Intelligent Order Management, if the order contains products that are marked as **Preorder eligible** and have a **Launch date**, then those lines in the sales order are updated to a **Status Reason** of **Preorder Hold**.

The sales order line gets updated with the product launch date as defined in the prerequisite settings.

![Sales order line with preorder hold status and and launch date highlighted](media/PreOrderHold.png)

Once a product is preordered, a background job will run automatically to trigger an inventory check based on the launch date to determine if the order lines can be moved to subsequent fulfillment. Intelligent Order Management will determine from the orchestration if inventory check should be triggered independently or triggered through the fulfillment and returns optimization process.

If an inventory check fails and no inventory is found, then the order lines will be updated to a status of **Backorder Hold**.

A job log will then be available to show the list of job runs and their statuses. The job log (named **Background Jobs**) is located on the **Home Page** left navigation pane under **Monitoring**. Selecting **Background Jobs** will show you the list of job runs, their statuses, and the number of records that have been successfully processed and moved to fulfillment.

![PreorderJob.](media/PreorderJob.png)

If a background job fails, you'll also be able to manually run it using the **Run** option in the upper menu. Select **Pre-Order Job** to start a new instance of the background job.

If you select the job line, you'll be able to see the details of the background job run.

![PreJobDetails.](media/Predet.png)
