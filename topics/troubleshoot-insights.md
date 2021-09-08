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

In the August 2021 release of Dynamics 365 Intelligent Order Management (version 1.0.03429), the fulfillment source table isn't automatically enabled for change tracking. This issue causes the Microsoft Power BI reports to display the following message for an indefinite period:

    "Your reports are being provisioned. Please allow up to 24 hours for the process to complete."  

To resolve this issue, complete the following steps. This procedure will reenable the fulfillment source table to sync and provision the Power BI reports.

1.  Disable the Power BI Insights setting:
    1. Open Intelligent Order Management.
    1. Switch to the **Configurations** site map in the lower corner of the application. <!-- which corner? is this a button? rewrite this step -->
    1. Select **Power BI Insights** under **Dashboard Settings**.
    1. Select **Manage**.
    1. Under **Summary**,set the **Status** toggle to **Disabled**.
    1. Select **Save**.
1.  Enable change tracking for the Fulfillment Source table.
    1. Go to the [Power Apps maker portal](https://make.powerapps.com/).
    1. Select the correct environment in the upper right corner.
    1. Under **Data** in the left pane, select **Tables**.
    1. Under the environment name, change the filter criteria from **Default** to **All**.
    1. Search for the "msdyn\_fulfillmentsource" table.
    1. Select the table name to go to the table details.
    1. Select **Settings**.
    1. Expand **More Settings** in the fly out window on the right.
    1. Expand **Create and update settings**.
    1. Select the **Enable change tracking** checkbox.
    1. Select **Done**.
    1 .Select **Save Table**.
1. Wait for the table data to sync. The table data should automatically start syncing, but you should wait at least an hour for the table to be fully processed.
1. Enable the Power BI Insights setting.
    1. Open the Intelligent Order Management.
    1. Switch to the **Configurations** site map in the lower corner of the application.
    1. Under **Dashboard Settings**, select **Power BI Insights**. 
    1. Select **Manage**.
    1. Set the toggle to **Enabled**.
    1. Select **Save**.
1. Verify that the Power BI reports render. The Power BI reports should be provisioned and appear within 15 minutes.
