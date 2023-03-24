---
author: Anusha Venkatesan
description: This article describles shipping carrier settings and assignment to fulfillment source in Microsoft Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 03/24/2023
ms.topic: overview
ms.author: anvenkat

title: setup carrier pick up schedule  
---

## Set up of carrier pick up schedule

Businesses can set up various carrier pick up schedules for their shipping carriers and assign them to their stores or warehouses. Carrier pick up schedules are used to denote the various pick up timings that the shipping carriers arrive at their facility to pick up the packages.

To set up carrier pick up schedule follow the steps below:
1. Go to **Fulfillment settings** > **Shipping carriers** > **Manage**
2. Select the shipping carrier that you want to attach a pick up schedule.
3. Select **Pickup Schedule** tab and select **+New Pickup Schedule**
4. In the **New Pickup Schedule** screen provide a **Name** in the selection
5. You will see the days of the week listed where you can select up to 5 pick up slots for any day.
6. The times are listed in the 24 hour format and should be selected in an ascending order for every successive pick up slot.
7. Select **Save** after maintaining the pick up schedule.

Please note that you can maintain multiple pick up schedules for a carrier, however only one of them can be assigned to a fulfillment source.

## Assigning the carrier pick up schedule to a fulfillment source.

1. Go to **Settings** > **Fulfillment Settings** > **Sources** > **Manage**
2. Select a **Source**
3. Select pick up schedule for the carriers defined in the fulfillment source settings.

Please note that the current capability allows to select the pick up schedule for Fedex and UPS parcel carriers only. This feature will expand to make this more generic by allowing selection for multiple carriers.

## Usage of carrier pick up schedule

Carrier API's such as FedEx need an accurate date and time of pick up to be able to accurately calculate the Estimated delivery dates and times for the shipment. Carrier pick up schedule table is checked by carrier API to send them the next available pick up time based on the **Working calendar** of the fulfillment source.

## Shipping carrier service types

Shipping carriers offer various service types that can be preconfigured within the **Shipping carrier** set up. follow the steps below to set up the master data for various service types.

1. Select the shipping carrier and select **related data**.
2. Select **Carrier services**
3. Add the relevant information here and save.Please note that the fields like **Method code**, **Carrier Code** and **Service type** are carrier specific and should be maintained by collaborating with your shipping carriers. 



