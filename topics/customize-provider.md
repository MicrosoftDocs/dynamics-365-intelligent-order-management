---
author: josaw1
description: Learn how to customize and out-of-box provider in Dynamics 365 Intelligent Order Management.
ms.date: 01/27/2026
ms.custom: 
  - bap-template
ms.topic: how-to
ms.author: anvenkat
title: Customize an out-of-box provider
---


# Customize an out-of-box provider

[!include [banner](includes/banner.md)]

You can customize a provider for Dynamics 365 Intelligent Order Management by modifying a provider that comes out of the box with Intelligent Order Management. Choose this option if:

- You need custom fields or want to change the way fields are mapped from an external service to Intelligent Order Management. In this case, modify the provider transformation.

- You want to change what happens when a specific action is triggered in the orchestration designer. In this case, modify the provider action.

If this option doesn't meet your needs, you can [create a new provider](create-new-provider.md).

## Modify the provider transformation

To customize a built-in provider, modify the transformation for the provider. Intelligent Order Management uses Power Query Online for data transformations. For more information about Power Query Online, see [What is Power Query?](/power-query/power-query-what-is-power-query) and [Power Query M formula language reference.](/powerquery-m/)

To modify the provider transformation, complete the following steps.

1. Go to **Providers > Installed**.

1. Find and select the provider that you want to change.

1. Go to the **Transformations** tab.

1. Select the transformation that you want to change.

1. Modify the transformation by doing one of the following steps.

    1. Edit the transformation directly by changing the M formula in the **Transformation** field.

    1. Select **Edit in PowerQuery** to open the PowerQuery editor and change the mapping.
