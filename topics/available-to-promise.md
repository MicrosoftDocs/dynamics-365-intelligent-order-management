---
author: sumanic
description: Learn how to set up available-to-promise (ATP) capabilities in Microsoft Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 01/27/2026
ms.custom: 
  - bap-template
ms.topic: overview
ms.author: sumanic
title: Set up available-to-promise inventory capabilities

---

# Set up available-to-promise inventory capabilities

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This article describes how to set up available-to-promise (ATP) capabilities in Microsoft Dynamics 365 Intelligent Order Management.

ATP is the projected amount of inventory that will be available in the upcoming period and that can be promised for customer orders. Use of this calculation can greatly increase your order fulfillment capability.

For many manufacturers, retailers, and sellers, it isn't enough to know what inventory is currently on hand. They must have full visibility into future availability. This future availability should consider future supply, future demand, and ATP.

## Prerequisites

The following prerequisites must be met before you can set up and use ATP capabilities in Intelligent Order Management:

- The Dynamics 365 Inventory Visibility provider must be installed. For installation instructions, see [Set up Inventory Visibility provider](set-up-inventory-visibility-provider.md).
- You must submit on-hand change schedule updates to the Dynamics 365 Inventory Visibility provider to confirm that the dates are within the period that is defined by the **Schedule period** setting.

The following table lists the details of the APIs that are used to submit an on-hand schedule change request. These APIs are available from the Microsoft Dynamics 365 Supply Chain Management Inventory visibility add-in and in Intelligent Order Management. For more information, see [Dynamics 365 Inventory Services](/dynamics365/supply-chain/inventory/inventory-visibility-available-to-promise).

| Path | Method | Description |
|---|---|---|
| /api/environment/{environmentId}/onhand/changeschedule | POST | Create one scheduled on-hand change. |
| /api/environment/{environmentId}/onhand/changeschedule/bulk | POST | Create multiple scheduled on-hand changes. |

## Set up and enable ATP features

Before you can use ATP, you must complete one or more of the following key setup procedures.

### Enable the ATP settings

First, you should enable the ATP settings in Intelligent Order Management.

1. In Intelligent Order Management, go to **Settings**. 
1. In the left navigation, under **Inventory settings**, select **Index and Reservation**.
1. On the **Feature Management & Settings** tab, turn on the **OnHandChangeSchedule** option.

:::image type="content" source="media/ATP.png" alt-text="Screenshot of the OnHandChangeSchedule option turned on in Feature Management and Settings.":::

### Define the calculated measure for the ATP settings

Next, you must define the calculated measure for the ATP settings.

The ATP calculated measure is a predefined calculated measure that is typically used to find the on-hand quantity that is currently available. The supply quantity is the sum of quantities for physical measures that have an addition modifier type. The demand quantity is the sum of quantities for physical measures that have a subtraction modifier type.

You can add multiple calculated measures to calculate multiple ATP quantities. However, the total number of distinct physical measures across all ATP calculated measures should be less than nine.

> [!NOTE]
> A calculated measure is a composition of physical measures. A calculated measure formula can include only physical measures without duplicates. It can't include calculated measures.

To define the calculated measure for the ATP settings, follow these steps:

1. Go to **Settings**.
1. In the left navigation, under **Inventory settings**, select **Index and Reservation**.
1. On the **ATP Setting** tab, in the **Data Source** field, select the data source.
1. In the **Calculated Measure** field, select the calculated measure for the data source.
1. In the **Schedule Period** field, enter the number of days for the schedule period. Currently, a maximum value of **7** is supported.
1. Select **Save**.

:::image type="content" source="media/ATPSetting.png" alt-text="Screenshot of the calculated measure defined for the ATP settings.":::

#### Calculated measure examples

For example, you first set up the **On-hand-available** calculated measure:

**On-hand-available** = (PhysicalInvent + OnHand + Unrestricted + QualityInspection + Inbound) – (ReservPhysical + SoftReservePhysical + Outbound)

The sum (PhysicalInvent + OnHand + Unrestricted + QualityInspection + Inbound) represents supply, and the sum (ReservPhysical + SoftReservePhysical + Outbound) represents demand. Therefore, the calculated measure can be understood in the following simplified way: **On-hand-available** = Supply – Demand.

You can then set up another calculated measure, **On-hand-physical**, to calculate the on-hand physical ATP quantity:

**On-hand-physical** = (PhysicalInvent + OnHand + Unrestricted + QualityInspection + Inbound) – Outbound

Between these two ATP calculated measures, eight distinct physical measures are used: PhysicalInvent, OnHand, Unrestricted, QualityInspection, Inbound, ReservPhysical, SoftReservePhysical, and Outbound.

