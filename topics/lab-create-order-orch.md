---
author: josaw1
description: 
ms.service: dynamics-365-intelligent-order-management
ms.date: 09/01/2021
ms.topic: how-to
ms.author: josaw

title: Create order orchestration

---

# Create order orchestration

[!include [banner](includes/banner.md)]

## Add the Validate order header tile

-	Go to **Orchestration \> Flows** and select **New**.
-	Enter a name for your new flow, and then select **Save**.
-	Select the plus symbol ("+") and then add the **Validate order header** tile.
-	For **Name**, enter "Order header validation."
-	For **Action Type**, enter "Order Validation."
-	For **Input Events**, enter "New Order."
-	For **Execution Policies**, enter "Order header validation policy."
-	Select **Save**.

## Add the Validate order header tile

-	Go to **Orchestration \> Flows** and select **New**.
-	Select the plus symbol ("+") and then add the **Validate order line** tile.
-	For **Name**, enter "Order line validation."
- For **Action Type**, enter "Order Line Validation."
-	For **Input Events**, enter "Validation of Order Header has Succeeded."
-	Select **Save**.

## Add a Custom tile

-	Go to **Orchestration \> Flows** and select **New**.
-	Select the plus symbol ("+") and then add a **Custom** tile.
-	For **Name**, enter "Simple fulfillment determination."
- For **Action Type**, enter "Policy Based Fulfillment Determination."
-	For **Input Events**, enter "Validation of Order Lines has Succeeded."
- For **Execution Policies**, enter "Simple fulfillment assignment policy."
- Select **Save**.

## Add a Splitter tile

-	Go to **Orchestration \> Flows** and select **New**.
-	Select the plus symbol ("+") and then add a **Splitter** tile.
-	For **Name**, enter "Fulfillment split."
- For the two **Splitter Settings** fields, enter "Seattle" and "Chicago" respectively.
- Select **Save**.

## Add a Send to fulfillment tile under Seattle branch

1. Go to **Orchestration \> Flows** and select **New**.
1. Under the **Seattle** branch, select the plus symbol ("+") and then add a **Send to fulfillment** tile.
1. For **Name**, enter "Send to Seattle."
1. For **Action Type**, enter "Send to Fulfillment."
1. For **Input Events**, enter "Creation of Fulfillment Order has Succeeded."
1. For **Provider Action**, enter "IOM Lab Send to Fulfillment (Outlook)."
1. For **Filter Policy**, enter "Fulfillment filter policy - Seattle."
1. Select **Save**.



## Add a Send to fulfillment tile under Chicago branch

1. Go to **Orchestration \> Flows** and select **New**.
1. Under the **Chicago** branch, select the plus symbol ("+") and then add a **Send to fulfillment** tile.
1. For **Name**, enter "Send to Chicago."
1. For **Action Type**, enter "Send to Fulfillment."
1. For **Input Events**, enter "Creation of Fulfillment Order has Succeeded."
1. For **Provider Action**, enter "IOM Lab Send to Fulfillment (RequestBin)."
1. For **Filter Policy**, enter "Fulfillment filter policy - Chicago."
1. Select **Save**.

## Publish the orchestration flow

After you are done creating the order orchestration flow, select **Publish** to publish the flow. 

If you've followed along, you should see the transpiled Power Automate cloud flows as shown in the following illustration.

![Transpiled Power Automate cloud flows in Intelligent Order Management](./media/power-automate-cloud-flows.PNG)






















