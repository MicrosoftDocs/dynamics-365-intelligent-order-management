---
author: sumanic
description: This topic describes how to set up the Inventory Visibility  provider in Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 05/19/2022
ms.topic: how-to
ms.author: sumanic

title: Set up Inventory Visibility

---

# Set up Inventory Visibility provider

[!include [banner](includes/banner.md)]


This topic describes how to set up the Inventory Visibility provider in Dynamics 365 Intelligent Order Management.

The Inventory Visibility Add-in (also referred to as the Inventory Visibility service) provides an independent and highly scalable microservice that enables real-time on-hand inventory change postings and visibility tracking across all your data sources and channels.  
  
To learn more about Inventory Visibility service, see [Inventory Visibility Add In](https://docs.microsoft.com/en-us/dynamics365/supply-chain/inventory/inventory-visibility). 

## Prerequisites

Inventory Visibilty add in is a first party out of the box addin that will be available as part of Intelligent Order Management product.
In order to add this provider for use in orchestration below are some key configurations to validate and update post installation.

1. Navigate to Inventory Visibility -> **Index And Reservations site map area**
1. Assert if the following tabs appear on the page:
    1. Product Index Hierarchy
    2. Data Source
    3. Calculated measure
    4. Soft Reservation Mapping
    5. Soft Reservation Hierarchy
    6. Feature Management
1. On the **Product Index Hierarchy** tab, assert the following:
    1. A grid with the title Set Product Index Hierarchy appears
    2. A New Index Set button appears
    3. Grid has the following columns
        1. Set Number
        2. Dimension
        3. Hierarchy
        4. Settings button image
1. On **Data Source** tab, assert the following:
    1. Title: Set Data Source
    2. New Data Source button appears
1. Below controls appear
    1. Datasource - IV
    2. Datasource - FNO
    3. Datasource - IOM
    4. Datasource - SAP
    5. Datasource - POS
1. In this expand **DataSource - IOM** and assert the following:
    Under Dimension Mappings
    1. Add button appears. 
    2. Under Physical Measures you find the following:
       1. Measure Name
       2. Modified on.

        **Sample Data:**
        Onhand, some datetime
       
1. On **Calculated Measure** tab, assert the following:
    1. Set Calculated Measures tab
    2. New Calculated Measure button appears

1. Goto **Feature Management**. Enable OnHandReservation

1. Goto **Soft Reservation Hierarchy**. The grid has the following columns:
    1. Dimensions
    2. Hierarchy
    3. Seetings Button

1. Goto **Soft Reservation Mapping**. The grid has the following columns:
   1. Physical Measure Data source
   2. Physical Measure
   3. Available For Reservation Data Source
   4. Available For Reservation Calculated Measure
   5. Settings Button

Once validated the above settings, configure or reuse the physical measures and calculated measure across your Datasources.

Note: The below Inventory Visibility Provider can be used to connect to Inventory service available as part of Intelligent Order management as well a Dynamics 365 FinOps Inventory visibility instance to soft reserve or update inventory on Shipment or Receipt at Returns.
However the upload capability using blob storage is exclusive to Intelligent Order Management and can be leveraged to upload only at IOM Inventory service instance.

## Set up Inventory Visibility Provider

To set up the provider, follow these steps: 

1.  In Intelligent Order Management, go to **Providers > Catalog**.

2.  Select **Add Provider** on the **Dynamics 365 Inventory Visibility** tile.

3.  Select **Create** on the **Terms and Conditions** page.

4.  There are two connections that you need to set up in the **Connections** section.

    1. Inventory Visibilty Dataverse (current environment) Connection

    1. Blob storage connection:

        1. Select the connection.

        1. Click on the Create link.

        1. It will automatically includ the Azure Blob storage connection.
        
        1. Click **Save** and then **Activate**.

    1. Go to the **Parameters** tab and add the below **non-mandatory** parameters:

        1. **Damaged Physical Measure** : Please enter the same physical measure name that you have defined in above setup for Damage.
        2. **Data Souce Name** : The Datasource that you have defined above as per your Inventory setup. Please note at this point only one Datasource function is supported.
        3. **Inventory Visibility Error File Drop Location** : This will be the path to the location where the Inventory Error log will be dropped for an upload failure.
        4. **Inventory Visibility File Drop Location** : This will be the path where the file will be dropped in Blob storage to be read and uploaded to Inventory visibility service.
        5. **Inventory Visibility Organization ID** : This will be the Intelligent Order Management org id.
        6. **Physical Available Measure** :  Please enter the same physical measure name that you have defined in above setup for available stock.
        7. **Restock Physical Measure** : Please enter the same physical measure name that you have defined in above setup for restock quantity.
        8. **Returned Physical Measure** : Please enter the same physical measure name that you have defined in above setup for returned quantity.
        9. **Soft Reserved Physical Measure** : Please enter the same physical measure name that you have defined in above setup for reservation quantity.
        10. **Scrapped Physical Measure**: Please enter the same physical measure name that you have defined in above setup for scrapped quantity.


|  Capability | Details |
| ------------------ | -------------------------------- |
|    Provider actions       |The actions associated with a provider that determine what actions are available to you when you create an orchestration flow.   | 
|                           |**Bulk or Delta Inventory Upload** : Part of Inventory Orchestration| 
|                           |**Inventory Update on Receipt** : Part of Order Orchestration| 
|                           |**Inventory Update on Shipment** : Part of Order Orchestration| 
|                           |**Soft Reserve Inventory** : Part of Order Orchestration|
|    Transformations        |Provider transformations are essential to any provider that retrieves or sends data from Intelligent Order Management to an external service. |
|                           |**Dataverse Inventory Onhand Data to Inventory Visibility Onhand Changes**|

## Additional resources

[Setting up Inventory Service in Dynamics 365 FinOps](https://docs.microsoft.com/en-us/dynamics365/supply-chain/inventory/inventory-visibility-setup#inventory-visibility-prerequisites)
