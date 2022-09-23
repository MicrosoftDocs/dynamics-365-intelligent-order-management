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

    i.  Goto **Settings**. Click on **Index and Reservation**.
   
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
