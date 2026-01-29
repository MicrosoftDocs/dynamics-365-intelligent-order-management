---
title: Set up a fulfillment source working calendar
description: Learn about how to set up a working calendar and assign it to a fulfillment source in Microsoft Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 01/28/2026
ms.custom: 
  - bap-template
author: anvenkat
ms.author: anvenkat
ms.topic: how-to
---

# Set up a fulfillment source working calendar

This article explains how to set up a working calendar and assign it to a fulfillment source in Microsoft Dynamics 365 Intelligent Order Management.

Businesses can set up working calendars for their stores or warehouses, and then assign them to fulfillment sources in fulfillment source settings. Use calendars to describe working hours, non-working hours, and time-off information.

To set up a calendar, follow these steps:

1. Go to **Fulfillment settings** \> **Holiday Calendar** \> **Manage**.
1. On the **Quick create** page, enter a name and description for the calendar, and then select **Save and close**. A calendar that uses default working hours is shown.
1. To add the actual working hours, select **New**, and then select **Working hours**.
1. Select the calendar's start date (for example, January 1, 2023), and then select **Custom**.
1. Select **Choose an end date**, and then select the end date of the calendar year (for example, December 31, 2023).
1. Clear the selection of any non-working days.
1. Select the working hours by selecting each day, changing the start time and end time, and selecting **Apply**.

> [!NOTE]
> Select the time zone of the calendar based on the time zone of the fulfillment source that you link the calendar to.

## Set up nonworking hours or holidays

> [!NOTE]
> You can also use nonworking hours to set up time off.

To set up nonworking hours or holidays, follow these steps:

1. Select **New**, and then select **Non-Working**.
1. Select the date and the reason for the holiday.
1. Select the start time and end time.

> [!NOTE]
> The default time zone is the user's current time zone.

## Assign a calendar to a fulfillment source

To assign a calendar to a fulfillment source, follow these steps:

1. Go to **Settings** \> **Fulfillment Settings** \> **Sources** \> **Manage**.
1. Select a source.
1. Under **Schedule**, in the **Working Calendar** field, select a calendar.

## Using a calendar for Fulfillment optimization

In Intelligent Order Management, the Fulfillment optimization API uses a working calendar when the **Respect warehouse timings** constraint is enabled. If you enable this constraint, the API checks the working calendar of the fulfillment source to determine whether the fulfillment source is working. If the source isn't working, the API filters it out from the selection, and the orders are routed to a source that *is* working.

## Using a calendar to determine carrier pickup times

Carrier APIs, such as FedEx, need an accurate pickup date and time to accurately calculate the estimated delivery date. The Fulfillment optimization API uses the working calendar to determine whether the date and time are during the working hours of the fulfillment source. If the date and time are outside the working hours, the next available working day is checked.
