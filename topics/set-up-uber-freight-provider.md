---
author: sumanic
description: This topic describes how to set up the Uber Freight provider in Microsoft Dynamics 365 Intelligent Order Management.
ms.date: 05/25/2022
ms.topic: how-to
ms.author: sumanic

title: Set up the Uber Freight provider

---

# Set up the Uber Freight provider

[!include [banner](includes/banner.md)]

This topic describes how to set up the Uber Freight provider in Microsoft Dynamics 365 Intelligent Order Management.

Uber Freight is a division of Uber that was created to focus on trucking freight across North America. It connects independent drivers with shippers who must have their cargo transported from one location to another.

For more information about Uber Freight, see the [Uber Freight website](https://www.uber.com/us/en/freight/coronavirus/).

## Prerequisites 

To set up the Uber Freight provider, you must have an Uber Freight development account and must be onboarded to the [Uber Developer Platform](https://developer.uber.com/docs/freight/guides/authentication).

## Set up the provider

To set up the provider, follow these steps.

1. In Intelligent Order Management, go to **Providers \> Catalog**.
2. On the **Uber Freight** tile, select **Add Provider**.
3. On the **Terms and Conditions** page, select **Create**.
4. In the **Connections** section, you must set up two connections:

    - Uber Freight Dataverse (current environment) connection
    - Uber Freight connection

    For each connection, follow these steps:

    1. Select the connection.
    1. In the **Connection** section, select **Create**.
    1. Set the **Connection Name**, **API Key**, and **Store Host URL** fields.
    1. Select **Save**, and then select **Activate**.
    1. Select **Save and close**.

5. On the **Parameters** tab, set the **Uber Freight customer ID** field.
6. Select **Save**.
7. Select **Activate** to activate the provider.
8. Select **Save and close**.
9. Go to **Providers \> Installed**, and validate that the provider is listed and has a status of **Activated**.

## Out-of-box capabilities

The Uber Freight provider has the following capabilities.

| Capability | Details |
| ---------- | ------- |
| Transformation | **Dataverse Fulfillment Order to Uber Freight Quote:** Transform a fulfillment order from Dataverse to Uber Freight to generate a quote. |
| Transformation | **Dataverse Fulfillment Order to Uber Freight Tender:** Transform a fulfillment order from Dataverse to Uber Freight to generate a shipment booking. |

## Additional resources

[Uber Freight application programming interface (API) documentation](https://developer.uber.com/docs/freight/introduction)
