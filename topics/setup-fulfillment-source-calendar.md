---
author: Anusha Venkatesan
description: This article describles how to set up working calendar and assign to a fulfillment source in Microsoft Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 04/03/2023
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

Please note that the time zone of the calendar needs to be selected based on the fulfillment source time zone it will be linked to. 

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
If this Constraint is enabled **Working Calendar** of the fulfillment source will be checked to see if the source is working and if the source is not working, it will be filtered out from the selection so orders can be routed to the working stores instead.

## Usage of Calendar for carrier pick up time determination

Carrier API's such as FedEx need an accurate date and time of pick up to be able to accurately calculate the Estimated delivery dates. **Working calendar**  is checked by the Fulfillment optimization API if the current date and time is within working hours for a fulfillment source. If its outside of the working hours, the next working day is selected based on the **Working calendar** to look for the carrier pick up times available for that day.  
