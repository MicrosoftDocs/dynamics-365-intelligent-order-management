---
author: sumanic
description: This topic describes how to set up the Inventory Visibility provider in Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 05/24/2022
ms.topic: how-to
ms.author: sumanic

title: Set up Inventory Visibility

---

# Set up Inventory Visibility provider

[!include [banner](includes/banner.md)]

This topic describes how to set up the Inventory Visibility provider in Dynamics 365 Intelligent Order Management.

The Inventory Visibility Add-in (also referred to as the Inventory Visibility service) provides an independent and highly scalable microservice that enables real-time, on-hand inventory change postings and visibility tracking across all your data sources and channels.  
  
To learn more about the Inventory Visibility service, see [Inventory Visibility Add In](/dynamics365/supply-chain/inventory/inventory-visibility). 

## Prerequisites

The Inventory Visibility Add-in is a first-party, out-of-the-box service that will be available as part of Dynamics 365 Intelligent Order Management. In order to add this provider for use in orchestration, below are some key configurations to validate and update post installation.

1. Go to **Inventory Visibility \> Index And Reservations site map area**.
1. Confirm that the following tabs appear on the page:
    - Product Index Hierarchy
    - Data Source
    - Calculated measure
    - Soft Reservation Mapping
    - Soft Reservation Hierarchy
    - Feature Management
1. On the **Product Index Hierarchy** tab, confirm that the following:
    - A grid with the title **Set Product Index Hierarchy** appears
    - A **New Index Set** button appears
    - Grid has the following columns:
        - Set Number
        - Dimension
        - Hierarchy
        - Settings button image
1. On **Data Source** tab, confirm the following:
    - Title: Set Data Source
    - New Data Source button appears
1. Confirm that the following controls appear:
    - Datasource - IV
    - Datasource - FNO
    - Datasource - IOM
    - Datasource - SAP
    - Datasource - POS
1. Expand **DataSource - IOM** and confirm the following:
    Under Dimension Mappings
    - Add button appears. 
    - Under Physical Measures, confirm the following:
       - Measure Name
       - Modified On.
       - Sample Data: Onhand, some datetime     
1. On **Calculated Measure** tab, confirm the following:
    - Set Calculated Measures tab
    - New Calculated Measure button
1. Go to **Feature Management** and enable **OnHandReservation**.
1. Go to **Soft Reservation Hierarchy** and confirm that the grid has the following columns:
    - Dimensions
    - Hierarchy
    - Settings Button
1. Go to **Soft Reservation Mapping** and confirm that the grid has the following columns:
   - Physical Measure Data source
   - Physical Measure
   - Available For Reservation Data Source
   - Available For Reservation Calculated Measure
   - Settings Button

Once validated, the settings above configure or reuse the physical and calculated measures across your Datasources.

> [!NOTE]
> The below Inventory Visibility Provider can be used to connect to Inventory service available as part of Intelligent Order management as well a Dynamics 365 FinOps Inventory visibility instance to soft reserve or update inventory on Shipment or Receipt at Returns.
However the upload capability using blob storage is exclusive to Intelligent Order Management and can be leveraged to upload only at IOM Inventory service instance.

## Set up the Inventory Visibility provider

To set up the provider, follow these steps: 

1.  In Intelligent Order Management, go to **Providers \> Catalog**.
1.  Select **Add Provider** on the **Dynamics 365 Inventory Visibility** tile.
1.  Select **Create** on the **Terms and Conditions** page.
1.  There are two connections that you need to set up in the **Connections** section.
    1. Inventory Visibility Dataverse (current environment) Connection.
    1. Blob storage connection:
        1. Select the connection.
        1. Select **Create**. The Azure Blob storage connection will be automatically included.        
        1. Select **Save**, and then select **Activate**.
1. Go to the **Parameters** tab and enter the following non-mandatory parameters:
    - **Damaged Physical Measure**: The same physical measure name that you have defined in the setup for Damage.
    - **Data Source Name**: The Datasource that you have defined above as per your Inventory setup. Please note at this point only one Datasource function is supported.
    - **Inventory Visibility Error File Drop Location**: The path to the location where the Inventory Error log will be dropped for an upload failure.
    - **Inventory Visibility File Drop Location**: The path where the file will be dropped in Azure Blob Storage to be read and uploaded to the Inventory Visibility service.
    - **Inventory Visibility Organization ID**: The Intelligent Order Management organization ID.
    - **Physical Available Measure**:  The same physical measure name that you have defined in above setup for available stock.
    - **Restock Physical Measure**: The same physical measure name that you have defined in above setup for restock quantity.
    - **Returned Physical Measure**: The same physical measure name that you have defined in above setup for returned quantity.
    - **Soft Reserved Physical Measure**: The same physical measure name that you have defined in above setup for reservation quantity.
    - **Scrapped Physical Measure**: The same physical measure name that you have defined in above setup for scrapped quantity.
1. Select **Save**, and then select **Activate** to activate the provider.

*Provider actions* are actions associated with a provider that determine what actions are available to you when you create an orchestration flow.

Provider *transformations* are essential to any provider that retrieves or sends data from Intelligent Order Management to an external service.

|  Capability | Details |
| ------------------ | -------------------------------- |
|**Provider action**  | **Bulk or Delta Inventory Upload** : Part of inventory orchestration   | 
| **Provider action** |**Inventory Update on Receipt** : Part of order orchestration| 
| **Provider action** |**Inventory Update on Shipment** : Part of order orchestration| 
|  **Provider action** |**Soft Reserve Inventory** : Part of order orchestration|
| **Transformation**  |**Dataverse Inventory Onhand Data to Inventory Visibility Onhand Changes**|

## Additional resources

[Setting up Inventory Service in Dynamics 365 FinOps](/dynamics365/supply-chain/inventory/inventory-visibility-setup#inventory-visibility-prerequisites)
