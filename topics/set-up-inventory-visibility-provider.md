---
author: sumanic
description: This topic describes how to set up the Inventory Visibility provider in Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 05/25/2022
ms.topic: how-to
ms.author: sumanic
title: Set up Inventory Visibility provider

---

# Set up Inventory Visibility provider

[!include [banner](includes/banner.md)]

This topic describes how to set up the Inventory Visibility provider in Dynamics 365 Intelligent Order Management.

The Inventory Visibility Add-in (also referred to as the Inventory Visibility service) provides an independent and highly scalable microservice that enables real-time, on-hand inventory change postings and visibility tracking across all your data sources and channels.  
  
To learn more about the Inventory Visibility service, see [Inventory Visibility Add In](/dynamics365/supply-chain/inventory/inventory-visibility). 

## Prerequisites

The Inventory Visibility Add-in is a first-party, out-of-the-box service that will be available as part of Dynamics 365 Intelligent Order Management. In order to add this provider for use in orchestration, after installing the add-in, you must validate and update the following configurations.

1. Go to **Inventory Visibility \> Index And Reservations site map area**.
1. Confirm that the following tabs appear on the page:
    - Product Index Hierarchy
    - Data Source
    - Calculated Measure
    - Soft Reservation Mapping
    - Soft Reservation Hierarchy
    - Feature Management
1. On the **Product Index Hierarchy** tab, confirm that the following elements appear:
    - A grid with the title **Set Product Index Hierarchy**.
    - A **New Index Set** button.
    - A grid with the following columns:
        - Set Number
        - Dimension
        - Hierarchy
        - Settings Button Image
1. On **Data Source** tab, confirm that the following elements appear:
    - **Set Data Source** title
    - **New Data Source** button
1. Confirm that the following controls appear:
    - **Datasource - IV**
    - **Datasource - FNO**
    - **Datasource - IOM**
    - **Datasource - SAP**
    - **Datasource - POS**
1. Expand **DataSource - IOM** and confirm that the following elements appear:
    - Under **Dimension Mappings**: 
        - **Add** button
    - Under **Physical Measures**:
        - **Measure Name**
        - **Modified On**
        - **Sample Data**
1. On the **Calculated Measure** tab, confirm that the following elements appear:
    - **Set Calculated Measures** tab.
    - **New Calculated Measure** button.
1. Go to **Feature Management** and enable **OnHandReservation**.
1. Go to **Soft Reservation Hierarchy** and confirm that the grid has the following:
    - **Dimensions** column
    - **Hierarchy** column
    - **Settings** button
1. Go to **Soft Reservation Mapping** and confirm that the grid has the following:
   - **Physical Measure Data Source** column
   - **Physical Measure** column
   - **Available For Reservation Data Source** column
   - **Available For Reservation Calculated Measure** column
   - **Settings** nutton

Once validated, the settings above configure or reuse the physical and calculated measures across your data sources.

## Set up the Inventory Visibility provider

> [!NOTE]
> - The Inventory Visibility provider can be used to connect to the inventory service available as part of Intelligent Order Management as well as to a Dynamics 365 Finance and Operations Inventory Visibility instance to soft reserve or update inventory upon shipment or receipt at returns. 
> - The upload capability using blob storage is exclusive to Intelligent Order Management and can only be used to upload an Intelligent Order Management Inventory service instance.

To set up the provider, follow these steps: 

1.  In Intelligent Order Management, go to **Providers \> Catalog**.
1.  Select **Add Provider** on the **Dynamics 365 Inventory Visibility** tile.
1.  Select **Create** on the **Terms and Conditions** page.
1.  There are two connections that you need to set up in the **Connections** section:
    1. Inventory Visibility Dataverse (current environment) connection
    1. Blob storage connection:
        1. Select the connection.
        1. Select **Create**. The Azure Blob storage connection will automatically be included.        
        1. Select **Save**, and then select **Activate**.
1. Go to the **Parameters** tab and enter the following non-mandatory parameters:
    - **Damaged Physical Measure**: The same physical measure name that you defined for damage during setup.
    - **Data Source Name**: The data source that you defined during setup. Currently only one data source function is supported.
    - **Inventory Visibility Error File Drop Location**: The path to the location where the inventory error log will be saved after an upload failure.
    - **Inventory Visibility File Drop Location**: The path in Azure Blob Storage where the Inventory Visibility file will be saved to be read by and uploaded to the Inventory Visibility service.
    - **Inventory Visibility Organization ID**: The Intelligent Order Management organization ID.
    - **Physical Available Measure**: The same physical measure name that you defined for available stock during setup.
    - **Restock Physical Measure**: The same physical measure name that you defined for restock quantity during setup.
    - **Returned Physical Measure**: The same physical measure name for returned quantity that you defined during setup.
    - **Soft Reserved Physical Measure**: The same physical measure name for reservation quantity that you defined during setup.
    - **Scrapped Physical Measure**: The same physical measure name for scrapped quantity that you defined during setup.
1. Select **Save**, and then select **Activate** to activate the provider.

## Out-of-box capabilities

*Provider actions* are actions associated with a provider that determine what actions are available to you when you create an orchestration flow.

Provider *transformations* are essential to any provider that retrieves or sends data from Intelligent Order Management to an external service.

|  Capability | Details |
| ------------------ | -------------------------------- |
|**Provider action**  | **Bulk or Delta Inventory Upload** : Part of inventory orchestration.   | 
| **Provider action** |**Inventory Update on Receipt** : Part of order orchestration.| 
| **Provider action** |**Inventory Update on Shipment** : Part of order orchestration.| 
|  **Provider action** |**Soft Reserve Inventory** : Part of order orchestration.|
| **Transformation**  |**Dataverse Inventory Onhand Data to Inventory Visibility Onhand Changes**|

## Additional resources

[Setting up Inventory Service in Dynamics 365 FinOps](/dynamics365/supply-chain/inventory/inventory-visibility-setup#inventory-visibility-prerequisites)
