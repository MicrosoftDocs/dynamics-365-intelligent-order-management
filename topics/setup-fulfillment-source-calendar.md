---
author: anvenkat
description: This article explains how to set up working calendar and assign to a fulfillment source in Microsoft Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 04/03/2023
ms.topic: overview
ms.author: anvenkat

title: setup fulfillment source calendar  

---

# Set up of the calendar

This article explains how to set up working calendar and assign to a fulfillment source in Microsoft Dynamics 365 Intelligent Order Management.

Business can set up working calendars for their stores or warehouses and assign to them in fulfillment source settings. Calendars are used to describe working, non-working hours, and time off information. 

To set up calendar, follow these steps.

1. Go to **Fulfillment settings** > **Holiday Calendar** > **Manage**.
1. On the **Quick create** page, enter the **Name** of the calendar, a **Description**, and select **Save and close**. You'll see a Calendar displayed with default working hours.
1. Select **+New**, and then **Working hours** to add the actual working hours.
1. On the page, select the calendar start date. For example, 01/01/2023, and select **Custom**.
1. Select **Choose an end date**, and select the end date of the calendar year. For example, 12/31/2023.
1. Deselect any non-working days.
1. You can no select the working hours by going into each day and changing the **start time** and **end time** and select **Apply**.

> [!Note]
> The time zone of the calendar needs to be selected based on the fulfillment source time zone it will be linked to. 

## Set up non-working hours or holidays

To set up holidays or non-working hours, follow these steps.

1. Select **+New**, and then **Non-Working**.
1. Select the date and the **Reason** for holiday.
1. Select the **Start time** and **End time**.

> [!Note}
> The default time zone is the user's current time zone.

## Assignment of Calendar to Fulfillment source

To assign a calendar to fulfillment source, follow these steps.

1. Go to **Settings** > **Fulfillment Settings** > **Sources** > **Manage**.
1. Select a **Source**.
1. Select a value in **Working Calendar** lookup under **Schedule**.

## Usage of Calendar for Fulfillment Optimization

In Intelligent Order Management, a **Working Calendar** is used by the Fulfillment optimization API when the **Respect warehouse timings** constraint is enabled.
If this constraint is enabled, the **Working Calendar** of the fulfillment source is checked to see if the source is working. If the fulfillment source isn't working, it is filtered out from the selection, and the orders are routed to a working source.

## Usage of Calendar for carrier pickup time determination

Carrier APIs, such as FedEx, need an accurate date and time of pickup to accurately calculate the estimated delivery date. The **Working calendar** is used by the Fulfillment optimization API to check if the date and time is within the working hours for a fulfillment source. If the date and time is outside of the working hours, the next available working day is checked.  
