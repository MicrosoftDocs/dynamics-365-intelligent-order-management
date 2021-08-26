---
author: josaw1
description: 
ms.service: dynamics-365-intelligent-order-management
ms.date: 09/01/2021
ms.topic: how-to
ms.author: josaw

title: Create RequestBin custom connector

---

# Create RequestBin custom connector

[!include [banner](includes/banner.md)]

> [!NOTE]
> RequestBin is non-Microsoft third party software used to collect, inspect, and debug HTTP requests and webhooks. This lab uses it for demo purposes, please use it at your own discretion. 

## Create RequestBin account

-	Go to RequestBin.com and select **Create Request Bin**.
-	You can choose to create a public bin, but if you want to keep your request bin long-term, sign in with one of the suggested authentication methods.
-	Once your RequestBin is set up, you should have a public endpoint URL in the format ``https://xxxxxxxxxxxxxxx.m.pipedream.net``. 

## Create custom connector

-	On the Power App Maker Portal, go to the newly created solution **IOMLabProviders**.
-	Select **New\Custom connector** and name it "RequestBin".
-	In the **Host** field, enter the public endpoint URL you obtained from RequestBin. Do not prepend ``https://`` to the URL. 
-	Select **Security**.
-	Select **Definition**.
-	Select **+ New action**. 
-	For **Summary**, enter "Create fulfillment order."
-	For **Description**, enter "Create fulfillment order."
-	For **Operation ID**, enter "CreateFulfillmentOrder."
-	For **Visibility**, select **none**.
-	Under **Request**, select **Import from sample**.
-	For **Verb**, select **POST**.
-	For **URL**, enter the public endpoint URL you obtained from RequestBin, including ``https://``.
-	Select **Import**.
-	Select **Create connector**.

Next step: [Create IOMLabOrderIntakeProvider]()

