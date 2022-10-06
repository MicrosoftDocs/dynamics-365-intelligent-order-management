---
author: raybennett-msft
description: This article describes the state framework architecture in Microsoft Dynamics 365 Intelligent Order Management.
ms.date: 10/06/2022
ms.topic: conceptual
ms.author: bennettray

title: State framework architecture

---
# State framework architecture

[!include [banner](includes/banner.md)]

This article describes the state framework architecture in Microsoft Dynamics 365 Intelligent Order Management.

State framework architecture is a new concept that was introduced in Dynamics 365 Intelligent Order Management in the October 2022 release. The state framework is a way of validating business process rules by checking, at runtime, whether the current state of an entity is allowed to move to another state. For example, a transition from **New** to **In Progress** will be successful if it's defined, but a transition from **Completed** to **In Progress** will throw an error.

Users can add their own states, state reasons, and transitions. However, they can't customize the out-of-box definitions.

## State framework data model

The state framework data model introduces some updates and new additions to the current data model.

The following illustration shows the tables that have been added in the state framework data model.

![State framework data model.](media/state-framework-1.png)

### Updates to the data model

#### Entity State and State Reason columns

The state framework introduces two new columns to the entities that are part of Intelligent Order Management. These columns were added to support localizable **State** and **State Reason** status fields. The state framework also introduces a new **ReadOnly** field that indicates that a record should not be editable in the user interface (UI).

| Field | Description |
|---|---|
| State | The state that the entity is in, as defined by the **State Definition** table. |
| State Reason | A detailed description of the reason why the entity is in its current state. |
| ReadOnly | Set the value to **True** if the record should not be editable in the UI. Otherwise, set it to **False**. |

### New additions to the data model

#### State Definition table

The **State Definition** table enables the creation of a set of states that are allowable on each entity. These states have associated properties that contain metadata to indicate the different behaviors of each state.

> [!NOTE]
> States are used to determine valid transitions as part of the orchestration journey.

| Field | Description |
|---|---|
| State Definition | The globally unique identifier (GUID) of the state. |
| Associated Entity | The entity that the state belongs to. |
| Details | The name of the state. |
| State Definition Properties | A lookup for associated metadata. |
| Readonly | A value of **True** marks the entity as read-only. |

#### State Definition Reason table

The **State Definition Reason** table provides extra details about why something is in a given state, but might not be part of indicating a valid state transition. For example, something can have a state of **On Hold** but a state reason of **Backorder** or **Preorder**.

| Field | Description |
|---|---|
| State Definition Reason | The GUID of the state reason. |
| State | The state that the state reason is associated with. |
| Details | The name/description of the state reason. |

#### State Definition Properties table

The **State Definition Properties** table contains extra metadata for each state.

| Field | Description |
|---|---|
| State Definition Properties | The GUID of the property. |
| Timeline Position | The order in which the state should be shown in the **Progress Bar Timeline** control in the UI. (This control is introduced in the October 2022 release.) |

### State Transition table

The **State Transition** table contains a list of state transitions that will occur when a business event is raised. The business event will set the state only if the current state is in an allowable state.

| Field | Description |
|---|---|
| State Transition | The GUID of the state transition. |
| Business Event Definition | A lookup to the **Business Event Definition** table to determine which business event the record belongs to. |
| Source State | The allowable source state to transition from. |
| Target State | The target state to set if coming from an allowable source state. |
| Target State Reason | The target state reason to set if coming from an allowable source state. |

The following table shows an example of data in this table.

| Business Event Definition | Source State | Target State | Target State Reason |
|---|---|---|---|
| On Hand Check Success | In Progress | Fulfillment in Process | Inventory Check Successful |
| On Hand Check Success | On Hold | Fulfillment in Process | Inventory Check Successful |
| On Hand Check Failed | In Progress | On Hold | Backorder Hold |

## Scenarios

### No transition exists for the business event

If no record is found in the **State Transition** table for the business event that is being raised, the validation will automatically succeed, but no **State** or **State Reason** value will be set.

### Add a new state and transition

To add a new state and transition, follow these steps.

1. Add a new state definition.
1. Add a new state reason definition, if it's required.
1. Add a new state transition, and then follow these steps:

    1. Associate the new state transition with a new business event.
    1. Set the **Source** field to what is allowed. Add one row per allowable source.
    1. Set the **State** field to what the state should be set to when the business event is raised.
    1. Set the **State Reason** field to what you want the reason to be when the business event is raised.

1. Add any properties (**ReadOnly** or **Timeline**) that are required. 
