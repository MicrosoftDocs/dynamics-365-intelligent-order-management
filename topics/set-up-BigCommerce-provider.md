--
author: josaw1
description: This topic provides instructions for how to set up the BigCommerce provider in Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 05/17/2021
ms.topic: how-to
ms.author: josaw
search.app: 
  - 
search.audienceType: 
  - 
title: Set up BigCommerce provider

---

# Set up BigCommerce provider

[!include [banner](includes/banner.md)]


This topic provides instructions for how to set up the BigCommerce provider in Dynamics 365 Intelligent Order Management.

BigCommerce is a flexible, open SaaS platform. You can connect to BigCommerce to retrieve orders, products, and related information. The BigCommerce provider enables Intelligent Order Management to access and process purchase orders from BigCommerce.  
  
For more information about BigCommerce, visit \[their website\](https://www.bigcommerce.com/). To learn more about BigCommerce's API, read their \[public documentation\](https://developer.bigcommerce.com/api-docs).

## Prerequisites 

To set up the BigCommerce provider, you need to have a BigCommerce developer account. You can create an account on \[this page\](https://developer.bigcommerce.com/).

## Set up the provider

1.  In Intelligent Order Management, go to **Providers > Catalog**.

2.  Select **Add Provider** on the **BigCommerce** tile.

3.  Select **Create** on the **Terms and Conditions** page.

4.  There are two connections that you need to set up in the **Connections** section.

    1.  BigCommerce Common Data Service Connection&lt;I don't see a connector in power automate for this. How do I set it up?&gt;

    2.  BigCommerce connection:

        1.  Select the connection.

        2.  Select the **Retrieve Connection Link** URL.

        3.  Search for **BigCommerce** and then select the connector.

        4.  Enter the following information: **Connection Name**: enter a name of your choice;**API Key**: enter the BigCommerce API key. You can retrieve it by following the instructions here: https://&lt;your store hash code&gt;.mybigcommerce.com/manage/settings/auth/api-accounts

        5.  Save the connection.

        6.  Test the connection to ensure that it is established by selecting **Test** in the top ribbon.

        7.  Copy your URL.

        8.  Go back the **Connection URL** page in Intelligent Order Management and paste the URL.

5.  Go to the **Parameters** tab and add the BigCommerce store hash&lt;where do you find this information?&gt;

## Out of box capabilities

The BigCommerce provider has the following capabilities:

Business Events:

-   Billing of order confirmed by billing provider: event that indicates that billing was confirmed by BigCommerce

-   Creation of fulfillment line succeeded: event that indicates that a fulfillment line was successfully created.

-   Creation of fulfillment order failed: event that indicates that fulfillment of the order failed.

-   Creation of fulfillment order succeeded: event that indicates that fulfillment of the order succeeded.


Transformation:

-   BigCommerce sales order to Microsoft Dataverse sales order: transforms a purchase order from BigCommerce into a sales order in Dataverse.
