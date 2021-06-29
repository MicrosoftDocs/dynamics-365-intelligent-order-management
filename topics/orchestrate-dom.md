---
author: v-chgri
description: This topic describes how to Orchestrate orders using a Distributed Order Management (DOM) provider in Microsoft Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 06/29/2021
ms.topic: conceptual
ms.author: josaw

title: Orchestrate orders using a Distributed Order Management (DOM) provider

---

# Orchestrate orders using a Distributed Order Management (DOM) provider

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic describes how to orchestrate orders using a Distributed Order Management (DOM) provider in Microsoft Dynamics 365 Intelligent Order Management.

> [!NOTE]
> To orchestrate orders using a DOM provider, you will need to use external DOM providers to bring orders into the system.

## Get started orchestrating orders using a DOM provider

To get started orchestrating orders using a DOM provider in Dynamics 365 Intelligent Order Management, follow these steps.

1. Click on Getting Started -> Configure Settings.
1. We will need to create three individual Dataverse Connector settings, one IOM Data Transformer and one Power Automate Management connection. 
1. Select the first record for “IOM Data Transformer”. 
1. Click on Retrieve Connection Link that opens a new tab. 
1. If it is first time, you will sign up for Power Automate. Ensure you are in right Dataverse Environment. From the Data -> Connections page, click on New Connection and in the search bar on the right. Type IOM Data Transformer and create a connection. It shows a connection popup. Please accept it and copy the browser link to this connection. 
1. Click on Save and Close. 
1. Select the next one and build a connector for Dataverse similarly. 
1. From the Catalog -> Add Provider and choose Dynamics 365 Distributed Order Management
1. Click on Connections and it will take you to connection reference page.
1. Click on Retrieve Connection Link and provide a new Dataverse Connection link
1. Click “New Connection”
1. Search for Dataverse on the right side corner
1. Click on Plus and it will show you this screenshot
1. It will open another popup for authentication. Please do that. Then the connection is created. Look at modified in the list. 
1. Open this and retrieve the link to the URL for your connection.
1. Go back to IOM Provider UI and click on “Save” and “Activate”. Click on Save and Close. 
1. Now we will need to activate the Provider. 
1. Click on Activate
1. It will activate the provider. It will take some time to activate. Action is automatically created. 
1. Now you can add “Send to Retail DOM” node in the Orchestration journey as shown below
1. Go to Action Types 
1. Select “Fulfillment Determination”
1. Select the Action Type Input Business Event and change the Business Event Definition to new order.
1. Click Save and Close. 
1. Now to go to Order Orchestration Journey and Add Send to DOM node with following details. 
1. Publish your Orchestration. This will help you orchestrate orders that are imported from different providers. It will not run for Orders that are created within IOM or within Dataverse directly. 


