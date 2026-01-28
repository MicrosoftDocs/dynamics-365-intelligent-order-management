---
author: sumanic
description: This article describes how to set up the FedEx provider in Microsoft Dynamics 365 Intelligent Order Management.
ms.date: 01/28/2026
ms.custom: 
  - bap-template
ms.topic: how-to
ms.author: anvenkat
title: Set up the FedEx provider

---

# Set up the FedEx provider

[!include [banner](includes/banner.md)]

This article describes how to set up the FedEx provider in Microsoft Dynamics 365 Intelligent Order Management.

FedEx Corporation is an American multinational conglomerate holding company that's based in Memphis, Tennessee, and is focused on transportation, e-commerce, and business services. It was formerly known as Federal Express Corporation and later as FDX Corporation. The name "FedEx" is a syllabic abbreviation of the name of the company's original air division, Federal Express, which was used from 1973 until 2000. For more information about FedEx, see the [FedEx website](https://www.fedex.com/en-us/about.html).

Dynamics 365 Intelligent Order Management integrates with FedEx services as an out-of-box provider model.

## Prerequisites

FedEx has the following three areas of operations. To use the capabilities of these areas via Intelligent Order Management, customers must make their credentials available across them.

- **FedEx APIF** – This FedEx area focuses on FedEx logistics that help brands access new information and capabilities so that they can better fulfill, ship, and service customer orders. To be able to register and integrate with the FedEx APIF APIs, you must follow these steps:

    1. Create a FedEx developer portal account by following the steps in [Getting started](https://developer.fedex.com/api/en-us/get-started.html).
    1. Copy your project's **API key**, **Secret**, and **Shipping account** values from the developer portal. You'll need these values later, when you set up the connection and future transactions.

- **FedEx Dataworks** – This FedEx area focuses on intelligence and predictability aspects of logistics, such two-day delivery and expected delivery delay predictions. The APIs in this area are manually onboarded, and you must connect with FedEx to obtain the credentials to onboard them.
- **FedEx Return Tech** – This FedEx area lets you enable easy returns from an e-commerce website through a branded, seamless customer return process that includes an option for a printer-less QR code experience and the ability to choose from approximately 60,000 drop-off locations. To configure FedEx Return Tech, follow these steps:

    1. Register in the [FedEx developer portal](https://developer-sandbox.supplychain.fedex.com/sandbox/) for the sandbox environment.
    1. Register in the [FedEx fulfillment portal](https://fulfillment.fedex.com/) for the production environment.
    1. After you're registered, go to [FedEx Supply Chain Developer Production](https://dev.supplychain.fedex.com/), and create an **API Connect** account. You can then select the FedEx Return Tech APIs to use and obtain approval. Subsequent steps will be enabled by the FedEx onboarding team. A **Retailer Commerce ID** value will be generated that you can use for future transactions.

## Set up FedEx connections

To set up the FedEx connections in Intelligent Order Management, follow these steps:

1. Go to **Providers**, and then select **Library**.
1. Select **FedEx**, and then select **Activate Providers**.
1. In the **Terms and Conditions** wizard, select **FedEx**, and then select **Accept**.
1. Review the events and actions.
1. In the **Connections** section, confirm the **Microsoft Dataverse** connection that should have connected automatically.
1. Next to the **FedEx** connection, select **Create**.
1. Enter a **Connection name** value, select the environment (**Sandbox** or **Production**), enter a **Client Id** value, and enter a **Client Secret** value.
1. Select **Create**.
1. Repeat steps 6 through 8 for the **FedEx Dataworks** connection.
1. Repeat step 6 through 8 for the **FedEx Supply Chain Returns** connection. For this connection, you must also enter **Client Application Name**, **Client Application Username**, and **Client Application password** values. 
1. After all the connections show green check marks, select **Next**.
1. If you're using the webhook from FedEx Dataworks, enter the **EDD Webhook CallbackSignatureKey** value. This key is the webhook name that was registered to consume estimated delivery delay updates from FedEx. 
1. Enter the **Retail Commerce ID** value. This ID was generated when you registered with FedEx Return Tech.
1. Select **Next**.
1. Review the setup.
1. Select **Next**.
1. Review the connections, and then select **Activate**. The final page of the wizard will show a status of **Inactive** for a short time but should then show a status of **Active**.

## Out-of-box capabilities

*Provider actions* are associated with a provider and determine the actions that are available to you when you create an orchestration flow.

The FedEx provider has the following capabilities.

| Action | Description |
| ---------- | ------- |
| FedEx Validate Address | This provider action validates the correctness of the shipping address with FedEx. |
| Select FedEx TSS Plan | This provider action optimizes the best plan for fulfillment, based on available inventory. |
| FedEx Generate Shipping Label | This provider action generates the shipping label from FedEx for forward shipments. |
| FedEx Cancel Shipment | This provider action cancels a shipment until the time when it's shipped. |
| FedEx Generate Return Shipping Label | This provider action generates the FedEx return label for a customer-initiated return. |
| FedEx Generate Return Drop Locations | This provider action fetches the available drop-off locations for a specific postal code. |
