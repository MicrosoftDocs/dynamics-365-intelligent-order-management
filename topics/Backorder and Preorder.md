---
author: sumanic
description: This topic describes Backorder and Preorder management with D365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 09/13/2022
ms.topic: how-to
ms.author: sumanic
title: Backorder and Preorder management

---

# Backorder and Preorder management with Dynamics 365 Intelligent Order Management

This topic describes how Intelligent Order Management can handle Backorders and Preorders giving cutsomers the flexibility to handle their inventory in the most optimal way.

## Backorders
When a customer places an order for an item that is not currently in stock, the customer may be informed it is on backorder and can still make payment with the promise of future delivery. Items available on backorder may indicate a date when they will be back in stock. 
A backorder is an order for a product or service that cannot be filled at the current time due to a lack of available supply.
With appropiate backorder management customers can get the below benefits:

a. Optimized utilization of inventory.

b. Regular inventory checks to fulfill backorders.

## Preorders
Preorder is the act of ordering a product even before the product is released. Ability to handle preorders gives a great flexibility to handle inventory appropriately.
Pre-orders allow consumers to guarantee immediate delivery on release, manufacturers can gauge how much demand there will be and hence how large initial production runs 
should be, and sellers can be assured of minimum sales. Additionally, high pre-order rates can be used to further increase sales.

## Pre-requisite Settings

a. **Available To Promise** settings should be enabled. For this follow the below steps:

  i. Goto **Settings**. Click on **Index and Reservation**.
   
  ii. Click on the tab **Feature Management and Settings**
   
  iii.Enable **OnHandChangeSchedule** option.
![ATP.](media/ATP.png)

b. **On hand schedule changes** should be uploaded in case you want to provide your customers an expected ship date. To do this follow the instructions [here.](https://docs.microsoft.com/en-us/dynamics365/supply-chain/inventory/inventory-visibility-available-to-promise)

c. Appropriate **Settings** described below should be enabled.

   i.  Goto **Settings**. Click on **General app settings**.
   
   ii. Goto **Order handling preferences**  and click on **Manage**.
   
   iii.Goto **Backorders** and turn **On** the capability.
   
   iv. Once it is enabled, you will see a section to add **Cancelation SLA**. Here you could enter the number of days upto 
        which you want to try on fulfilling the backorder. After that tenure, the order will be automatically canceled.
        
   ![Backorder Product.](media/Backorder.png)
   
d. Enable **Preorder** eligibility for **Products**. 
  
   i.  Goto **Demand Planning** in sitemap and select **Products**.
   
   ii. Select the **Product** by clicking on the item.
   
   iii.If the product is preorder eligible then select **Yes** for the field **Pre-order Eligible**.
   
   iv. Once you select it will enable a field to enter the **Launch Date**. Enter the date when this product will be released.
   
   v.  Click on **Save** or **Save & Close**.

![Preorder Product.](media/Preorder.png)

## How does Backorder work?

When an order is created in Dynamics 365 Intelligent Order Management, an inventory check could be initiated as part of **policy assignment** or **Fulfillment and Returns optimization**. In either of these two processes, inventory may not be found for the **Order product**. In such cases the order line is updated with **Status Reason** as **Backorder Hold**.

With the **ATP Settings** enabled, the backordered lines would also be updated with the **Inventory Availibility Date** for the product and an **Estimated Shipment Date**.

Below is a sample order journey with policy based fulfillment asisgnment.

![Orchestration.](media/SampleOrch.png)

When the order lines are **backordered**, below is a smaple sceen highlighting the key updates that happen to a sales order lines.

![Backorder.](media/BackorderHold.png)

Once this happens, based on he initial **pre-requisite settings**, a background job will run automatically that will trigger inventory check everyday once to check if inventory is found and the order lines can be moved to subsequent fulfillment.
It will be intelligent enough to determine from the orchestation if inventory check would be triggered independently or triggered through **Fulfillment and Returns optimization**.

A job log will be now available to show the list of job runs and their statuses. This can be located on the **Home Page** left menu under **Monitoring** as **Background Jobs**. It will show you the list of job runs, their statuses and the number of records it has successfully processed and moved to fulfillment.

![Job.](media/Job.png)

If a background job fails, you will also be able to manually run it using the **Run** option in the upper menu bar. Select the **Back-Order Job** and this iwll start a new instance of the background job.

On clicking the Job line, you will be able to see the details of the background job run.

![Jobdetails.](media/Jobdetails.png)

## How does Preorder work?

When an order is created in Dynamics 365 Intelligent Order Management, if the order contains products that are marked as **Preorder eligible** and has a **Launch date**, then those lines in sales order are moved to **Status Reason** as **Preorder Hold**.

The sales order line gets updated with the **Launch Date** from the **Products** defined as part of the **Pre-requisite Settings**.

![Preorder.](media/PreOrderHold.png)

Once this happens, a background job will run automatically trigger inventory check on the **Lauch Date** and the order lines can be moved to subsequent fulfillment.
It will be intelligent enough to determine from the orchestation if inventory check would be triggered independently or triggered through **Fulfillment and Returns optimization**.

If inventory check fails and no inventory found, then the order lines will move to **Backorder Hold** status.

A job log will be now available to show the list of job runs and their statuses. This can be located on the **Home Page** left menu under **Monitoring** as **Background Jobs**. It will show you the list of job runs, their statuses and the number of records it has successfully processed and moved to fulfillment.

![PreorderJob.](media/PreorderJob.png)

If a background job fails, you will also be able to manually run it using the **Run** option in the upper menu bar. Select the **Pre-Order Job** and this will start a new instance of the background job.

On clicking the Job line, you will be able to see the details of the background job run.

![PreJobDetails.](media/Predet.png)
