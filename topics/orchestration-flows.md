---
author: josaw1
description: This topic provides information about orchestration flows in Dynamics 365 Intelligent Order Management.
ms.date: 04/12/2024
ms.custom: 
  - bap-template
ms.topic: conceptual
ms.author: josaw

title: Create orchestration flows
---


# Create orchestration flows

[!include [banner](includes/banner.md)]



This topic covers orchestration flows and describes how to create them in Microsoft Dynamics 365 Intelligent Order Management.

Orchestration flows are a central concept in Intelligent Order Management. You can create orchestration flows that determine how data obtained from configured providers are being orchestrated.

Intelligent Order Management supports the ability to define orchestration flows for different purposes such as ordering intake to fulfillment and collecting and distributing inventory visibility information.

## Orchestration types

Orchestration types control which actions and elements can be used to define the orchestration flow. One orchestration type is currently supported out-of-the-box. Additional orchestration types will be released over time.

| Type            | Purpose                                                                                                        |
|---------------------|--------------------------------------------------------------------------------------------------------------------|
| Order orchestration | Allows users to define an end-to-end orchestration flow for orders, from order capture to fulfillment and billing. |

## Orchestration fields

An orchestration flow record consists of three fields, as listed in the following table.

| Field | Description |
|-------------------------|-------------------------|
| Name | A unique name provided by the user. |
| Orchestration type | Specifies the orchestration type. |
| Created on | The date and time when the orchestration flow was created. |
| Status | <p>An orchestration flow can be in two status states:</p><ul><li>**Unpublished** – The orchestration flow and its actions will not be executed when data flows into the system.</li><li>**Published** – This status is obtained when the orchestration flow is published using the **Publish** action in designer view. The orchestration flow and its actions are executed when data flows into the system.</li></ul> |


## Actions and elements 

Actions and elements can be used to define the orchestration flow in designer view. The following table lists actions and elements for the order orchestration type.

| Action or Element                                          | Description                                                                                                                                                                  |
|----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Validate Order Header                                          | Performs validation on the order header level.                                                                                                                               |
| Validate Order Line                                            | Performs validation on the order line level.                                                                                                                                 |
| Send to DOM                                                    | Sends orders and order lines to the distributed order management (DOM) provider for fulfillment determination. Fulfillment orders and fulfillment order lines are generated. |
| Assign Fulfillment Source                                      | Allows fulfillment determination to be assigned by simple user-defined policy and rules. Fulfillment orders and fulfillment order lines are generated.                       |
| Send to Fulfillment                                            | Sends fulfillment orders and fulfillment order lines to the fulfillment provider.                                                                                            |
| Send to Fulfillment – Dynamics 365 finance and operations apps | Sends orders and order lines to finance and operations apps. The fulfillment determination takes place in finance and operations apps.                                       |
| Send to Invoice                                                | Sends orders and order lines to the billing provider.                                                                                                                        |
| Custom                                                         | Allows adding user-defined actions to the orchestration flow. For example, a user-defined action can be used to orchestrate orders to a custom provider.                     |


The following table lists other available actions and elements.

| Action or Element | Description |
|-------------------------|-------------------------|
| Condition | <p>Allows you to split the orchestration flow into two paths, with no constraint that the paths will merge again.</p><ul><li>**Yes** – This path will be triggered if the previous orchestration step succeeded.</li><li>**No** – This path will be triggered if the previous orchestration step failed.</li></ul> |
| Splitter | <p>Allows you to split the orchestration flow into a user-defined number of paths, with no constraint that the paths will merge again.</p><p>**Note:** Adding a filter policy in the subsequent action is used to define the split in path.</p> |
| Condition-Merge | <p>Allows you to split the orchestration flow into two paths, with the constraint that the paths will merge again.</p><ul><li>**Yes** – This path will be triggered if the previous orchestration step succeeded.</li><li>**No** – This path will be triggered if the previous orchestration step failed.</li></ul> |
| Splitter-Merge | <p>Allows you to split the orchestration flow into a user-defined number of paths, with the constraint that the paths will merge again.</p><p>**Note:** Adding a filter policy in the subsequent action is used to define the split in path.</p> |



## Create a new orchestration flow

To create a new orchestration flow, follow these steps.

1.  Go to **Orchestration &gt; Flows**.

2.  Select **New** to initiate the orchestration flow creation process. The orchestration flow designer canvas opens.

3.  In the upper-left corner, enter a unique name such as "Test Order flow sample."

4.  In the **Orchestration Type** field, select **Order Orchestration**.

5.  In the **Description** field, enter "My first orchestration flow."

6.  In the designer canvas, select the plus symbol ("+") to add an **Action** or **Element**.

7.  Select **Splitter-Merge**. A dialog box appears on the right.

8.  In the **Name** field, enter "Validation split."

9.  In **Splitter Settings**, delete **Branch 1** and enter **Order Source 1**, and then delete **Branch 2** and enter **Order Source 2**.

10. In the designer canvas under **Order Source 1**, select the plus symbol ("+") to add an **Action** or **Element**.

11. Select **Validate order header**. A dialog box appears on the right.

12. In the **Name** field, enter "Test validation 1."

13. In the **Input Events** field, select **New order**.

14. Select **Add**.

15. In the **Filter Policies** field, select **Filter Policy – BigCommerce**.

16. In the **Execution Policies** field, select **Order header Validation Policy**.

17. Select **Add**.

18. In the designer canvas under **Order Source 2**, select the plus symbol ("+") to add an **Action** or **Element**.

19. Select **Validate order header**. A dialog box appears on the right.

20. In the **Name** field, enter "Test validation 2."

21. In the **Input Events** field, select **New order**.

22. Select **Add**.

23. In the **Filter Policies** field, select **Filter Policy – Orderful**.

24. In the **Execution Policies** field, select **Order header Validation Policy**.

25. Select **Add**.

26. Select **Publish**.

The following illustration shows an example orchestration flow named "Test Order flow sample."

![Test order flow sample.](media/test-order-flow.png)

> [!NOTE]
> -   Several orchestration flows of the same type can be in the status "Published" simultaneously. An order and its lines can be processed by multiple orchestration flows. Adding and configuring filter policies is important if you create and publish several orchestration flows.
> -   An orchestration flow cannot be edited after it is published.
> -   A published orchestration flow can be stopped, which will update the status to "Unpublished." This ensures that data will no longer flow through that orchestration flow.
> -   You may receive a message that explains that a stopped orchestration flow cannot be restarted. This message is incorrectly generated from the designer platform and does not apply to the implementation of the designer in Intelligent Order Management.
> -   An unpublished orchestration flow can be edited and published again, which will update the status to "Published." This ensures that data will again flow through the new version of the orchestration flow.
