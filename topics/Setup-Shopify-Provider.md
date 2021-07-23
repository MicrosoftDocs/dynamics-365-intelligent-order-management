---
author: sumanic
description: This topic provides information about how to set up the Shopify provider in Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 07/09/2021
ms.topic: how-to
ms.author: sumanic

title: Set up Shopify provider

---

# Set up Shopify provider

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic provides information about how to set up the Shopify provider in Dynamics 365 Intelligent Order Management.

Shopify is a flexible, open SaaS platform. You can connect to Shopify to retrieve orders, products, and related information. The Shopify provider enables Intelligent Order Management to access and process orders from Shopify. 
  
For more information about Shopify, see [their website](http://www.shopify.com). 

## Prerequisites

You need to have a sample app or store set up. Go to the Shopify website and create a trial account . 
Follow the instructions to set up your sample store or build your own app through the Get Started page.
To remove the 30-day trial limitation, contact Shopify.


To set up the Shopify provider, you need to have an Shopify partner account. You can create a [trial account](https://accounts.shopify.com/signup?rid=e573fe3c-1e76-474a-9fb5-76645ad78172) here.

## Set up the provider

To set up the provider, follow these steps:

1. In Intelligent Order Management, go to **Providers &gt; Catalog**.

2. Select **Add Provider** on the **Shopify** tile.

3. Select **Create** on the **Terms and Conditions** page.

4. There are two connections that you need to set up in the **Connections** section.

    1. Shopify Dataverse connection.

    2. Shopify connection:

        1. Select the connection.

        1. Select the **Retrieve Connection Link** URL.

        1. Search for **Shopify** and then select the connector.

        1. Enter the following information: 
            - **Connection Name**: Enter a name of your choice.
            - **API Key**: Enter the Shopify API key. You can retrieve it by following the instructions [here](https://ui.orderful.com/settings/api-credentials).

        1. Save the connection.

        1. Test the connection by selecting **Test** in the top ribbon.

        1. Copy your URL.

        1. Go back to the **Connection URL** page in Intelligent Order Management and paste the URL.

5.  Go to the **Parameters** tab and add the **Store URL**. <where do I find this information>
  
6. Select Save.

7. Select Activate to activate the provider.

8. Select Save & Close.

9. Go to Providers > Installed and validate that the provider you set up is listed with the status Activated.

##  Out-of-box capabilities

|  Capability | Details |
| ------------------ | -------------------------------- |
|    Connection             |   The connection component in Intelligent Order Management allows a provider to establish a connection with an external service. Each provider instance may require one or more connections that it uses to gain access and communicate with the external service.<br>**Shopify Connection**<br>**Shopify Dataverse (current environment) Connection**</br>   |
|    Parameters             |    Some providers require additional configuration information to retrieve and send information.<br>**Store URL**</br>  |
|    Provider   Actions     |    The actions associated with a provider determine what actions are available to you when you create an orchestration flow.   |
|    Business   Events      |   The events defined for a provider are events that the associate provider actions can raise in the orchestration designer.        |
|    Transformations        |    Provider transformations are essential to any provider that retrieves or sends data from Intelligent Order Management to an external service.<br>**Shopify Sales Order to Dataverse Sales Order**</br>  |
