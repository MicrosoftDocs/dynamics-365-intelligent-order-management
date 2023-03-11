---
author: Anusha Venkatesan
description: This article describles how to set up working calendar and assign to a fulfillment source in Microsoft Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 03/10/2023
ms.topic: overview
ms.author: anvenkat

title: setup fulfillment source calendar  

---

# Set up of the calendar

Business can set up various working calendars for their stores or warehouses and assign to them in fulfillment source settings. Calendars are generally used to describe working , non working hours and time off
information. To set up calendar follow the steps below:
1. Go to **Fulfillment settings** > **Holiday Calendar** > **Manage**
2. In the **Quick create** form enter the **Name** of the calendar and **Description**, and select **Save and close**
3. You will see a Calendar displayed with default working hours.
4. You can then add the actual working hours by selecting **+New** and **Working hours**
5. On the form select start of the calendar start date example 01.01.2023 and select **Custom**
6. Select **Choose an end date** option below the days of the week and select the end date of the calendar year example 12.31.2023
7. You can unselect any non working days by simply selecting those days.
8. You can no select the working hours by going into each day and changing the **start time** and **end time** and select **Apply**

## Set up non working hours or holidays

1. To set up holidays or non working hours select **+New**, **Non Working**
2. Select the date and the **Reason** for holiday
3. Select **Start time** and **End time**
4. The default time zone will be in user's time zone.

## Assignment of Calendar to Fulfillment source

1. Go to **Settings** > **Fulfillment Settings** > **Sources** > **Manage**
2. Select a **Source**
3. Select a value in **Working Calendar** lookup under **Schedule**

## Usage of Calendar for Fulfillment Optimization

In Intelligent Order Management **Working Calendar** is used and referred in Fulfillment Optimization if the **Constraint** **Respect warehouse timings** is enabled.
If this Constraint is enabled **Working Calendar** of the fulfillment source will be checked to see if the source is working and prioritize routing of the orders to the fulfillment source that is working.

## Usage of Calendar for 
