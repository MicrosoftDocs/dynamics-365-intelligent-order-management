---
author: sumanic
description: This topic describes how to set up the Inventory Visibility Inventory Allocation in Microsoft Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 05/25/2022
ms.topic: how-to
ms.author: sumanic
title: Set up Inventory Visibility Inventory Allocation

---

## Business background and purpose
In many cases, manufacturers, retailers, and other supply chain business holders must pre-allocate stock for important sales channels, locations, or customers, or for specific sales events. Inventory allocation is a typical practice in the sales operational planning process, and is done before the actual sales activities occur and a sales order is created.

For example, a bicycle company has limited stock available for a very popular bike. This company does both online and in-store sales. In each sales channel, the company has a few important corporate partners (marketplaces and large retailers) that demand that a specific portion of the bike's available inventory be saved for them. Therefore, the bicycle company must be able to balance stock distribution across channels and also manage the expectations of its VIP partners. The best way to achieve both goals is to use inventory allocation, so that each channel and retailer can receive specific allocated quantities that can be sold to consumers later.

**Inventory allocation has two basic business purposes:**

**Inventory protection (ringfencing)** – Organizations want to pre-allocate restricted or limited stock to prioritized channels, regions, VIP customers, and subsidiary companies. The Inventory Visibility allocation feature aims to protect the allocated inventory, so that the other allocations, reservations, or other sales demands won't affect the previously allocated inventory.

**Oversell control** – The Inventory Visibility allocation feature aims to put a restriction on the previously allocated quantities, so that the receiving party (for example, a channel or customer group) won't over-consume them when the actual sales transaction that is based on a soft reservation goes into effect.

## Allocation definition in Inventory Visibility Service

Although the allocation feature in Inventory Visibility service doesn't set aside physical inventory quantities, it does refer to available physical inventory quantity to define its initial available to allocate virtual pool quantity. Inventory allocation in Inventory Visibility is a soft allocation. It's done before actual sales transactions occur and doesn't depend on sales orders. For example, you can allocate stock to your most important sales channels or large corporate retailers before any end customers visit the sales channel or retail store to purchase it.

The difference between inventory allocation and inventory soft reservation is that soft reservation is usually linked to actual sales transactions (sales order lines). Therefore, if you want to use the allocation and soft reservation features together, we recommend that you do inventory allocation first and then soft reserve against the allocated quantities. For more information, see Consume as a soft reservation.

The inventory allocation feature lets sales planners or key account managers manage and pre-allocate important stock across allocation groups (such as channels, regions, and customer groups). It also supports real-time tracking, adjustment, and analytics of consumption against allocated quantities, so that replenishment or reallocation can be done on time. This ability to have real-time visibility into allocation, consumption, and allocation balance is especially important at fast-sale or promotion events.

## Terminology

The following terms and concepts are useful in discussions of inventory allocation:


**Allocation group** – The group that owns the allocation, such as a sales channel, customer group, or order type.

**Allocation group value** – The value of each allocation group. For example, web or store might be the value of the sales channel allocation group, whereas VIP or normal might be the value of the customer allocation group.

**Allocation hierarchy** – A means to combine allocation groups in a hierarchical manner. For example, you can define channel as hierarchy level 1, region as level 2, and customer group as level 3. During inventory allocation, you must follow the allocation hierarchy sequence when you specify the value of the allocation group. For example, you might allocate 200 red bikes to the Web channel, the London region, and the VIP customer group.

**Available to allocate** – The virtual common pool that indicates the quantity that is available for further allocation. It's a calculated measure that you can freely define by using your own formula. If you're also using the soft reservation feature, we recommend that you use the same formula to calculate available-to-allocate and available-to-reserve.

**Allocated** – A physical measure that shows the allocated quota that can be consumed by the allocation groups.
**Consumed** – A physical measure that indicates that quantities that have been consumed against the original allocated quantity. As numbers are added to this physical measure, the Allocated physical measure is automatically reduced.
The following illustration shows the business workflow for inventory allocation.

![Allocation.](media/Allocationpp.png)
