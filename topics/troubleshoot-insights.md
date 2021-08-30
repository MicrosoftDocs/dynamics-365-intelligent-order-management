---
author: josaw1
description: This troubleshooting topic provides a solution for cases where Power BI reports for Dynamics 365 Intelligent Order Management don't provision.
ms.service: dynamics-365-intelligent-order-management
ms.date: 09/01/2021
ms.topic: troubleshooting
ms.author: josaw
ms.custom: 
title: Power BI reports don't provision in trial version
---


# Power BI reports don't provision in trial version

[!include [banner](includes/banner.md)]

In the August 2021 release of Dynamics 365 Intelligent Order Management (version 1.0.03429), the fulfillment source table isn't automatically enabled for change tracking. This issue causes the Microsoft Power BI reports to display "Your reports are being provisioned. Please allow up to 24 hours for the process to complete." for an indefinite period. 

To resolve this issue, complete the following steps. This procedure will reenable the fulfillment source table to sync and provision the Power BI reports.

1.  Disable the Power BI Insights setting.

    1.  Open Intelligent Order Management.

    2.  Switch to the 'Configurations' site map in the lower corner of the application <!-- which corner? is this a button? rewrite this step -->

    3.  Select **Power BI Insights** under **Dashboard Settings**.

    4.  Select **Manage**.

    5.  Under **Summary**,set the **Status** toggle to **Disabled**.

    6.  Select **Save**.

2.  Enable Change Tracking for the Fulfillment Source table

    1.  Go to the Power Apps maker portal

        1.  make.powerapps.com

    2.  Select the correct environment in the upper right hand corner

    3.  Select 'Tables' under 'Data' in the left side pane

    4.  Under the environment name, change the filter from 'Default' to 'All'

    5.  Search for table 'msdyn\_fulfillmentsource'

    6.  Click the table name to go to the table details

    7.  Click on 'Settings'

    8.  Expand 'More Settings' in the flight out window on the right

    9.  Expand 'Create and update settings'

    10. Click the check box so 'Enable change tracking' is selected

    11. Click Done

    12. Click Save Table

3.  Wait for data to sync

    1.  The table data should automatically start syncing, but please wait at least an hour for the table to be properly processed

4.  Enable the Power BI Insights setting

    1.  Open the Intelligent Order Management Application

    2.  Switch to the 'Configurations' site map in the lower corner of the application

    3.  Select 'Power BI Insights' under 'Dashboard Settings'

    4.  Click Manage

    5.  Toggle the button into the Enabled State

    6.  Click Save

5.  Verify Power BI reports render

    1.  The Power BI reports should be provisioned and appear within 15 mins
