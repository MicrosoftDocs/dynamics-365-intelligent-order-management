---
author: sumanic
description: This topic provides information about how to set up the Uber Freight provider in Dynamics 365 Intelligent Order Management.
ms.date: 05/24/2022
ms.topic: how-to
ms.author: sumanic

title: Set up Uber Freight provider

---

# Set up Uber Freight provider

[!include [banner](includes/banner.md)]

This topic describes how to set up the Uber Freight provider in Dynamics 365 Intelligent Order Management.

Uber Freight is a division of Uber created to focus on trucking freight across North America. It connects independent drivers with shippers who need their cargo transported from one location to another.  

For more information about Uber Freight, see the [Uber Freight website](https://www.uber.com/us/en/freight/coronavirus/). 

## Prerequisites 

To set up the Uber Freight provider, you must first have an Uber Freight development account and be onboarded to the [Uber Developer Platform](https://developer.uber.com/docs/freight/guides/authentication).

## Set up the provider

To set up the provider, follow these steps: 

1.  In Intelligent Order Management, go to **Providers \> Catalog**.
2.  Select **Add Provider** on the **Uber Freight** tile.
3.  Select **Create** on the **Terms and Conditions** page.
4.  There are two connections that you need to set up in the **Connections** section.
    1. Uber Freight Dataverse (current environment) Connection
    1. Uber Freight Connection:
        1. Select the connection.
        1. Under the **Connection** section, select **Create**.
        1. Enter the **Connection Name**, **API Key**, and **Store Host URL**.
        1. Select **Save**, and then Select **Activate**.       
        1. Select **Save and close**.
5. On the **Overview \> Parameters**, enter the **Uber Freight customer id**.
6. Select **Save**.
7. Select **Activate** to activate the provider.
8. Select **Save and close**.
9. Go to **Providers \> Installed** and validate that the provider you set up is listed with the status **Activated**.

## Out-of-box capabilities

The Uber Freight provider has the following capabilities:

|  Capability | Details |
| ------------------ | -------------------------------- |
| Transformation  |  **Dataverse Fulfillment Order to Uber Freight Quote**: Transforms a fulfillment order from Dataverse to Uber Freight to generate a quote.|
| Transformation  |  **Dataverse Fulfillment Order to Uber Freight Tender**: Transforms a fulfillment order from Dataverse to Uber Freight to generate a shipment booking.|

## Additional resources

[Uber Freight API documentation](https://developer.uber.com/docs/freight/introduction)](https://developer.uber.com/docs/freight/introduction))
