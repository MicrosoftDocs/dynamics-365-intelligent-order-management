---
author: josaw1
description: This topic describes the Power BI dashboards that are available in Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 06/15/2021
ms.topic: conceptual
ms.author: josaw

title: Power BI dashboards in Intelligent Order Management
---


# Power BI dashboards in Intelligent Order Management

[!include [banner](includes/banner.md)]


Dynamics 365 Intelligent Order Management includes a set of dashboards embedded into the user interface that are based on Microsoft Power BI technology. The Power BI dashboards provide longer-range insights into the order and fulfillment data that is moving through the app.

The Intelligent Order Management license allows you to view your data in the Power BI-based dashboards, so you don't have to obtain additional licenses to view the dashboards.

> [!NOTE]
> There's a known issue with trial environments. Deploying embedded Power BI is currently not supported.

## Integration to Power BI

Integration between Power BI and Intelligent Order Management is preconfigured and doesn't require additional setup.

## Architecture

The Power BI dashboards use the architecture modeled in the following diagram.

1.  When data is entered in Intelligent Order Management, it's created or updated in Microsoft Dataverse.

2.  The Dataverse data is synchronized to the Dataverse-managed data lake using Athena. Synchronization is executed every 4 hours. The synchronization timing can't be modified.

3.  A data snapshot is copied and transferred to the analytics platform storage account.

4.  The data is transformed for Power BI KPIs.

5.  The transformed data is copied and transferred back to Dataverse-managed data lake.

6.  The Power BI workspace is provisioned or refreshed.

7.  The Power BI reports and pages are embedded in Intelligent Order Management.

![architecture flow.](media/architecture-flow.png)

## Customizations

Customization of dashboards based on embedded Power BI isn't supported. 

The data stored in managed data lake isn't accessible for any customizations. If custom reports or insights are required, you can build them by accessing data stored in Dataverse.
