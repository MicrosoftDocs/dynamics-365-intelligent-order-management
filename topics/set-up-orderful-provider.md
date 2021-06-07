---
author: josaw1
description: This topic provides information about how to set up the Orderful provider in Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 06/04/2021
ms.topic: how-to
ms.author: josaw

title: Set up Orderful provider

---

# Set up Orderful provider

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic provides information about how to set up the Orderful provider in Dynamics 365 Intelligent Order Management.

Orderful is a cloud electronic data interchange (EDI) platform for manufacturers, distributors, retailers, and technology companies. The Orderful provider enables Intelligent Order Management to access and process purchase orders from Orderful.  
  
For more information about Orderful, see the [Orderful website](https://orderful.com/). To learn more about Orderful's API, see the [Orderful API documentation](https://docs.orderful.com/).

## Prerequisites

To set up the Orderful provider, you need to have an Orderful developer account. You can create an account on [Orderful sign-in page](https://ui.orderful.com).

## Set up the provider

To set up the provider, follow these steps:

1. In Intelligent Order Management, go to **Providers &gt; Catalog**.

2. Select **Add Provider** on the **Orderful** tile.

3. Select **Create** on the **Terms and Conditions** page.

4. There are two connections that you need to set up in the **Connections** section.

    1. Orderful Dataverse connection.

    2. Orderful connection:

        1. Select the connection.

        1. Select the **Retrieve Connection Link** URL.

        1. Search for **Orderful** and then select the connector.

        1. Enter the following information: 
            - **Connection Name**: Enter a name of your choice.
            - **API Key**: Enter the Orderful API key. You can retrieve it by following the instructions [here](https://ui.orderful.com/settings/api-credentials).

        1. Save the connection.

        1. Test the connection by selecting **Test** in the top ribbon.

        1. Copy your URL.

        1. Go back to the **Connection URL** page in Intelligent Order Management and paste the URL.

5.  Go to the **Parameters** tab and add the **Owner Id** and **Webhook Name**. <where do I find this information>

##  Out-of-box capabilities

|  Capability | Details |
| ------------------ | -------------------------------- |
|    Connection             |   The connection component in Intelligent Order Management allows a provider to establish a connection with an external service. Each provider instance may require one or more connections that it uses to gain access and communicate with the external service.<br>**Orderful Connection<**/br><br>**Orderful Dataverse (current environment) Connection**</br>   |
|    Parameters             |    Some providers require additional configuration information to retrieve and send information.<br>**Owner ID**</br><br>**Webhook Name**</br>  |
|    Provider   Actions     |    The actions associated with a provider determine what actions are available to you when you create an orchestration flow.   |
|    Business   Events      |   The events defined for a provider are events that the associate provider actions can raise in the orchestration designer.        |
|    Transformations        |    Provider transformations are essential to any provider that retrieves or sends data from Intelligent Order Management to an external service.<br>**Orderful 850 Purchase Order to Dataverse Sales Order**</br>  |
