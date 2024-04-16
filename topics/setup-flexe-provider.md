---
author: josaw1
description: This topic provides information about how to set up the Flexe provider in Dynamics 365 Intelligent Order Management.
ms.date: 04/12/2024
ms.custom: 
  - bap-template
ms.topic: how-to
ms.author: josaw

title: Set up Flexe provider

---

# Set up Flexe provider

[!include [banner](includes/banner.md)]


This topic provides information about how to set up the Flexe provider in Dynamics 365 Intelligent Order Management.

Flexe is warehousing and fulfillment service that provides simple integrations, performance insights, and scalability. The Flexe provider enables Intelligent Order Management to access and process purchase orders from Flexe.  

For more information about Flexe, see the [Flexe website](https://www.flexe.com/why-flexe/technology-platform). 

## Prerequisites 

To set up the Flexe provider, you need to have Flexe developer account. You can create an account on the [Flexe developer portal](https://developer-sandbox.flexe.com).


## Set up the provider
To set up the provider, follow these steps:

1. In Intelligent Order Management, go to **Providers > Catalog**.

2. Select **Add Provider** on the **Flexe** tile.

3. Select **Create** on the **Terms and Conditions** page.

4. There are two connections that you need to set up in the **Connections** section.

    1. Flexe Common Data Service connection.

    3. Flexe connection:

        1. Select the connection.

        1. Select the **Retrieve Connection Link** URL.

        1. Search for **Flexe** and then select the connector.

        1. Enter the following information: 
            - **Connection Name**: Enter a name of your choice.
            - **API Key**: Enter the Flexe API key. You can retrieve it by following the instructions [here](https://developer-sandbox.flexe.com/tokens).

        1. Save the connection.

        1. Test the connection by selecting **Test** in the top ribbon.

        1. Copy your URL.

        1. Go back to the **Connection URL** page in Intelligent Order Management and paste the URL.

5.  Go to the **Parameters** tab and add the **Owner ID** and **Webhook Name**.

##  Out-of-box capabilities

The Flexe provider has the following capabilities.

|  Capability | Details |
| ------------------ | -------------------------------- |
|  Business events   | **Billing of order confirmed by billing provider**: Event that indicates that billing was confirmed by Flexe. <br>**Creation of fulfillment line succeeded**: Event that indicates that a fulfillment line was successfully created. <br>**Creation of fulfillment order failed**: Event that indicates that fulfillment of the order failed. <br>**Creation of fulfillment order succeeded**: Event that indicates that fulfillment of the order succeeded.   |
|  Transformation    |  **Microsoft Dataverse fulfillment line to Flexe order line**: Transforms a fulfillment order line from Intelligent Order Management to a Flexe order line. <br>**Dataverse fulfillment order to Flexe order**: Transforms a fulfillment order from Intelligent Order Management to a Flexe order.   |

## Additional resources
To learn more about Flexe's API, see the [Flexe API documentation](https://developer-sandbox.flexe.com/doc/public).
