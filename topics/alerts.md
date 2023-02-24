---
title: Intelligent Order Management alerts
description: This article provides an overview about alerts functionality and use cases in Microsoft Dynamics 365 Intelligent Order Management.
author: derekkwanpm
ms.date: 02/24/2023
ms.topic: conceptual
ms.author: derekkwan
ms.custom: bap-template
---


# Intelligent Order Management alerts

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

Microsoft Dynamics 365 Intelligent Order Management provides alerts to business critical events so you can act quickly when issues arise. Time-sensitive and high-impact problems can get buried in a sea of business events. With no way to surface those issues in a structured and timely manner, they'll get lost, leading to potential customer dissatisfaction and business disruption. 

With this release, Intelligent Order Management now has alerts for order statuses. For example, an order can trigger an alert if it's three days before the requested delivery date of an order, and the order hasn't been sent to fulfillment yet. 

This feature is still in private preview and your administrator will need to enable alerts in the **Administration settings** area. After alerts are enabled, you can find them in the **Monitoring** group.

![Screenshot of the alerts navigation menu.](/topics/media/alerts_menu.png)

## Creating alerts

> [!Note]
> For private preview, no alerts are pre-built out-of-the-box. You will need to create alert configurations for alerts that you want to start triggering. Select **Alert configuration** in the left menu to open the **Active Alert configuration** page.

![Screenshot of the Active Alert configuration page.](/topics/media/alerts_config.png)

On the **Active Alert configurations** page:

- (1) The top menu includes several functions, including **New**.
- (2) The table contains a list of current alerts configurations. Double-click any individual configuration in the list to open the configuration settings and make changes to the configuration.

When you select **New**, the **New Alert Configuration** page opens with the following options:

- **Name**: Give your configuration a descriptive name so that you can easily identify different configurations. For example, "Not delivered one day past requested date".
- **Owner**: This field value defaults with your name as the creator of the configuration. You can update this field as needed.
- **Alert action**: This is the problematic action that will trigger the alert. There are two options to select from: 

    - **Not sent to fulfillment**
    - **Not shipped**

- **Expected date**: When combined with an alert action, this is the date on an order that triggers an alert. For this private preview release, the only option is **Requested delivery date**. More options will be added in upcoming releases.
- **Time before expected**: The number of days, hours, or minutes between the alert action and the expected date that will cause an alert to trigger.

### Example
For example, if the following alert settings have been configured:

- Alert action: Not sent to fulfillment
- Expected date: Requested delivery date
- Time before expected = 3 days

Any order with a requested delivery date three days from now, that hasn't been sent to fulfillment triggers an alert. 

You can view all the alert configurations that were created on the **Active Alerts** page. You can also select any existing configuration and edit the settings as needed.

## View alerts

Select **Alerts** on the left menu in the **Monitoring** to open the **Active Alerts** list page. This page provides a list of current orders that match the criteria for your alert's configurations. On this page, you can view any specific order that is under alert, change the status of the alert, as well as access the configuration that is triggering the alert.

> [!Note]
> Alerts are a list of orders that are under alert. Alert configurations are a list of the configurations you created to generate alerts.

Each row in the **Alerts** list is an order that is currently under alert.

![Screenshot of the Alerts list.](/topics/media/alerts_list.png)

- The **Order** column contains a link to the actual order in Intelligent Order Management that is currently under alert.
- The **Alert Configuration** column contains a link to the actual configuration that is triggering the alert.
- The **Status Reason** column contains the status of the alert. This means if the status is **Active**, the alert is active. The order might have a status of **In fulfillment**, or **Sent for delivery**. The intention of the alert status is to allow you to update the status of an alert if you've already taken an action on the order. For example, if an order is delayed and an alert is triggered, and you expedited the order for delivery, you can change the alert status to resolved. Use this list of alerts like a to-do list. View which orders are under alert, and then check them off as you take actions on the order to resolve. The options for alert statuses are:

    - Active
    - In progress
    - On hold
    - Inactive
    - Resolved
  
## Update an alert
  
You can change the alert status by selecting any row in the **Active alerts** page.

![Screenshot of Active Alerts statuses.](/topics/media/alerts_status.png)

- (1) Hovering to the left of the **Order** column displays a radio button. Select the radio button to select that row.
- (2) The top menu changes when a row is selected. The **Edit** button lets you edit the alert.
- (3) Quick action buttons, including **Resolve**, **Activate**, and **Deactivate** are available to update the **Status Reason** for the alert. 

If you select **Edit**, the **Alert edit** page opens with the following options:

- Alert details such as **Owner**, **Order**, and **Configuration** are displayed. The owner of the alert can be changed to someone else in your organization.
- **Alert status** is a drop-down list that can be changed to **Active**, **In Progress**, **On Hold**, or **Resolved**. If an alert needs to be deactivated, select **Deactivate** on the top menu.

## Other notes

Future releases will have some out-of-the-box alerts, in-app notifications, as well as other alert types like inventory alerts and data anomalies.

During the private preview phase, there are some resource limitations. If an alert configuration triggers more than 5000 orders at a time, the alert will fail. While this should rarely happen, some safeguards to take are to ensure the **Time before expected** is lower the **Days before expected date** setting. For example, there will be many more orders that haven't been sent to delivery ten days before the expected delivery date, compared to two days before the expected delivery date. Two days would be much less likely to hit 5000 order limit.
