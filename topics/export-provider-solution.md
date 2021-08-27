---
author: josaw1
description: Export provider solution DESCRIPTION TBD
ms.service: dynamics-365-intelligent-order-management
ms.date: 09/01/2021
ms.topic: how-to
ms.author: josaw

title: Export provider solution

---

# Export provider solution

[!include [banner](includes/banner.md)]

You should now see the following components in your provider solution.

![Provider solution components](./media/provider-solution-components.PNG)

For instructions on exporting your solution, see [Export solutions](/powerapps/maker/data-platform/export-solutions).

## Clean up

1. On the Power App Maker portal, go to **Solutions \> default solution** and filter on **Cloud flow**.
1. Stop the following cloud flows created to initialize provider definition logic definition. 
    - IOM Lab Order Intake Message Request Handler.
    - IOM Lab Send To Fulfillment (Outlook).
    - IOM Lab Send To Fulfillment (RequestBin).

> [!NOTE]
> New flows are generated when instantiating a provider. If these flows are not turned off, more than the expected outgoing payload will be sent.

Next step: [Onboard provider instance](lab-onboard-provider.md)
