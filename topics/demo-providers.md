---
author: rikothap
description: This article describes demo providers in Microsoft Dynamics 365 Intelligent Order Management. It helps users ensure orders flow between Intelligent Order Management and other 3rd party providers.
ms.author: rikothap
ms.date: 10/17/2022
ms.topic: conceptual

title: Demo providers

---

# Demo providers for Dynamics 365 Intelligent Order Management

[!include [banner](includes/banner.md)]

Demo Providers are designed to help you see how orders flow between IOM (Dynamics 365 Intelligent Order Management) and its 3rd party connections. After setting things up, you will be able to generate a test order and monitor its status in IOM as it moves through each step of an orchestration flow from order validation all the way to fulfillment. These simulated providers include:
<ol>	Demo Ecommerce (generate an order)
<ol>	Demo Fulfillment (process and fulfill an order)
<ol>	Demo Inventory (update inventory system after fulfillment)
<br> Before you can start using Demo Providers, you will need to set them up in 4 steps:
<ol> Activate connections
<ol>	Publish policies
<ol>	Add providers
<ol>	Activate demo order flow

Setting up Demo Providers
1.	Activate connections: 
a.	From the IOM home page, select Settings, then click on Initial Connections
b.	Open each connection and wait for it to establish, confirmed by a green check, then click “Save and close”. 

Home->configure->Manage
