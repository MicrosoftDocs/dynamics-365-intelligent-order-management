---
author: josaw1
description: Learn about how to set up the Orderful provider in Dynamics 365 Intelligent Order Management.
ms.date: 01/28/2026
ms.custom: 
  - bap-template
ms.topic: how-to
ms.author: anvenkat
title: Set up Orderful provider

---

# Set up Orderful provider

[!include [banner](includes/banner.md)]

This article provides information about how to set up the Orderful provider in Dynamics 365 Intelligent Order Management.

Orderful is a cloud electronic data interchange (EDI) platform for manufacturers, distributors, retailers, and technology companies. The Orderful provider enables Intelligent Order Management to access and process purchase orders from Orderful.  
  
For more information about Orderful, contact Orderful at <sales+msft@orderful.com>.

## Prerequisites

To set up the Orderful provider, you need an Orderful developer account. You can create an account on the [Orderful sign-in page](https://ui.orderful.com).

## Set up the provider

To set up the provider, follow these steps:

1. In Intelligent Order Management, go to **Providers &gt; Catalog**.

1. Select **Add Provider** on the **Orderful** tile.

1. Select **Create** on the **Terms and Conditions** page.

1. Set up two connections in the **Connections** section:

    1. Orderful Dataverse connection.

    1. Orderful connection:

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

       1. Select **Save**.

       1. Select **Activate** to activate the connection.

       1. Select **Save and close**.

1. Go to the **Parameters** tab and add the **Owner Id** and **Webhook Name**.

1. Select **Save**.

1. Select **Activate** to activate the provider.

1. Select **Save and close**.

1. Go to **Providers > Installed** and validate that the provider you set up is listed with the status **Activated**.

## Out-of-box capabilities

|  Capability | Details |
| ------------------ | -------------------------------- |
|    Connection             |   The connection component in Intelligent Order Management allows a provider to establish a connection with an external service. Each provider instance might require one or more connections that it uses to gain access and communicate with the external service.<br>**Orderful Connection**<br>**Orderful Dataverse (current environment) Connection**</br>   |
|    Parameters             |    Some providers require extra configuration information to retrieve and send information.<br>**Owner ID**<br>**Webhook Name**</br>  |
|    Provider   Actions     |    The actions associated with a provider determine what actions are available when you create an orchestration flow.   |
|    Business   Events      |   The events defined for a provider are events that the associate provider actions can raise in the orchestration designer.        |
|    Transformations        |    Provider transformations are essential to any provider that retrieves or sends data from Intelligent Order Management to an external service.<br>**Orderful 850 Purchase Order to Dataverse Sales Order**</br>  |

## Additional resources

[Orderful API documentation](https://docs.orderful.com/)
