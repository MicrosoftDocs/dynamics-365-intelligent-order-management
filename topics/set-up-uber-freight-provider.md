---
author: sumanic
description: Learn about how to set up the Uber Freight provider in Microsoft Dynamics 365 Intelligent Order Management.
ms.date: 01/28/2026
ms.custom: 
  - bap-template
ms.topic: how-to
ms.author: sumanic
title: Set up Uber Freight provider

---

# Set up Uber Freight provider

[!include [banner](includes/banner.md)]

This article describes how to set up the Uber Freight provider in Microsoft Dynamics 365 Intelligent Order Management.

Uber Freight is a division of Uber that focuses on trucking freight across North America. It connects independent drivers with shippers who need to transport their cargo from one location to another.

For more information about Uber Freight, see the [Uber Freight website](https://www.uber.com/us/en/freight/coronavirus/).

## Prerequisites

To set up the Uber Freight provider, you must have an Uber Freight development account and be onboarded to the [Uber Developer Platform](https://developer.uber.com/docs/freight/guides/authentication).

## Set up the provider

To set up the provider, follow these steps:

1. In Intelligent Order Management, go to **Providers \> Catalog**.
1. On the **Uber Freight** tile, select **Add Provider**.
1. On **Terms and Conditions**, select **Create**.
1. In the **Connections** section, set up two connections:

    - Uber Freight Dataverse (current environment) connection
    - Uber Freight connection

    For each connection, follow these steps:

    1. Select the connection.
    1. In the **Connection** section, select **Create**.
    1. Set the **Connection Name**, **API Key**, and **Store Host URL** fields.
    1. Select **Save**, and then select **Activate**.
    1. Select **Save and close**.

1. On the **Parameters** tab, set the **Uber Freight customer ID** field.
1. Select **Save**.
1. Select **Activate** to activate the provider.
1. Select **Save and close**.
1. Go to **Providers \> Installed**, and validate that the provider is listed and has a status of **Activated**.

## Out-of-box capabilities

The Uber Freight provider has the following capabilities.

| Capability | Details |
| ---------- | ------- |
| Transformation | **Dataverse Fulfillment Order to Uber Freight Quote:** Transform a fulfillment order from Dataverse to Uber Freight to generate a quote. |
| Transformation | **Dataverse Fulfillment Order to Uber Freight Tender:** Transform a fulfillment order from Dataverse to Uber Freight to generate a shipment booking. |

## Additional resources

[Uber Freight application programming interface (API) documentation](https://developer.uber.com/docs/freight/introduction)
