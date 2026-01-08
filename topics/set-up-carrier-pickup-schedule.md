---
title: Set up a carrier pickup schedule
description: This article explains how to set up a shipping carrier and assign it to a fulfillment source in Microsoft Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 03/21/2025
ms.custom: 
  - bap-template
author: anvenkat
ms.author: anvenkat
ms.topic: how-to
---

# Set up a carrier pickup schedule

This article explains how to set up a shipping carrier and assign it to a fulfillment source in Microsoft Dynamics 365 Intelligent Order Management.

Businesses can set up pickup schedules for their shipping carriers, and then assign them to their stores or warehouses. A carrier pickup schedule indicates the times when a shipping carrier will arrive at a business's facility to pick up packages.

To set up a carrier pickup schedule, follow these steps:

1. Go to **Fulfillment settings** \> **Shipping carriers** \> **Manage**.
1. Select the shipping carrier.
1. On the **Pickup Schedule** tab, select **New Pickup Schedule**.
1. On the **New Pickup Schedule** page, enter a name.
1. Select up to five pickup slots for any day. Times are listed in 24-hour format and should be selected in ascending order for each successive pickup slot.
1. Select **Save**.

> [!NOTE]
> You can maintain multiple pickup schedules for each carrier. However, only one pickup schedule can be assigned to a fulfillment source.

## Assign a carrier pickup schedule to a fulfillment source

To assign a carrier pickup schedule to a fulfillment source, follow these steps:

1. Go to **Settings** \> **Fulfillment Settings** \> **Sources** \> **Manage**.
1. Select a source.
1. Select the pickup schedule for the carrier.

> [!NOTE]
> Currently, you can select a pickup schedule only for the FedEx and UPS parcel carriers. However, this feature will eventually be expanded and become more generic, so that you can select a pickup schedule for multiple carriers.

## Using carrier pickup schedules

Carrier APIs, such as FedEx, need an accurate pickup date and time to accurately calculate the estimated delivery date and time for a shipment. The Carrier API uses the Carrier pickup schedule table to send the next available pickup time, based on the working calendar of the fulfillment source.

## Shipping carrier service types

Shipping carriers offer different service types that can be preconfigured in the **Shipping carrier** setup.

To set up the master data for carrier service types, follow these steps:

1. Select the shipping carrier, and then select **Related data**.
1. Select **Carrier services**.
1. Add the relevant information, and then select **Save**.

> [!NOTE]
> Fields such as **Method code**, **Carrier Code**, and **Service type** are carrier-specific. To maintain them, you should work with your shipping carriers.
