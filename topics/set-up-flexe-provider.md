---
author: josaw1
description: This topic provides instructions for how to set up the Flexe provider in Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 05/17/2021
ms.topic: how-to
ms.author: josaw

title: Set up Flexe provider

---

# Set up Flexe provider

[!include [banner](includes/banner.md)]


This topic provides instructions for how to set up the Flexe provider in Dynamics 365 Intelligent Order Management.

Flexe is warehousing and fulfillment service that provides simple integrations, performance insights, and scalability. The Flexe provider enables Intelligent Order Management to access and process purchase orders from Flexe.  
  
For more information about Flexe, visit [their website](https://www.flexe.com/why-flexe/technology-platform). To learn more about Flexe's API, read their [public documentation](https://developer-sandbox.flexe.com/doc/public).

## Prerequisites 

To set up the Flexe provider, you need to have Flexe developer account. You can create an account on [this page](https://developer-sandbox.flexe.com).

## Set up the provider

1. In Intelligent Order Management, go to **Providers > Catalog**.

2. Select **Add Provider** on the **Flexe** tile.

3. Select **Create** on the **Terms and Conditions** page.

4. There are two connections that you need to set up in the **Connections** section.

    1. Flexe Common Data Service connection <I don't see a connector in power automate for this. How do I set it up?>

    1. Flexe connection:

        1. Select the connection.

        1. Select the **Retrieve Connection Link** URL.

        1. Search for **Flexe** and then select the connector.

        1. Enter the following information: **Connection Name**: enter a name of your choice; **API Key**: enter the Flexe API key. You can retrieve it by following the instructions [here](https://developer-sandbox.flexe.com/tokens).

        1. Save the connection.

        1. Test the connection by selecting **Test** in the top ribbon.

        1. Copy your URL.

        1. Go back the **Connection URL** page in Intelligent Order Management and paste the URL.

5.  Go to the **Parameters** tab and add the **Owner Id** and **Webhook Name**. <where do I find this information?>

##  Out of box capabilities

The Flexe provider has the following capabilities.

Business Events:

-   Billing of order confirmed by billing provider: event that indicates that billing was confirmed by Flexe

-   Creation of fulfillment line succeeded: event that indicates that a fulfillment line was successfully created.

-   Creation of fulfillment order failed: event that indicates that fulfillment of the order failed.

-   Creation of fulfillment order succeeded: event that indicates that fulfillment of the order succeeded.

Actions: <I don't see any actions in the current environment, is this correct?>

-   Transformation:

    -   Microsoft Dataverse fulfillment line to Flexe order line: transforms a fulfillment order line from Intelligent Order Management to a Flexe order line.

    -   Dataverse fulfillment order to Flexe order: transforms a fulfillment order from Intelligent Order Management to a Flexe order.
