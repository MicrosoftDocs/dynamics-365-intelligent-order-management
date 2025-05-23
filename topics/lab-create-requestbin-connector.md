---
author: josaw1
description: This topic describes the steps required to create a RequestBin custom connector in Microsoft Dynamics 365 Intelligent Order Management.
ms.date: 03/21/2025
ms.custom: 
  - bap-template
ms.topic: how-to
ms.author: josaw

title: Create RequestBin custom connector

---

# Create RequestBin custom connector

[!include [banner](includes/banner.md)]

This topic describes the steps required to create a RequestBin custom connector in Microsoft Dynamics 365 Intelligent Order Management.

> [!NOTE]
> RequestBin is non-Microsoft third party software used to collect, inspect, and debug HTTP requests and webhooks. This lab uses it for demo purposes, please use it at your own discretion. 

## Create RequestBin account

To create a RequestBin account, follow these steps.

1. Go to RequestBin.com and select **Create Request Bin**.
1. You can choose to create a public bin, but if you want to keep your request bin long-term, sign in with one of the suggested authentication methods.
1. Once your RequestBin is set up, you should have a public endpoint URL in the format ``https://xxxxxxxxxxxxxxx.m.pipedream.net``. 

## Create custom connector

To create a custom connector, follow these steps.

1. Go to the [Power App Maker portal](https://make.powerapps.com) and navigate to the newly created solution **IOMLabProviders**.
1. Select **New \> Custom connector** and name it "RequestBin".
1. In the **Host** field, enter the public endpoint URL you obtained from RequestBin. Do not prepend ``https://`` to the URL. 
1. Select **Security**.
1. Select **Definition**.
1. Select **+ New action**. 
1. In the **General** dialog box, do the following:
    1. For **Summary**, enter "Create fulfillment order".
    1. For **Description**, enter "Create fulfillment order".
    1. For **Operation ID**, enter "CreateFulfillmentOrder".
    1. For **Visibility**, select **none**.
1. Under **Request**, select **Import from sample**.
1. In the **Import from sample** dialog box, do the following:
    1. For **Verb**, select **POST**.
    1. For **URL**, enter `https://<URL_FROM_REQUESTBIN>/CreateFulfillmentOrder`, where **\<URL\_FROM\_REQUESTBIN\>** is the public endpoint URL you obtained from RequestBin.
1. Select **Import**.
1. Select **+ New action**.
1. In the **General** dialog box, do the following:
    1. For **Summary**, enter "Create fulfillment order lines".
    1. For **Description**, enter "Create fulfillment order lines".
    1. For **Operation ID**, enter "CreateFulfillmentOrderLines".
    1. For **Visibility**, select **none**.
1. Under **Request**, select **Import from sample**.
1. In the **Import from sample** dialog box, do the following:
    1. For **Verb**, select **POST**.
    1. For **URL**, enter `https://<URL_FROM_REQUESTBIN>/CreateFulfillmentOrderLines`, where **\<URL\_FROM\_REQUESTBIN\>** is the public endpoint URL you obtained from RequestBin.
1. Select **Import**.
1. Select **Create connector**.


Next quick start lab step: [Create intake provider](lab-create-intake-provider.md)

