---
author: josaw1
description: This article describes the steps required to create policies in Microsoft Dynamics 365 Intelligent Order Management.
ms.date: 01/28/2026
ms.custom: 
  - bap-template
ms.topic: how-to
ms.author: anvenkat
title: Create policies

---

# Create policies

[!include [banner](includes/banner.md)]

This article describes the steps required to create policies in Microsoft Dynamics 365 Intelligent Order Management.

## Create new header validation policy

To create a new header validation policy, follow these steps:

1. Go to **Orchestration \> Policies** and select **New**.
1. For **Policy Name**, enter "Order header validation policy".
1. For **Policy Type**, enter "Execution Policy".
1. For **Policy Criticality**, enter "Critical".
1. For **Status**, enter "Unpublished".
1. For **Associated Entity**, enter "Order".
1. Select **Save**.

## Create new order header validation policy rule

To create new order header validation policy rule, follow these steps:

1. On the order header validation policy form, select **New Rule**.
1. For **Rule Name**, enter "ShipToCountry - US".
1. For **Rule definition**:
    1. In the first field, select **Ship to Country/Region**.
    1. In the second field, select **Equals**.
    1. In the third field, select **US**.
1. For **Policy**, enter or select "Order header validation policy".

   :::image type="content" source="media/lab_order_header_validation_rule.png" alt-text="Screenshot of the order header validation rule.":::

1. Select **Save & close**.

## Publish the header validation policy

To publish the header validation policy, follow these steps:

1. Go to the order header validation policy you created. You should be on this screen already if you followed the above steps.
1. Select **Publish**.

## Create new line validation policy

To create a new line validation policy, follow these steps:

1. Go to **Orchestration \> Policies** and select **New**.
1. For **Policy Name**, enter "Order line validation policy".
1. For **Policy Type**, enter "Execution Policy".
1. For **Policy Criticality**, enter "Critical".
1. For **Status**, enter "Unpublished".
1. For **Associated Entity**, enter "Order Product".
1. Select **Save**.

## Create new order line validation policy rule

To create a new order line validation policy rule, follow these steps:

1. On the order line validation policy form, select **New Rule**.
1. Under **Condition**, for **Rule Name**, enter "Min quantity".
1. For **Rule definition**:
    1. In the first field, select **Quantity**.
    1. In the second field, select **Is greater than or equal to**.
    1. In the third field, enter or select **5**.
1. Under **Action**, set the **Add Action** value to **No**.

   :::image type="content" source="media/lab_order_line_validation_rule.png" alt-text="Screenshot of the order line validation rule.":::

1. Select **Save and close**.

## Publish the line validation policy

To publish the line validation policy, follow these steps:

1. Go to the order line validation policy you created. You should be on this screen already if you followed the above steps.
1. Select **Publish**.

## Create simple fulfillment assignment policy

To create a simple fulfillment assignment policy, follow these steps:

1. Go to **Orchestration \> Policies** and select **New**.
1. For **Policy Name**, enter "Simple fulfillment assignment policy".
1. For **Policy Type**, enter "Execution Policy".
1. For **Policy Criticality**, enter "Information".
1. For **Status**, enter "Unpublished".
1. For **Associated Entity**, enter "Order Product".
1. Select **Save**.

## Create new simple fulfillment assignment policy rule for Seattle store

To create a new simple fulfillment assignment policy rule for the Seattle store, follow these steps:

1. On the simple fulfillment assignment policy form, select **New Rule**.
1. Under **Condition**, for **Rule Name**, enter "Assignment rule- Seattle".
1. For **Rule definition**:
    1. In the first field, select **Quantity**.
    1. In the second field, select **Is greater than or equal to**.
    1. In the third field, enter or select **100**.
1. Under **Action**, set the **Add Action** value to **Yes**.
    1. In the first field, select **Fulfillment Source**.
    1. In the second field, select **Set Value**.
    1. In the third field, enter or select **Seattle store**.

   :::image type="content" source="media/lab_assignment_rule_seattle.png" alt-text="Screenshot of the assignment rule for Seattle.":::

1. Select **Save and close**.

## Create new simple fulfillment assignment policy rule for Chicago store

To create a new simple fulfillment assignment policy rule for the Chicago store, follow these steps:

