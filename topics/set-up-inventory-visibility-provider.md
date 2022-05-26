---
author: sumanic
description: This topic describes how to set up the Inventory Visibility provider in Microsoft Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 05/25/2022
ms.topic: how-to
ms.author: sumanic
title: Set up Inventory Visibility provider

---

# Set up Inventory Visibility provider

[!include [banner](includes/banner.md)]

This topic describes how to set up the Inventory Visibility provider in Microsoft Dynamics 365 Intelligent Order Management.

The Inventory Visibility Add-in (also referred to as the Inventory Visibility service) provides an independent and highly scalable microservice that enables real-time on-hand inventory change postings and visibility tracking across all your data sources and channels.

For more information about the Inventory Visibility service, see [Inventory Visibility Add In](/dynamics365/supply-chain/inventory/inventory-visibility).

## Prerequisites

The Inventory Visibility Add-in is a first-party, out-of-box service that will be available as part of Intelligent Order Management. To add this provider so that it can be used in orchestration, you must validate and update the following configurations after you install the add-in.

1. Go to **Inventory Visibility \> Index And Reservations** site map area.
1. Confirm that the following tabs appear on the page:

    - Product Index Hierarchy
    - Data Source
    - Calculated Measure
    - Soft Reservation Mapping
    - Soft Reservation Hierarchy
    - Feature Management

1. On the **Product Index Hierarchy** tab, confirm that the following elements appear:

    - A grid that has the title **Set Product Index Hierarchy**
    - A **New Index Set** button
    - A grid that has the following columns:

        - Set Number
        - Dimension
        - Hierarchy
        - Settings Button Image

1. On the **Data Source** tab, confirm that the following elements appear:

    - **Set Data Source** title
    - **New Data Source** button

1. Confirm that the following controls appear:

    - Datasource - IV
    - Datasource - FNO
    - Datasource - IOM
    - Datasource - SAP
    - Datasource - POS

1. Expand the **DataSource - IOM** control, and confirm that the following elements appear:

    - Under **Dimension Mappings**:

        - **Add** button

    - Under **Physical Measures**:

        - Measure Name
        - Modified On
        - Sample Data

1. On the **Calculated Measure** tab, confirm that the following elements appear:

    - **Set Calculated Measures** tab
    - **New Calculated Measure** button

1. Go to **Feature Management**, and enable the **OnHandReservation** feature.
1. Go to **Soft Reservation Hierarchy**, and confirm that the grid has the following elements:

    - **Dimensions** column
    - **Hierarchy** column
    - **Settings** button

1. Go to **Soft Reservation Mapping**, and confirm that the grid has the following elements:

    - **Physical Measure Data Source** column
    - **Physical Measure** column
    - **Available For Reservation Data Source** column
    - **Available For Reservation Calculated Measure** column
    - **Settings** button

After you've completed the preceding validation, the settings configure or reuse the physical and calculated measures across your data sources.

## Set up the Inventory Visibility provider

> [!NOTE]
> - The Inventory Visibility provider can be used to connect both to the inventory service that is available as part of Intelligent Order Management and to a Dynamics 365 Finance + Operations Inventory Visibility instance to soft reserve or update inventory upon shipment or receipt at returns.
> - The upload capability that uses Azure Blob Storage is exclusive to Intelligent Order Management and can be used only to upload an instance of the Intelligent Order Management Inventory service.

To set up the provider, follow these steps.

1. In Intelligent Order Management, go to **Providers \> Catalog**.
1. On the **Dynamics 365 Inventory Visibility** tile, select **Add Provider**.
1. On the **Terms and Conditions** page, select **Create**.
1. In the **Connections** section, you must set up two connections:

    - Inventory Visibility Dataverse (current environment) connection
    - Blob storage connection

    For each connection, follow these steps:

    1. Select the connection.
    1. Select **Create**. The Blob Storage connection will automatically be included.
    1. Select **Save**, and then select **Activate**.

1. On the **Parameters** tab, set the following non-mandatory parameters:

    - **Damaged Physical Measure** – Specify the same physical measure name that you defined for damage during setup.
    - **Data Source Name** – Specify the data source that you defined during setup. Currently, only one data source function is supported.
    - **Inventory Visibility Error File Drop Location** – Specify the path of the location where the inventory error log should be saved after an upload failure.
    - **Inventory Visibility File Drop Location** – Specify the path in Blob Storage where the Inventory Visibility file should be saved so that it can be read by and uploaded to the Inventory Visibility service.
    - **Inventory Visibility Organization ID** – Specify the Intelligent Order Management organization ID.
    - **Physical Available Measure** – Specify the same physical measure name that you defined for available stock during setup.
    - **Restock Physical Measure** – Specify the same physical measure name that you defined for restock quantity during setup.
    - **Returned Physical Measure** – Specify the same physical measure name for returned quantity that you defined during setup.
    - **Soft Reserved Physical Measure** – Specify the same physical measure name for reservation quantity that you defined during setup.
    - **Scrapped Physical Measure** – Specify the same physical measure name for scrapped quantity that you defined during setup.

1. Select **Save**, and then select **Activate** to activate the provider.

## Out-of-box capabilities

*Provider actions* are associated with a provider and determine the actions that are available to you when you create an orchestration flow. *Transformations* are essential for any provider that retrieves or sends data from Intelligent Order Management to an external service.

| Capability | Details |
| ---------- | ------- |
| Provider action | **Bulk or Delta Inventory Upload:** Part of inventory orchestration |
| Provider action | **Inventory Update on Receipt:** Part of order orchestration |
| Provider action | **Inventory Update on Shipment:** Part of order orchestration |
| Provider action | **Soft Reserve Inventory:** Part of order orchestration |
| Transformation | **Dataverse Inventory Onhand Data to Inventory Visibility Onhand Changes** |

## Additional resources

[Inventory Visibility prerequisites](/dynamics365/supply-chain/inventory/inventory-visibility-setup#inventory-visibility-prerequisites)
