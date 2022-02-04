# Enable timeline on Fulfillment order page

[!include [banner](includes/banner.md)]


This document describes how to enable timeline capabilities on the **Fulfillment order** page in Dynamics 365 Intelligent Order Management. 

When the timeline is enabled on the **Fulfillment order** page, it will list all business events raised by the orchestration flow in chronological order. This can provide valuable insights into how a fulfillment order and its lines have been processed, and can also help explain the current status of the fulfillment order.

## Enable timeline

To enable the timeline on the **Fulfillment order** page, follow these steps.

1.	Go to **Settings** > **Advanced Settings**. 
2.	Expand **Settings**. 
3.	Select **Activity Feeds Configuration**.
4.	On the ribbon, select **Refresh**. 
5.	Select **Entity Name Fulfillment Order**. 
6.	On the ribbon, select **Activate**, and then confirm the activation.
7.	When the message “You will need to publish the related entity for form wall changes to take effect” appears, select **OK**.

> [!NOTE]
> You must clear the cache on your browser before the timeline can be populated with data.
 
## Additional resources

[Configure timeline](/dynamics365/customer-service/customer-service-hub-user-guide-timeline-admin)
