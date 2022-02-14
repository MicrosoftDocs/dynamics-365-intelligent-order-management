---
author: sumanic
description: This topic provides information about how to set up the Avalara provider in Dynamics 365 Intelligent Order Management.
ms.date: 07/26/2021
ms.topic: how-to
ms.author: sumanic

title: Set up Avalara provider

---

# Set up Avalara provider

[!include [banner](includes/banner.md)]


This topic provides information about how to set up the Avalara provider in Dynamics 365 Intelligent Order Management.

Avalara is software for automated tax compliance. The Avalara provider enables Intelligent Order Management to validate addresses and calculate tax from Avalara.  
  
For more information about Avalara, see the [Avalara website](https://www.avalara.com/us/en/index.html). 

## Prerequisites

To set up the Avalara provider, you need to have an Avalara developer account. To create an account, go to the [Avalara get started page](https://www.avalara.com/us/en/get-started.html).

## Set up the provider

To set up the provider, follow these steps:

1. In Intelligent Order Management, go to **Providers > Catalog**.

2. Select **Add Provider** on the **Avalara** tile.

3. Select **Create** on the **Terms and Conditions** page.

4. There are two connections that you need to set up in the **Connections** section.

    1. Avalara Dataverse (current environment) connection.

    2. Avalara connection:

       1. Select the connection.

       1. Select the **Retrieve Connection Link** URL.

       1. Search for **Avalara** and then select the connector.

       1. Enter the following information: 
          - **Connection Name**: Enter a name of your choice.
          - **Username**: Enter your Avalara login username.
          - **Password**: Enter your Avalara password.

       1. Save the connection.

       1. Test the connection by selecting **Test** in the top ribbon.

       1. Copy your URL.

       1. Go back to the **Connection URL** page in Intelligent Order Management and paste the URL.

       1. Select **Save**.

       1. Select **Activate** to activate the connection.

       1. Select **Save and close**.

5.  Go to the **Parameters** tab and add the **Avalara Company Code**. 

6. Select **Save**.

7. Select **Activate** to activate the provider.

8. Select **Save and close**.

9. Go to **Providers > Installed** and validate that the provider you set up is listed with the status **Activated**.


##  Out-of-box capabilities

|  Capability | Details |
| ------------------ | -------------------------------- |
|    Connection             |   The connection component in Intelligent Order Management allows a provider to establish a connection with an external service. Each provider instance may require one or more connections that it uses to gain access and communicate with the external service.<br>**Avalara Connection**<br>**Avalara Dataverse (current environment) Connection**   |
|    Parameters             |    Some providers require additional configuration information to retrieve and send information.<br>**Avalara Company Code**  |
|    Provider Actions     |    The actions associated with a provider determine what actions are available to you when you create an orchestration flow. The following actions are available as out-of-the-box capabilities: <br>**Resolve Address**<br>**Calculate Tax**|
|    Business Events      |   The events defined for a provider are events that the associate provider actions can raise in the orchestration designer.        |
|    Transformations        |    Provider transformations are essential to any provider that retrieves or sends data from Intelligent Order Management to an external service.<br>**Build Avalara CreateTransaction payload**<br>**Build Avalara ResolveAddress payload** |

## Additional resources
[Avalara API documentation](https://developer.avalara.com/documentation/)
