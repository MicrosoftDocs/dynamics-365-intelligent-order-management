---
author: josaw1
description: This article describes how to enable timeline capabilities in Microsoft Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 03/21/2025
ms.custom: 
  - bap-template
ms.topic: article
ms.author: anvenkat

title: Enable timeline capabilities
---


# Enable timeline capabilities

[!include [banner](includes/banner.md)]

This article describes how to enable timeline capabilities on the **Sales order** and **Fulfillment order** pages in Microsoft Dynamics 365 Intelligent Order Management.

When you enable the timeline on the **Sales order** or **Fulfillment order** page, it lists all business events that the orchestration flow raises, in chronological order. It provides valuable insights into how a sales order or fulfillment order and its lines are processed. It also helps explain the current status of the sales order or fulfillment order.

## Enable timeline

To enable the timeline, follow these steps:

1. Go to **Settings** > **Advanced Settings**.
1. Expand **Settings**.
1. Select **Activity Feeds Configuration**.
1. On the ribbon, select **Refresh**.
1. Select **Entity Name Sales Order**.
1. On the ribbon, select **Activate**, and then confirm the activation.
1. When the message "You need to publish the related entity for form wall changes to take effect" appears, select **OK**.

> [!NOTE]
> You must clear the cache on your browser before the timeline can be populated with data.

When enabled, the timeline starts to list business events as the orchestration flow raises them, as shown in the following example image.

:::image type="content" source="media/timeline.png" alt-text="Screenshot of the timeline showing business events in chronological order.":::

## Additional resources

[Configure timeline](/dynamics365/customer-service/customer-service-hub-user-guide-timeline-admin)
