---
author: josaw1
description: This topic provides information about how to set up the BigCommerce provider in Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 06/30/2021
ms.topic: how-to
ms.author: josaw

title: Set up BigCommerce provider

---

# Set up BigCommerce provider

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic provides information about how to set up the BigCommerce provider in Dynamics 365 Intelligent Order Management.

BigCommerce is a flexible, open SaaS platform. You can connect to BigCommerce to retrieve orders, products, and related information. The BigCommerce provider enables Intelligent Order Management to access and process purchase orders from BigCommerce.  

For more information about BigCommerce, see the [BigCommerce website](https://www.bigcommerce.com/). 

## Prerequisites 

You need to have a sample store set up. Go to the [BigCommerce Essentials website](https://www.bigcommerce.com/essentials/) and select **Start your free trial**. Follow the instructions to set up your sample store. To remove the 15-day trial limitation, contact BigCommerce.

## Set up the provider
To set up the provider, follow these steps: 

1.  In Intelligent Order Management, go to **Providers > Catalog**.

2.  Select **Add Provider** on the **BigCommerce** tile.

3.  Select **Create** on the **Terms and Conditions** page.

4.  There are two connections that you need to set up in the **Connections** section.

    1. BigCommerce Common Data Service Connection;

    2. BigCommerce connection:

          1. Select the connection.

          3. Select the **Retrieve Connection Link** URL.

          5. Search for **BigCommerce** and then select the connector.

          7. Enter the following information: 
              - **Connection Name**: Enter a name of your choice.
              - **API Key**: Enter the BigCommerce API key. You can retrieve it by following the instructions here: https://\<your store hash code\>.mybigcommerce.com/manage/settings/auth/api-accounts.

          9. Save the connection.

          11. Test the connection by selecting **Test** in the top ribbon.

          13. Copy your URL.

          15. Go back to the **Connection URL** page in Intelligent Order Management and paste the URL.

5. Go to the **Parameters** tab and add the BigCommerce store hash.

## Out-of-box capabilities

The BigCommerce provider has the following capabilities:

|  Capability | Details |
| ------------------ | -------------------------------- |
|  Business events  | **Billing of order confirmed by billing provider**: Event that indicates that billing was confirmed by BigCommerce.</br><br>**Creation of fulfillment line succeeded**: Event that indicates that a fulfillment line was successfully created.</br><br>**Creation of fulfillment order failed**: Event that indicates that fulfillment of the order failed.</br><br>**Creation of fulfillment order succeeded**: Event that indicates that fulfillment of the order succeeded.</br>  |
| Transformation  |  **BigCommerce sales order to Microsoft Dataverse sales order**: Transforms a purchase order from BigCommerce into a sales order in Dataverse.|

## Additional resources

To learn more about BigCommerce's API, see the [BigCommerce API documentation](https://developer.bigcommerce.com/api-docs).
