---
author: josaw1
description: This topic provides information about how to set up a Dynamics 365 Intelligent Order Management environment.
ms.service: dynamics-365-intelligent-order-management
ms.date: 05/17/2021
ms.topic: conceptual
ms.author: josaw

title: Set up an environment

---


# Set up an environment

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

Dynamics 365 Intelligent Order Management is currently in the public preview release phase so customers can evaluate the app and provide feedback.

To provision a trial environment, see [Deployment](https://docs.microsoft.com/power-platform/admin/trial-environments). After you provision your environment, the **Welcome and get started** page is displayed. The trial environment is preconfigured and you can explore the app using the demo data that's provided.

![Welcome and get started screen ](media/welcome2.png)

## Configuration

On the **Welcome and get started** page, you can access the following features.

- **Configure settings**: Select **Manage** to create and configure required connections. See [create and configure connections](setup.md#Create and configure connections) below for detailed instructions.

- **Manage insights and dashboards**: Select **Manage** to go to the **Daily Events** dashboard, where you can learn more about the configuration for reporting and Power BI Integration.

- **Set up providers for third-party services**: Select **Manage** to go to the provider **Catalog**, where you can configure providers that you want to use to receive orders or communicate to external systems. To learn about providers, see [Working with providers](https://microsoft.sharepoint.com/teams/D365OperationsRedmond/Shared%20Documents/OMS/Documentation/work-providers.md).

- **Orchestrate your order journeys**: Select **Manage** to go to the pages where you can create and manage order orchestration flows.

- **Explore data management**: Select **Manage** to go to the administration pages to manage data import and export.

- **Enable fulfillment optimization**: Select **Manage** to go to configure the fulfillment optimization service with Intelligent Order Management.

- **Configure inventory visibility services**: Select **Manage** to go to the pages where you can configure the inventory service to be used with Intelligent Order Management.

- **Invite your teammates**: Select **Manage** to go to the page where you can invite users to your environment.


## Create and configure connections

To configure Intelligent Order Management so that you can orchestrate orders using a DOM provider, you will first need to create three Dataverse connections, one Intelligent Order Management Data Transformer connection, and one Power Automate Management connection. 

To create and configure the connections, follow these steps. 

1. Go to **Getting Started \> Configure Settings**. 
1. Create the following new connection references:
    - IOM Data Transformer
    - Microsoft Dataverse 
    - Microsoft Dataverse - Application
    - Microsoft Dataverse - Integration
    - Power Automate Management
1. On the **Active IOM Platform Connection References** page, select **IOM Data Transformer**. 
1. Under **Connections**, select **Retrieve Connection Link** to open Microsoft Power Automate in a new tab. If it your first time setting up a connection, you will need to sign up for Microsoft Power Automate. Ensure that you are in right Dataverse environment.  
1. Go to **Data \> Connections**. Select **New Connection**, and in the search bar on the top right enter "IOM Data Transformer" and create a new connection. 
1. When the connection dialog box appears, accept it and then copy the browser URL to the connection.
1. On the **IOM Data Transformer** page, paste the copied URL into the **Connection URL** field.
1. Select **Save and Close**. 
1. On the **Active IOM Platform Connection References** page, repeat steps 4-8 to configure the remaining four connections. 
