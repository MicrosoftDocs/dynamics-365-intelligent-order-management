---
author: josaw1
description: This topic provides information about how to set up the BigCommerce provider in Dynamics 365 Intelligent Order Management.
ms.date: 01/28/2026
ms.custom: 
  - bap-template
ms.topic: how-to
ms.author: anvenkat
title: Set up BigCommerce provider

---

# Set up BigCommerce provider

[!include [banner](includes/banner.md)]

This topic provides information about how to set up the BigCommerce provider in Dynamics 365 Intelligent Order Management.

BigCommerce is a flexible, open SaaS platform. You can connect to BigCommerce to retrieve orders, products, and related information. The BigCommerce provider enables Intelligent Order Management to access and process purchase orders from BigCommerce.  

For more information about BigCommerce, see the [BigCommerce website](https://www.bigcommerce.com).

## Prerequisites

You need to have a sample store set up. Go to the [BigCommerce website](https://www.bigcommerce.com) and select **Start your free trial**. Follow the instructions to set up your sample store.

## Set up the provider

To set up the provider, follow these steps:

1. In Intelligent Order Management, go to **Providers > Catalog**.

1. Select **Add Provider** on the **BigCommerce** tile.

1. Select **Create** on the **Terms and Conditions** page.

1. There are two connections that you need to set up in the **Connections** section.

    1. BigCommerce Common Data Service Connection

    1. BigCommerce connection:

        1. Select the connection.

        1. Select the **Retrieve Connection Link** URL.

        1. Search for **BigCommerce** and then select the connector.

        1. Enter the following information:

            - **Connection Name**: Enter a name of your choice.
            - **API Key**: Enter the BigCommerce API key. You can retrieve it by following the instructions here: https://\<your store hash code\>.mybigcommerce.com/manage/settings/auth/api-accounts.

        1. Save the connection.

        1. Test the connection by selecting **Test** in the top ribbon.

        1. Copy your URL.

        1. Go back to the **Connection URL** page in Intelligent Order Management and paste the URL.

        1. Select **Save**.

        1. Select **Activate** to activate the connection.

        1. Select **Save and close**.

1. Go to the **Parameters** tab and add the BigCommerce store hash.

1. Select **Save**.

1. Select **Activate** to activate the provider.

1. Select **Save and close**.

1. Go to **Providers > Installed** and validate that the provider you set up is listed with the status **Activated**.

## Out-of-box capabilities

The BigCommerce provider has the following capabilities:

|  Capability | Details |
| ------------------ | -------------------------------- |
|  Business events  | <p>**Billing of order confirmed by billing provider**: Event that indicates that billing was confirmed by BigCommerce.</p><p>**Creation of fulfillment line succeeded**: Event that indicates that a fulfillment line was successfully created.</p><p>**Creation of fulfillment order failed**: Event that indicates that fulfillment of the order failed.</p><p>**Creation of fulfillment order succeeded**: Event that indicates that fulfillment of the order succeeded.</p>  |
| Transformation  |  **BigCommerce sales order to Microsoft Dataverse sales order**: Transforms a purchase order from BigCommerce into a sales order in Dataverse.|

## Additional resources

- [BigCommerce API documentation](https://developer.bigcommerce.com/api-docs) – Learn more about BigCommerce's API.
- [Run sample order orchestration flow from BigCommerce](run-sample-order-bigcommerce.md)
