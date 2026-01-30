---
title: Power BI reports aren't provisioned in the trial version
author: josaw1
description: Learn about a solution for cases where Microsoft Power BI reports for Dynamics 365 Intelligent Order Management aren't provisioned.
ms.date: 01/28/2026
ms.custom: 
  - bap-template
ms.topic: concept-article
ms.author: anvenkat
---

# Power BI reports aren't provisioned in the trial version

[!include [banner](includes/banner.md)]

In the August 2021 release of Microsoft Dynamics 365 Intelligent Order Management (version 1.0.03429), the Fulfillment Source table isn't automatically enabled for change tracking. This issue causes the Power BI reports to show the following message for an indefinite period:

> Your reports are being provisioned. Please allow up to 24 hours for the process to complete.

To fix this problem, follow these steps. This procedure reenables the Fulfillment Source table to sync and provision the Power BI reports.

1. Disable the Power BI Insights setting:

    1. Open Intelligent Order Management.
    1. Switch to the **Configurations** site map in the lower corner of the app.
    1. Under **Dashboard Settings**, select **Power BI Insights**.
    1. Select **Manage**.
    1. Under **Summary**, set the **Status** option to **Disabled**.
    1. Select **Save**.

1. Enable change tracking for the Fulfillment Source table:

    1. Open the [Power Apps maker portal](https://make.powerapps.com/).
    1. In the upper-right corner, select the correct environment.
    1. In the left pane, under **Data**, select **Tables**.
    1. Under the environment name, change the filter criterion from **Default** to **All**.
    1. In the search field, enter **msdyn\_fulfillmentsource**.
    1. Select the table name to go to the table details.
    1. Select **Settings**.
    1. In the **Edit table** dialog box, expand **More settings**.
    1. Expand **Create and update settings**.
    1. Select the **Enable change tracking** checkbox.
    1. Select **Done**.
    1. Select **Save Table**.

1. Synchronization of the table data should automatically begin. Wait at least an hour for the table to be fully processed.
1. When the table data syncs, enable the Power BI Insights setting:

    1. Open Intelligent Order Management.
    1. Switch to the **Configurations** site map in the lower corner of the app.
    1. Under **Dashboard Settings**, select **Power BI Insights**.
    1. Select **Manage**.
    1. Under **Summary**, set the **Status** option to **Enabled**.
    1. Select **Save**.

1. Verify that the Power BI reports are rendered. The reports should be provisioned and appear within 15 minutes.
