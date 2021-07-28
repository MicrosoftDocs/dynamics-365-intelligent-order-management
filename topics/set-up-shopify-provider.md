---
author: sumanic
description: This topic describes how to set up the Shopify provider in Microsoft Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 07/28/2021
ms.topic: how-to
ms.author: sumanic

title: Set up Shopify provider

---

# Set up the Shopify provider

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic describes how to set up the Shopify provider in Microsoft Dynamics 365 Intelligent Order Management.

Shopify is a flexible, open software as a service (SaaS) platform. You can connect to Shopify to retrieve orders, products, and related information. The Shopify provider enables Dynamics 365 Intelligent Order Management to access and process orders from Shopify. 
  
For more information about Shopify, see http://www.shopify.com. 

## Prerequisites

To set up the Shopify provider, you must have a Shopify partner trial account. To create a trial account, see [Shopify Signup](https://accounts.shopify.com/signup?rid=e573fe3c-1e76-474a-9fb5-76645ad78172). Follow the instructions to set up your sample store or build your own app. To remove the 30-day trial limitation, contact Shopify.

## Set up the provider

To set up the provider, follow these steps:

1. In Intelligent Order Management, go to **Providers \> Catalog**.
1. Select **Add Provider** on the **Shopify** tile.
1. Select **Create** on the **Terms and Conditions** page.
1. In the **Connections** section, set up the **Shopify Dataverse** connection.
1. In the **Connections** section, set up the **Shopify** connection:
    1. Select the connection.
    1. Select **Retrieve Connection Link**.
    1. Search for **Shopify** and then select the connector. 
    1. For **Connection Name**, enter a name for the connection.
    1. For **API Key**, enter the Shopify API key, which you can retrieve by following the instructions at https://ui.orderful.com/settings/api-credentials. 
    1. Save the connection.
    1. Test the connection by selecting **Test** in the top ribbon.
    1. Copy the connection URL.
    1. Go back to the **Connection URL** page in Intelligent Order Management and paste the URL.
    1. Go to the **Parameters** tab and add the **Store URL**.
    1. Select **Save**.
    1. Select **Activate** to activate the connection.
    1. Select **Save and close**.
1.  Select **Activate** to activate the provider.
1.  Select **Save and close**.
1.  Go to **Providers \> Installed** and confirm that the provider you set up is listed with the status **Activated**.

##  Out-of-box provider capabilities

|  Capability | Details |
| ------------------ | -------------------------------- |
|    Connection             |   The connection component in Intelligent Order Management allows a provider to establish a connection with an external service. Each provider instance may require one or more connections that it uses to gain access and communicate with the external service.<br><br>Shopify-related connections:<br><ul><li>Shopify connection</li><li>Shopify Dataverse connection (current environment)</li></ul>   |
|    Parameters             |    Some providers require additional configuration information to retrieve and send information.<br><br>Shopify-related parameters:<br><ul><li>Store URL</li></ul>  |
|    Provider actions     |    The actions associated with a provider determine what actions are available to you when you create an orchestration flow.   |
|    Business events      |   The events defined for a provider are events that the associated provider actions can raise in the orchestration designer.        |
|    Transformations        |    Provider transformations are essential to any provider that retrieves or sends data from Intelligent Order Management to an external service.<br><br>Shopify-related transformations:<br><ul><li>Shopify sales order to Dataverse sales order</li></ul> |