For more information about calculated measures, see [Calculated measures](/dynamics365/supply-chain/inventory/inventory-visibility-configuration#calculated-measures).

### Define the calculated measure mapping

Next, you must define the Intelligent Order Management calculated measure mapping.

1. Go to **Settings**.
1. In the left navigation, under **Inventory settings**, select **Index and Reservation**.
1. On the **Intelligent Order Management Mappings** tab, in the **Set Calculated Measure Mappings** section, select the data source that you selected in the calculated measure for the ATP settings.
1. In the **Base Measure** field, select **atponhand**.

    > [!NOTE]
    > The base measure is a predefined measure in Intelligent Order Management that is called from the inventory check actions in orchestration. This base measure mapping is maintained by using the calculated measure for the ATP settings.

1. In the **Calculated Measure** field, select the calculated measure that you selected in the calculated measure for the ATP settings.

:::image type="content" source="media/IOMmapping.png" alt-text="Screenshot of the calculated measure mapping defined in Intelligent Order Management Mappings.":::

## Run a sample transaction with ATP check

Intelligent Order Management can perform inventory checks as an independent provider action. If a fulfillment source is assigned to the sales order lines via a policy or manual order creation, you can orchestrate the order to perform independent inventory checks. If the previously described settings are enabled, the system checks ATP dates and determine the **Material Availability Date** and **Estimated Shipment Date** values on the sales order line.

> [!NOTE]
> Inventory checks occur as part of fulfillment and returns optimization. The sales order lines are updated accordingly, based on the ATP settings.

The following illustration shows an example of an orchestration journey that has a policy-based fulfillment assignment.

:::image type="content" source="media/SampleOrch.png" alt-text="Screenshot of a sample orchestration journey with policy-based fulfillment assignment.":::

The following provider actions are available as part of Intelligent Order Management. They check ATP when the ATP settings are enabled.

| Provider action | Description |
|---|---|
| Send fulfillment process request | This provider action checks for inventory availability of the assigned fulfillment source on the sales order line. If the ATP settings are enabled, it also checks for promise dates. This action also generates the fulfillment order, and updates the **Inventory Availability Date** and **Estimated Ship Date** values on the sales order line. |
| Send to fulfillment optimization | This provider action determines the best fulfillment location for a sales order line, based on an inventory check. It also generates the fulfillment order, and updates the **Inventory Availability Date** and **Estimated Ship Date** values on the sales order line. |

The example in the following illustration highlights the **Estimated Ship Date** and **Inventory Availability Date** values on the sales order line after the preceding order orchestration runs. In this example, the inventory check found no inventory and has backordered the lines.

:::image type="content" source="media/BackorderHold.png" alt-text="Screenshot of the results of an order orchestration run showing Estimated Ship Date and Inventory Availability Date values.":::

## API URLs

As a part of the ATP feature capabilities, a set of API URLs is available from Intelligent Order Management. These URLs are also available from Supply Chain Management. They can be directly called by third-party enterprise resource planning (ERP), commerce, or supplier systems for inventory queries that have ATP capabilities. For more information, see [Submit change schedules, change events, and ATP queries through the API](/dynamics365/supply-chain/inventory/inventory-visibility-available-to-promise#api-urls). 

The following example shows a payload for the inventory query to call various services from Intelligent Order Management.

```JSON
{
    "API": "OnHandQuery",
    "Payload": "{\"filters\": {\"OrganizationId\": [\"{{orgid}}\"],\"ProductId\": [\"ACSC-SP\"],\"SiteId\": [\"default\",\"1\"],\"LocationId\":    [\"120\"]},\"groupByValues\": [],\"returnNegative\": true }"]
}
```

The associated path resembles the following example.

`{{orgurl}}/api/data/v9.1/msdyn_IOMInventoryAPICall`

The request and response for these payloads resemble what is available from Supply Chain Management. The following table shows the mapping between the Intelligent Order Management APIs and Dynamics 365 Inventory Visibility APIs. It also provides links to the appropriate documentation.

| Intelligent Order Management API name | Dynamics 365 Inventory Visibility API | Method | Description | Documentation |
|---|---|---|---|---|
| OnHandQuery | /api/environment/{environmentId}/onhand/indexquery | POST | Query inventory availability. | [Query inventory availability](/dynamics365/supply-chain/inventory/inventory-visibility-api#query-with-post-method) |
| OnHandDelta | /api/environment/{environmentId}/onhand | GET | Query on-hand delta. | [Create one on-hand change event](/dynamics365/supply-chain/inventory/inventory-visibility-api#create-one-onhand-change-event) |
| OnHandDelta\_Bulk | /api/environment/{environmentId}/onhand/bulk | POST | Create multiple change events. | [Create multiple change events](/dynamics365/supply-chain/inventory/inventory-visibility-api#create-multiple-onhand-change-events) |
| OnHandChangeSchedule | /api/environment/{environmentId}/onhand/changeschedule | POST | Create on-hand change schedule. | [Create one on-hand change schedule](/dynamics365/supply-chain/inventory/inventory-visibility-available-to-promise#create-one-on-hand-change-schedule) |
| OnHandChangeSchedule\_Bulk | /api/environment/{environmentId}/onhand/changeschedule/bulk | POST | Create multiple on-hand change schedules. | [Create multiple on-hand change schedules](/dynamics365/supply-chain/inventory/inventory-visibility-available-to-promise#create-multiple-on-hand-change-schedules) |