1. On the simple fulfillment assignment policy form, select **New Rule**.
1. Under **Condition**, for **Rule Name**, enter "Assignment rule- Chicago".
1. For **Rule definition**:
    1. In the first field, select **Quantity**.
    1. In the second field, select **Is less than**.
    1. In the third field, enter or select **100**.
1. Under **Action**, set the **Add Action** value to **Yes**.
    1. In the first field, select **Fulfillment Source**.
    1. In the second field, select **Set Value**.
    1. In the third field, enter or select **Chicago store**.
:::image type="content" source="media/lab_assignment_rule_chicago.png" alt-text="Screenshot of the assignment rule for Chicago.":::

1. Select **Save and close**.

## Publish simple fulfillment assignment policy

To publish the simple fulfillment assignment policy, follow these steps:

1. Go to the simple fulfillment assignment policy you created. You should be on this screen already if you followed the above steps.
1. Select **Publish**.

## Create filter policy for Seattle store

To create a filter policy for the Seattle store, follow these steps:

1. Go to **Orchestration \> Policies** and select **New**.
1. For **Policy Name**, enter "Fulfillment filter policy - Seattle".
1. For **Policy Type**, enter "Filter Policy".
1. For **Policy Criticality**, enter "Information".
1. For **Status**, enter "Unpublished".
1. For **Associated Entity**, enter "Fulfillment Order".
1. Select **Save**.

## Create new filter rule for Seattle store

To create a new filter rule for the Seattle store, follow these steps:

1. On the Fulfillment filter policy - Seattle form, select **New Rule**.
1. Under **Condition**, for **Rule Name**, enter "Min quantity".
1. For **Rule definition**:
    1. In the first field, select **Fulfillment Source**.
    1. In the second field, select **Equals**.
    1. In the third field, enter or select **Seattle store**.
1. Under **Action**, set the **Add Action** value to **No**.

   :::image type="content" source="media/lab_filter_rule_seattle.png" alt-text="Screenshot of the filter rule for Seattle.":::

1. Select **Save and close**.

## Publish filter policy for Seattle store

To publish the filter policy for the Seattle store, follow these steps:

1. Go to the Seattle filter policy you created. You should be on this screen already if you followed the above steps.
1. Select **Publish**.

## Create filter policy for Chicago store

To create a filter policy for the Chicago store, follow these steps:

1. Go to **Orchestration \> Policies** and select **New**.
1. For **Policy Name**, enter "Fulfillment filter policy - Chicago".
1. For **Policy Type**, enter "Filter Policy".
1. For **Policy Criticality**, enter "Information".
1. For **Status**, enter "Unpublished".
1. For **Associated Entity**, enter "Fulfillment Order".
1. Select **Save**.

## Create new filter rule for Chicago store

To create a new filter rule for the Chicago store, follow these steps:

1. On the **Fulfillment filter policy - Chicago** form, select **New Rule**.
1. Under **Condition**, for **Rule Name**, enter "Min quantity".
1. For **Rule definition**:
    1. In the first field, select **Fulfillment Source**.
    1. In the second field, select **Equals**.
    1. In the third field, enter or select **Chicago store**.
1. Under **Action**, set the **Add Action** value to **No**.

   :::image type="content" source="media/lab_filter_rule_chicago.png" alt-text="Screenshot of the filter rule for Chicago.":::

1. Select **Save and close**.

## Publish filter policy for Chicago store

To publish the filter policy for the Chicago store, follow these steps:

1. Go to the Chicago filter policy you created. You should be on this screen already if you followed the above steps.
1. Select **Publish**.

If you've followed along, you should now see the transpiled Power Automate cloud flows as shown in the following illustration.

:::image type="content" source="media/lab_create_policies.png" alt-text="Screenshot of the transpiled Power Automate cloud flows for policies in Intelligent Order Management.":::

## Add input event to action type

To add an input event to an action type, follow these steps:

1. Go to **Providers \> Action Types**.
1. Select **Policy Based Fulfillment Determination**.
1. Select **+ New IOM Action Type Input Business Event**.
1. For **Name**, enter "Validation of Order Lines has Succeeded".
1. For **Action Type**, enter "Policy Based Fulfillment Determination".
1. For **Business Event Definition**, enter "Validation of Order Lines has Succeeded".
1. Select **Save**.

Next quick start lab step: [Create order orchestration](lab-create-order-orch.md)
