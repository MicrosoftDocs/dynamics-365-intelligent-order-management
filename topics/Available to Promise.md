---
author: sumanic
description: This topic describes Available to promise capabilities in Microsoft Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 09/27/2022
ms.topic: how-to
ms.author: sumanic
title: Inventory Available to promise

---

# Inventory Available to Promise

Availible to Promise is a projected amount of inventory that will be available in the incoming period to be able to promise customer orders.
Use of this calculation can greatly increase your order fulfillment capability.

For many manufacturers, retailers, or sellers, it isn't enough just to know what is currently on hand. They must have full visibility into future availability. This future availability should consider future supply, future demand, and ATP.

# Pre-requisite

a. Submit on-hand change schedule changes to Inventory Visibility rovided that the dates are within the period that is defined by the **Schedule period** setting.

b. Below are the API details to submit a on-hand schedule change request. Please note that these APIs are available from Dynamics 365 Supply Chain Management Invnetory visibility add in.
More details can be found in [Dynamics 365 Inventory Services.](https://docs.microsoft.com/en-us/dynamics365/supply-chain/inventory/inventory-visibility-available-to-promise)

|Path|Method|Description|
|----|------|-----------|
|/api/environment/{environmentId}/onhand/changeschedule|	POST	|Create one scheduled on-hand change.|
|/api/environment/{environmentId}/onhand/changeschedule/bulk|	POST	|Create multiple scheduled on-hand changes.|

# Enable and set up the features
Before you can use ATP, you must enable one or more key setups as below:

a. **Available To Promise** settings should be enabled. For this follow the below steps:

   i. Goto **Settings**. Click on **Index and Reservation**.
 
   ii. Click on the tab **Feature Management and Settings**
 
   iii.Enable **OnHandChangeSchedule** option.
   
   ![ATP.](media/ATP.png)
   
 b. The calculated measure for **ATP Setting** must be defined.

The **ATP calculated measure** is a predefined calculated measure that is typically used to find the on-hand quantity that is currently available. The **supply quantity** is the sum of quantities for those physical measures that have a modifier type of addition, and the **demand quantity** is the sum of quantities for those physical measures that have a modifier type of subtraction.

You can add multiple calculated measures to calculate multiple ATP quantities. However, the total number of distinct physical measures across all ATP calculated measures should be less than nine.

[!NOTE]
> - A calculated measure is a composition of physical measures. Its formula can include only physical measures without duplicates, not calculated measures.

**For example**, you set up the following calculated measure:

**On-hand-available** = (PhysicalInvent + OnHand + Unrestricted + QualityInspection + Inbound) – (ReservPhysical + SoftReservePhysical + Outbound)

The sum (PhysicalInvent + OnHand + Unrestricted + QualityInspection + Inbound) represents supply, and the sum (ReservPhysical + SoftReservePhysical + Outbound) represents demand. Therefore, the calculated measure can be understood in the following way:

**On-hand-available** = Supply – Demand

You can add another calculated measure to calculate the On-hand-physical ATP quantity.

**On-hand-physical** = (PhysicalInvent + OnHand + Unrestricted + QualityInspection + Inbound) – (Outbound)

There are eight distinct physical measures across those two ATP calculated measures: PhysicalInvent, OnHand, Unrestricted, QualityInspection, Inbound, ReservPhysical, SoftReservePhysical, and Outbound.

For more information about calculated measures, see [Calculated measures](https://learn.microsoft.com/en-us/dynamics365/supply-chain/inventory/inventory-visibility-configuration#calculated-measures).
 
   i.    Goto **Settings**. Click on **Index and Reservation**.
 
   ii.   Click on the tab **ATP Settings**
   
   iii.  Select the **Data Source** from the dropdown.
   
   iv.   Select the **Calculated Measure** for the selected **Data Source**.
   
   v.    Assign the **Schedule Period**. Currently this is supported to a max of 7 days.
   
    ![ATPSetting.](media/ATPSetting.png)
   
