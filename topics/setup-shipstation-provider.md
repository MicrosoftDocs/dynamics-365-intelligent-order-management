---
author: sumanic
description: This topic describes how to set up the ShipStation provider in Dynamics 365 Intelligent Order Management.
ms.date: 07/27/2021
ms.topic: how-to
ms.author: sumanic

title: Set up ShipStation provider

---

# Set up ShipStation provider

[!include [banner](includes/banner.md)]


This topic describes how to set up the ShipStation provider in Dynamics 365 Intelligent Order Management.

ShipStation is a software as a service (SaaS) shipping platform that allows you to manage all your small parcel shipping needs in one place. The ShipStation provider enables Intelligent Order Management to access and manage carrier pickups.  
  
To contact ShipStation for more information, see [Contact Support](https://help.shipstation.com/hc/sections/360004023491-Contact-Support). 

## Prerequisites

To set up the ShipStation provider, you must have a ShipStation trial account. To create a trial account, see [Create My Account](https://www.shipstation.com/step1/).

## Set up the ShipStation provider

To set up the ShipStation provider, follow these steps:

1. In Intelligent Order Management, go to **Providers \> Catalog**.
1. Select **Add Provider** on the **ShipStation** tile.
1. Select **Create** on the **Terms and Conditions** page.
1. In the **Connections** section, set up the **ShipStation Dataverse** connection.
1. In the **Connections** section, set up the **ShipStation** connection:
    1. Select the connection.
    1. Select **Retrieve Connection Link**.
    1. Search for **ShipStation** and then select the connector. 
    1. For **Connection Name**, enter a name for the connection.
    1. For **Username**, enter the ShipStation API key located at https://ss.shipstation.com/#/settings/api. 
    1. For **Password**, enter the ShipStation API secret located at https://ss.shipstation.com/#/settings/api.
    1. Save the connection.
    1. Copy the connection URL.
    1. Go back to the **Connection URL** page in Intelligent Order Management and paste the URL.
    1. Select **Save**.
    1. Select **Activate** to activate the connection.
    1. Select **Save and close**.
1.  Select **Activate** to activate the provider.
1.  Select **Save and close**.
1.  Go to **Providers \> Installed** and confirm that the provider you set up is listed with the status **Activated**.

##  Out-of-box provider capabilities

The following table describes the out-of-box provider capabilities in Intelligent Order Management.

|  Capability | Details |
| ------------------ | -------------------------------- |
|    Connection             |   The connection component in Intelligent Order Management allows a provider to establish a connection with an external service. Each provider instance may require one or more connections that it uses to gain access and communicate with the external service.<br>**ShipStation connection**<br>**ShipStation Dataverse connection (current environment)**   |
|    Parameters             |    Some providers require additional configuration information to retrieve and send information.
|    Provider actions     |    The actions associated with a provider that determine what actions are available to you when you create an orchestration flow.   |
|    Business events      |   The events defined for a provider are events that the associated provider actions can raise in the orchestration designer.        |
|    Transformations        |    Provider transformations are essential to any provider that retrieves or sends data from Intelligent Order Management to an external service.<br>**Dataverse fulfillment order to ShipStation order**  |

## Additional resources

[ShipStation API documentation](https://www.shipstation.com/docs/api/)
