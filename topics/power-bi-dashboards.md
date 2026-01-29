---
author: josaw1
description: Learn about the Power BI dashboards that are available in Dynamics 365 Intelligent Order Management.
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

The Intelligent Order Management license allows you to view your data in the Power BI-based dashboards, so you don't need to get extra licenses to view the dashboards.

> [!NOTE]
> There's a known problem with trial environments. Deploying embedded Power BI isn't currently supported.

## Integration to Power BI

Integration between Power BI and Intelligent Order Management is preconfigured and doesn't require additional setup.

## Architecture

The Power BI dashboards use the architecture modeled in the following diagram.

1. When you enter data in Intelligent Order Management, you create or update it in Microsoft Dataverse.

1. Athena synchronizes the Dataverse data to the Dataverse-managed data lake. Synchronization runs every four hours. You can't modify the synchronization timing.

1. The process copies and transfers a data snapshot to the analytics platform storage account.

1. The process transforms the data for Power BI KPIs.

1. The process copies and transfers the transformed data back to Dataverse-managed data lake.

1. The process provisions or refreshes the Power BI workspace.

1. The process embeds the Power BI reports and pages in Intelligent Order Management.

:::image type="content" source="media/architecture-flow.png" alt-text="Screenshot of the architecture flow diagram for Power BI dashboards.":::

## Customizations

You can't customize dashboards based on embedded Power BI.

You can't access data stored in the managed data lake for any customizations. If you need custom reports or insights, you can build them by accessing data stored in Dataverse.
