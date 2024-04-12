---
author: josaw1
description: This topic covers policy types and describes how to create a policy with rules in Dynamics 365 Intelligent Order Management.
ms.date: 04/12/2024
ms.custom: 
  - bap-template
ms.topic: conceptual
ms.author: josaw

title: Policies and rules

---


# Policies and rules

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic covers policy types and describes how to create a policy with rules in Dynamics 365 Intelligent Order Management.

## Policy types

Policies and their associated rules are used for different purposes in the Intelligent Order Management orchestration flow. Policies are classified into different policy types. Policy types ensure that users can easily select the appropriate policies in the orchestration flow. The two supported policy types are listed in the following table. 

| Policy type                   | Description                                                                                                         |
|-------------------------------|------------------------------------------------------------------------------------------------------------------|
| Filter policy                 | Allows validation of data running through an orchestration flow. For example, you may want to drive a specific orchestration for a specific provider. Filter policy allows you to filter the orchestration step to run based on the policy success criteria.|
| Execution policy              | Allows checking and updating data running through an orchestration flow. For example, you may want to assign a specific Fulfillment location to your order whenevr your order quantity is greater than 100. An execution policy will make this assignment simple and configurable.                                            |

## Policy fields

A policy consists of five fields, as shown in the following table.

| Policy field       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|--------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Policy Name        | A unique name provided by the user.                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| Policy Type        | The user can select one of two policy types: **Filter policy** or **Execution policy**.                                                                                                                                                                                                                                                                                                                                    |
| Policy Criticality | The user can select one of two options: <br>**Information** - The rules of the policy will be evaluated but the orchestration flow will not be stopped in an unsuccessful evaluation.<br> **Critical information** - The rules of the policy will be evaluated and the orchestration flow will be stopped in an unsuccessful evaluation.                                                                                                           |
| Status              | A policy and its associated rules can be in one of two status states:<br>**Unpublished** - The default status of a policy. A policy and its rules are not available to select in the orchestration flow when in this state.<br>**Published** - This status is obtained when the policy and its associated rules are published using the **Publish** action. The policy and its rules are available to select in the orchestration flow when in this state. |
| Associated Entity  | The user can select one of four primary entities for the policy: **Order**, **Order product**, **Fulfillment order**, **Fulfillment order product**. The   rules defined can be used against the primary entity or any related entity in the data model.                                                                                                                                                                                                                             |

## Create a new policy

To create a new policy, follow these steps.

1.	Go to **Orchestration** > **Policies**.  
2.	Select **New** to initiate the policy creation process.
3.	In the **Policy Name** field, enter a unique name (for example, “Order line validations extended”). 
4.	In the **Policy Type** field, select **Execution Policy**. 
5.	In the **Policy Criticality** field, select **Information**. 
6.	In the **Associated Entity** field, select **Order Product**. 
7.	Select **Save**.

The following image shows the policy details entered for the “Order line validations extended” policy example.

![Order line validations extended policy example.](media/order-line-validations-extended.png)

## Rules

You can create conditional rules in Intelligent Order Management by using Condition Builder's user interface.

To add a condition to your policy, select **New IOM Rule**. An **Add** button appears in the rule definition that, when selected, displays the following options:

   - **Add row**: Each individual condition that you check for, such as “the value is greater than 10,” or “the list does not contain Test”, creates a new row in Condition Builder.
   - **Add group**: You can combine one or more rows together in a group. Each group is combined by using either an **And** or an **Or** operator. If you select **And**, then all the condition rows must be true. If you select **Or**, then only one of the condition rows needs to be true.
   - **Add related entity**: You can add conditions against values in related entities. You can also select between entities that are related to the primary entity of the policy. The supported relations are **Many to One** and **One to Many**.

You can have as many rows or groups as you need to build out your logic and you can continue adding rows or groups both at the top level of the condition, and inside groups using **Add** buttons. If you want a simplified view of the condition, you can collapse it using a button at the top-right of each group.

Additionally, there is an ellipsis menu (“...”) on the right side of each row and group that allows you to delete a row or group. There are also check boxes on the left side of each row or group that allow you to select several different rows, and then select **Group** from the ellipsis menu to combine the rows into a single group.

The supported operators differentiate each field type, as shown in the following table.

| Operator                      | Field | Entity-based field |
|-------------------------------|-------|--------------------|
| Equals                        | Y     | Y                  |
| Does not   equal              | Y     | Y                  |
| Is   greater than             | Y     |                    |
| Is   greater than or equal to | Y     |                    |
| Is less   than                | Y     |                    |
| Is less   than or equal to    | Y     |                    |
| Contains   data               | Y     | Y                  |
| Does not   contain data       | Y     | Y                  |

## Create a rule

To create a new example rule, follow these steps.

1.	Go to **Orchestration** > **Policies**.
1.	Select a policy record (for example, “Order line validations extended”).
1.	Select **New IOM Rule** to initiate the rule creation process.
1. In the **Rule Name** field, enter a unique name (for example, “Order product and amount validation”).

### Create a condition

1. Select **Add**, and then select **Add Row**.
1. Select **Quantity**.
1. Select the **Is greater than or equal to** operator.
1. Enter "50".
1. Select **Add**, and then select **Add Group**.
1. Change the condition to "Or".
1. Select **Product Name**.
1. Select the **Equals** operator.
1. Enter "Item A".
1. Select **Add** at the bottom of the **Or** group, and then select **Add Row**.
1. Select **Product Name**.
1. Select the **Equals** operator.
1. Enter "Item B".

### Create an action

1. Change **Add Action** to **Yes**.
1. Select **Add**, and then select **Add Row**.
1. Select **Price Per Unit**.
1. Select **Set Value operator**.
1. Enter "20".
1. Select **Save & Close**.
1. Select **Publish**.

The following image shows the "Order product and amount validation" rule example as it would appear in the rule editor screen.

![Sample Policy Setup](media/Policy.png)

## Add custom action

Custom actions can only be added for execution policies. To add a custom action that is not triggered by the orchestration flow when a rule is evaluated, under **Action**, select **Yes** for **Add Action**.

You can then select the fields to set for the associated entity that was chosen when you created the policy.
