---
author: josaw1
description: This topic describes the steps required to export a provider solution in Microsoft Dynamics 365 Intelligent Order Management.
ms.date: 01/28/2026
ms.custom: 
  - bap-template
ms.topic: how-to
ms.author: anvenkat
title: Export provider solution

---

# Export provider solution

[!include [banner](includes/banner.md)]

This topic describes the steps required to export a provider solution in Microsoft Dynamics 365 Intelligent Order Management.

At this stage of the quick start lab you should now see the following components in your provider solution.

:::image type="content" source="media/lab_export_components.png" alt-text="Screenshot of the provider solution components.":::

For instructions on exporting your solution, see [Export solutions](/powerapps/maker/data-platform/export-solutions).

## Clean up after export

To clean up after export, follow these steps:

1. Go to the [Power App Maker portal](https://make.powerapps.com), navigate to **Solutions \> default solution**, and then filter on **Cloud flow**.
1. Stop the following cloud flows created to initialize provider definition logic definition. 
    - IOM Lab Order Intake Message Request Handler.
    - IOM Lab Send To Fulfillment (Outlook).
    - IOM Lab Send To Fulfillment (RequestBin).

> [!NOTE]
> New flows are generated when instantiating a provider. If these flows are not turned off, more than the expected outgoing payload will be sent.

Next quick start lab step: [Onboard provider instance](lab-onboard-provider.md)
