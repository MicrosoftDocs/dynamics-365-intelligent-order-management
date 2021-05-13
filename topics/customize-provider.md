---
author: josaw1
description: This topic provides instructions on how to customize and out-of-box provider in Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 05/17/2021
ms.topic: conceptual
ms.author: josaw

title: Customize an out-of-box provider

---


# Customize an out-of-box provider

[!include [banner](includes/banner.md)]


One option for customizing a provider for Dynamics 365 Intelligent Order Management is to modify a provider that comes out of the box with Intelligent Order Management. Choose this option if:

-   You have custom fields or need to change the way fields are mapped from an external service to Intelligent Order Management. In this case, you'll need to modify the provider transformation.

-   You want to change what happens when a specific action is triggered in the orchestration designer. In this case, you'll need to modify the provider action.

If this option isn't adequate for your needs, you can [create a new provider](create-new-provider.md)

## Modify the provider transformation

To customize an out-of-box provider, you need to modify the transformation for the provider. Intelligent Order Management uses Power Query Online for data transformations. For information about Power Query online, see [What is Power Query? and](https://docs.microsoft.com/power-query/power-query-what-is-power-query) [Power Query M formula language reference.](https://docs.microsoft.com/powerquery-m/)

To modify the provider transformation, complete the following steps.

1.  Go to **Providers > Installed.**

2.  Find and select the provider that you want to change.

3.  Go to the **Transformations** tab.

4.  Select the transformation that you want to change.

5.  Modify the transformation by doing one of the following.

    1.  Edit the transformation directly by changing the M formula in the **Transformation** field.

    2.  Select **Edit in PowerQuery** to open the PowerQuery editor and change the mapping.
