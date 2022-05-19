---
author: sumanic
description: This topic provides information about how to set up the Uber Freight provider in Dynamics 365 Intelligent Order Management.
ms.date: 05/19/2022
ms.topic: how-to
ms.author: sumanic

title: Set up Uber Freight provider

---

# Set up Uber Freight provider

[!include [banner](includes/banner.md)]


This topic provides information about how to set up the Uber Freight provider in Dynamics 365 Intelligent Order Management.

 Uber Freight is a division of Uber created to focus on trucking freight across North America. It connects independent drivers with shippers who need their cargo transported from one location to another.  

For more information about Uber Freight, see the [Uber Freight website](https://www.uber.com/us/en/freight/coronavirus/). 

## Prerequisites 

As a prerequisite to this one would need to have a Uber account and follow the steps [here.](https://developer.uber.com/docs/freight/guides/authentication)

## Set up the provider
To set up the provider, follow these steps: 

1.  In Intelligent Order Management, go to **Providers > Catalog**.

2.  Select **Add Provider** on the **Uber Freight** tile.

3.  Select **Create** on the **Terms and Conditions** page.

4.  There are two connections that you need to set up in the **Connections** section.

    1. Uber Freight Dataverse (current environment) Connection

    1. Uber Freight Connection:

        1. Click on the connection.

        1. Under Connection section click on **Create**

        1. Enter the **Connection Name**, **API Key**, **Store Host URL**.

        1. Click on **Save** and then click on **Activate**.
        
        1. Click on **Save and Close**.

5. Go to the **Parameters** tab in  Overview and add the **Uber Freight customer id**.

6. Select **Save**.

7. Select **Activate** to activate the provider.

8. Select **Save and close**.

9. Go to **Providers > Installed** and validate that the provider you set up is listed with the status **Activated**.

## Out-of-box capabilities

The Uber Freight provider has the following capabilities:

|  Capability | Details |
| ------------------ | -------------------------------- |
| Transformation  |  **Dataverse Fulfillment Order to Uber Freight Quote**: Transforms a Fulfillment Order from Dataverse to Uber Freight to generate Quote.|
|                 |  **Dataverse Fulfillment Order to Uber Freight Tender**: Transforms a Fulfillment Order from Dataverse to Uber Freight to generate a Shipment Booking.|

## Additional resources

- [BigCommerce API documentation](https://developer.bigcommerce.com/api-docs) – Learn more about BigCommerce's API.
- [Run sample order orchestration flow from BigCommerce](run-sample-order-bigcommerce.md)
