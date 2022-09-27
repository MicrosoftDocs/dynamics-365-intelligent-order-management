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
More details can be found in [Dynamics 365 Inventory Services.](https://docs.microsoft.com/en-us/dynamics365/supply-chain/inventory/inventory-visibility-available-to-promise).

# Enable and set up the features
Before you can use ATP, you must enable one or more key setups as below:

a. **Available To Promise** settings should be enabled. For this follow the below steps:

   i. Goto **Settings**. Click on **Index and Reservation**.
 
   ii. Click on the tab **Feature Management and Settings**
 
   iii.Enable **OnHandChangeSchedule** option.
   
   ![ATP.](media/ATP.png)
