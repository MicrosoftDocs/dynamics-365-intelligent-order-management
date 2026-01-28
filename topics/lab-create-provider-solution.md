---
author: josaw1
description: This article describes the steps required to create a new provider solution package in Microsoft Dynamics 365 Intelligent Order Management.
ms.date: 01/28/2026
ms.custom: 
  - bap-template
ms.topic: how-to
ms.author: anvenkat
title: Create a new provider solution package

---

# Create a new provider solution package

[!include [banner](includes/banner.md)]

This article describes the steps required to create a new provider solution package in Microsoft Dynamics 365 Intelligent Order Management.

It is recommended to have one provider per solution, but multiple providers can be included in the same solution. This is the solution that can be shared and will be installed on Intelligent Order Management environments.

## Create a new provider solution

To create a new provider solution, follow these steps:

1. Go to the [Power App Maker Portal](https://make.powerapps.com) and sign in with your Intelligent Order Management credentials. 
1. Go to **Solutions**.
1. Select **New solution**.
1. For **Display name**, enter "IOM LabProviders".
1. For **Name**, enter "IOM LabProviders".
1. For **Publisher**, select **CDS Default Publisher**.
1. For **Version**, enter "1.0.0.0".

   :::image type="content" source="media/lab_new_solution.png" alt-text="Screenshot of the new solution properties.":::

Next quick start lab step: [Create RequestBin custom connector](lab-create-requestbin-connector.md).
