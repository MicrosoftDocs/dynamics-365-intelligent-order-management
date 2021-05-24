---
author: josaw1
description: This topic provides information about how to enable timeline capabilities In Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 05/25/2021
ms.topic: conceptual
ms.author: josaw

title: Enable timeline on Sales order form
---


# Enable timeline on Sales order form

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This document describes how to enable timeline capabilities on the **Sales order** form in Dynamics 365 Intelligent Order Management. 

When the timeline is enabled on the **Sales order** form, it will list all business events raised by the orchestration flow in chronological order, which can provide valuable insights into how a sales order and its lines have been processed, and can also help explain the current status of the sales order.

## Enable timeline

To enable the timeline on the **Sales order** form, follow these steps.

1.	Go to **Settings** > **Advanced Settings**. 
2.	Expand **Settings**. 
3.	Select **Activity Feeds Configuration**.
4.	On the ribbon, select **Refresh**. 
5.	Select **Entity Name Sales Order**. 
6.	On the ribbon, select **Activate**, and then confirm the activation.
7.	When the message “You will need to publish the related entity for form wall changes to take effect” appears, select **OK**.

> [!NOTE]
> You must clear the cache on your browser before the timeline can be populated with data.

Once enabled, the timeline should start to list business events as they are raised by the orchestration flow, as shown in the following example image. 

![Timeline of business events](media/timeline.png)

## Additional resources

[Configure timeline](/dynamics365/customer-service/customer-service-hub-user-guide-timeline-admin)
