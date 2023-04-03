---
title: Set up a carrier pickup schedule 
description: This article explains shipping carrier settings and assignment to fulfillment source in Microsoft Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 03/24/2023
author: anvenkat
ms.author: anvenkat
ms.topic: how-to
ms.custom: bap-template

---

# Set up a carrier pickup schedule

This article explains shipping carrier settings and assignment to fulfillment source in Microsoft Dynamics 365 Intelligent Order Management.

Businesses can set up carrier pickup schedules for their shipping carriers and assign them to their stores or warehouses. Carrier pickup schedules are used to denote the pickup times when the shipping carriers will arrive at their facility to pick up the packages.

To set up carrier pickup schedule follow these steps.

1. Go to **Fulfillment settings** > **Shipping carriers** > **Manage**.
1. Select the shipping carrier.
1. Select the **Pickup Schedule** tab, and select **+New Pickup Schedule**.
1. On the **New Pickup Schedule** page, provide a **Name**. 
1. Select up to 5 pickup slots for any day. The times are listed in the 24-hour format, and should be selected in an ascending order for every successive pickup slot.
1. Select **Save**.

> [!Note] 
> You can maintain multiple pickup schedules for a carrier; however, only one pickup schedule can be assigned to a fulfillment source.

## Assign a carrier pickup schedule to a fulfillment source.

To assign a carrier pickup schedule to a fulfillment source, follow these steps.

1. Go to **Settings** > **Fulfillment Settings** > **Sources** > **Manage**.
1. Select a **Source**.
1. Select the pickup schedule for the carriers.

> [!Note>
> Currently you can only select the pickup schedule for Fedex and UPS parcel carriers. This feature will expand to make this more generic by allowing selection for multiple carriers.

## Use carrier pickup schedules

Carrier APIs, such as FedEx, need an accurate date and time of pickup to accurately calculate the estimated delivery date and time for the shipment. The Carrier pickup schedule table is used by the Carrier API to send the next available pickup time based on the **Working calendar** of the fulfillment source.

## Shipping carrier service types

Shipping carriers offer various service types that can be preconfigured within the **Shipping carrier** setup. 

To set up the master data for carrier service types, follow these steps.

1. Select the shipping carrier, and select **related data**.
1. Select **Carrier services**.
1. Add the relevant information and Select **Save**. 

> [!Note]
> Fields, like **Method code**, **Carrier Code**, and **Service type**, are carrier specific and should be maintained by collaborating with your shipping carriers. 



