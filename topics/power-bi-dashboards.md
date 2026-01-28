---
author: josaw1
description: This topic describes the Power BI dashboards that are available in Dynamics 365 Intelligent Order Management.
ms.date: 01/28/2026
ms.custom: 
  - bap-template
ms.topic: how-to
ms.author: anvenkat
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

1. When data is entered in Intelligent Order Management, it's created or updated in Microsoft Dataverse.

1. The Dataverse data is synchronized to the Dataverse-managed data lake using Athena. Synchronization is executed every 4 hours. The synchronization timing can't be modified.

1. A data snapshot is copied and transferred to the analytics platform storage account.

1. The data is transformed for Power BI KPIs.

1. The transformed data is copied and transferred back to Dataverse-managed data lake.

1. The Power BI workspace is provisioned or refreshed.

1. The Power BI reports and pages are embedded in Intelligent Order Management.

:::image type="content" source="media/architecture-flow.png" alt-text="Screenshot of the architecture flow diagram for Power BI dashboards.":::

## Customizations

Customization of dashboards based on embedded Power BI isn't supported.

The data stored in managed data lake isn't accessible for any customizations. If custom reports or insights are required, you can build them by accessing data stored in Dataverse.
