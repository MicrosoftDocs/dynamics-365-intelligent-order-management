---
title: Set up a fulfillment source working calendar
description: This article explains how to set up a working calendar and assign it to a fulfillment source in Microsoft Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 04/12/2024
ms.custom: 
  - bap-template
author: anvenkat
ms.author: anvenkat
ms.topic: how-to
ms.custom: bap-template

---

# Set up a fulfillment source working calendar

This article explains how to set up a working calendar and assign it to a fulfillment source in Microsoft Dynamics 365 Intelligent Order Management.

Businesses can set up working calendars for their stores or warehouses, and then assign them to fulfillment sources in fulfillment source settings. Calendars are used to describe working hours, non-working hours, and time-off information.

To set up a calendar, follow these steps.

1. Go to **Fulfillment settings** \> **Holiday Calendar** \> **Manage**.
1. On the **Quick create** page, enter a name and description for the calendar, and then select **Save and close**. A calendar that uses default working hours is shown.
1. To add the actual working hours, select **New**, and then select **Working hours**.
1. Select the calendar's start date (for example, January 1, 2023), and then select **Custom**.
1. Select **Choose an end date**, and then select the end date of the calendar year (for example, December 31, 2023).
1. Clear the selection of any non-working days.
1. Select the working hours by selecting each day, changing the start time and end time, and selecting **Apply**.

> [!NOTE]
> The time zone of the calendar must be selected based on the time zone of the fulfillment source that the calendar will be linked to.

## Set up non-working hours or holidays

> [!NOTE]
> Non-working hours can also be used to set up time off.

To set up non-working hours or holidays, follow these steps.

1. Select **New**, and then select **Non-Working**.
1. Select the date and the reason for the holiday.
1. Select the start time and end time.

> [!NOTE]
> The default time zone is the user's current time zone.

## Assign a calendar to a fulfillment source

To assign a calendar to a fulfillment source, follow these steps.

1. Go to **Settings** \> **Fulfillment Settings** \> **Sources** \> **Manage**.
1. Select a source.
1. Under **Schedule**, in the **Working Calendar** field, select a calendar.

## Using a calendar for Fulfillment optimization

In Intelligent Order Management, a working calendar is used by the Fulfillment optimization API when the **Respect warehouse timings** constraint is enabled. If this constraint is enabled, the working calendar of the fulfillment source is checked to determine whether the fulfillment source is working. If the source isn't working, it's filtered out from the selection, and the orders are routed to a source that *is* working.

## Using a calendar to determine carrier pickup times

Carrier APIs, such as FedEx, need an accurate pickup date and time to accurately calculate the estimated delivery date. The Fulfillment optimization API uses the working calendar to determine whether the date and time are during the working hours of the fulfillment source. If the date and time are outside the working hours, the next available working day is checked.
