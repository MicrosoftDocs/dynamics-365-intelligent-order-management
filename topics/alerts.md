---
title: Intelligent Order Management alerts
description: Learn about alerts functionality and use cases in Microsoft Dynamics 365 Intelligent Order Management.
author: derekkwanpm
ms.date: 01/27/2026
ms.custom: 
  - bap-template
ms.topic: article
ms.author: anvenkat
---

# Intelligent Order Management alerts

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

Time-sensitive and high-impact issues can get lost in a sea of business events. If you can't surface those issues in a structured and timely manner, they might lead to customer dissatisfaction and business disruption. Microsoft Dynamics 365 Intelligent Order Management provides alerts about business-critical events, so that you can act quickly when problems arise.

In this release, Intelligent Order Management has alerts for order statuses. For example, an order triggers an alert if the current date is three days before the requested delivery date of an order, but the order isn't yet sent to fulfillment.

This feature is in private preview. Your administrator must enable alerts in the **Administration settings** area. After enabling alerts, you can find them in the **Monitoring** section on the left menu.

:::image type="content" source="media/alerts_menu.png" alt-text="Screenshot of the monitoring section of the left menu.":::

## Create an alert

> [!NOTE]
> For the private preview, the solution doesn't include any prebuilt alerts. You must create alert configurations for alerts that you want to start to trigger.

1. On the left menu, in the **Monitoring** section, select **Alert Configuration** to open the **Active Alert Configurations** page.

    On the **Active Alert Configurations** page, the top menu bar (labeled "1" in the illustration) contains several buttons, including **New**. The grid (labeled "2") contains a list of current alert configurations. Double-tap (or double-click) any configuration in the list to open the configuration settings and make changes to the configuration.

    ![Screenshot of the top menu bar and grid on the Active Alert Configurations page.](media/alerts_config.png)

1. Select **New** on the menu bar to open the **New Alert Configuration** page.
1. Set the following fields:

    - **Name** – Enter a descriptive name for your configuration, so that you can easily identify it among the different configurations. For example, enter **Not delivered one day past requested date**.
    - **Owner** – By default, this field shows your name as the creator of the configuration. However, you can update the value as needed.
    - **Alert action** – Select one of the following values to specify the issue that triggers the alert:

        - Not sent to fulfillment
        - Not shipped

    - **Expected date** – Use this field in combination with the **Alert action** field. Specify the date on an order that triggers an alert. For this private preview release, the only available option is **Requested delivery date**. More options are added in upcoming releases.
    - **Time before expected** – Specify the number of days, hours, or minutes between the alert action and the expected date that causes an alert to trigger.

### Example

For example, configure the following alert settings:

- **Alert action:** Not sent to fulfillment
- **Expected date:** Requested delivery date
- **Time before expected:** Three days

In this case, any order that has a requested delivery date three days from now, but that isn't yet sent to fulfillment, triggers an alert.

On the **Active Alerts** page, view all the alert configurations that you created. You can also select any existing configuration and edit the settings as needed.

## View alerts

- On the left menu, in the **Monitoring** section, select **Alerts** to open the **Active Alerts** list.

The **Active Alerts** page provides a list of current orders that match the criteria for your alert configurations. On this page, you can view any specific order that's under alert, change the status of the alert, and access the configuration that's triggering the alert.

> [!NOTE]
> Alerts are a list of orders that are under alert. Alert configurations are a list of the configurations that you created to generate alerts.

Each row in the grid represents an order that's currently under alert. Here's an explanation of the grid columns:

- **Order** – This column contains a link to the order in Intelligent Order Management that's currently under alert.
- **Alert Configuration** – This column contains a link to the configuration that's triggering the alert.
- **Status Reason** – This column contains the status of the alert. The following alert statuses are used:

  - Active
  - In progress
  - On hold
  - Inactive
  - Resolved

    A status of **Active** indicates that the alert is active. The order itself might have a status of **In fulfillment** or **Sent for delivery**. The purpose of the alert status is to enable you to update the status of an alert if you already took action on the order. For example, if an alert is triggered because an order is delayed, and you expedited the order for delivery, you can change the alert status to **Resolved**. Therefore, you can use the list of alerts in the grid as a to-do list. You can view which orders are under alert, and then check them off as you take action on the orders to resolve the alerts.

:::image type="content" source="media/alerts_list.png" alt-text="Screenshot of the alert list on the Active Alerts page.":::

## Update an alert

You can change the alert status for any row on the **Active Alerts** page. (The numbered steps correspond to the numbered callouts in the illustration.)

1. In the row for the alert that you want to update, hover over the area to the left of the **Order** column, and then select the checkbox to select the row. When you select a row, the top menu bar changes.
1. To edit details of the alert, including the alert status, select **Edit** on the menu bar to open the **Alert edit** page. This page shows alert details such as the owner of the alert, the order that's under alert, and the configuration. You can make the following changes:

    - In the **Owner** field, select someone else in your organization as the owner of the alert.
    - In the **Alert status** field, select **Active**, **In Progress**, **On Hold**, or **Resolved** as the alert status.
    - Select **Deactivate** on the menu bar to deactivate the alert.

1. To quickly change the alert status, select **Resolve**, **Activate**, or **Deactivate** on the menu bar to update the **Status Reason** value for the row.

![Screenshot of updating an alert on the Active Alerts page.](media/alerts_status.png)

## Other notes

Future releases include some out-of-box alerts, in-app notifications, and other alert types, such as inventory alerts and data anomalies.

During the private preview phase, some resource limitations exist. If an alert configuration triggers more than 5,000 orders at a time, the alert fails. Although this situation rarely occurs, you can help safeguard against it by ensuring that the **Time before expected** value is lower than the **Days before expected date** value. For example, the number of orders that aren't sent to delivery 10 days before the expected delivery date is greater than the number two days before the expected delivery date. Therefore, the limit of 5,000 orders is much less likely to be reached two days before the expected delivery date.
