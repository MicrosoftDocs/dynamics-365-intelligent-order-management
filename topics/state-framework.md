# State Framework
The State Framework is a new concept introduced to Dynamics 365 Intelligent Order Management for the October 2022 release. The State Framework is a way of validating business process rules by checking at runtime if the current state of an entity is allowed to move to another state; for example, from **New -> In Progress** would be a successful transition if defined, but **Completed -> In Progress** would throw an error.

Users can add their own State, State Reason and Transitions, but won't be allowed to customize out of the box definitions.

## State Framework Data Model

![Data Model](media/state-framework-1.png)

State Framework introduces a few changes to the current data model and a few additions.

### Updated – Entity State/State Reason Columns
The State Framework is introducing two new columns to the entities that are part of Intelligent Order Management. These columns were added to support localizable State and State Reason status fields. It also introduces a new ReadOnly field, which will indicate to the UI not to allow any changes.

|**Field**|**Description**|
| :- | :- |
|**State**|What state the entity is in, as defined by the State Definition table|
|**State Reason**|A detailed description of why the entity is in that state|
|**ReadOnly**|True to indicate to the UI that the record shouldn't be editable, otherwise False|

### New – State Definition
The State Definition table is for creating a set of States that are allowable on each Entity. These States have associated properties that contain metadata to indicate different behaviors for that state.

**Note:** States are used to determine valid transitions as part of the orchestration journey

|**Field**|**Description**|
| :- | :- |
|**State Definition**|ID (guid) for this State|
|**Associated Entity**|Which entity the State belongs to|
|**Details**|Name of the State|
|**State Definition Properties**|A lookup to associated metadata|
|**Readonly**|Indicates that setting this state should mark the entity as ReadOnly|

### New – State Reason Definition
The State Reason Definition is for providing extra details for why something is in that State, but may not be part of indicating a valid state transition. For example, something can have a **State** of **On** **Hold**, but have a **State** **Reason** of **Backorder** or **Preorder**.

|**Field**|**Description**|
| :- | :- |
|**State Definition Reason**|ID (guid) for this State Reason|
|**State**|Which State the State Reason is associated with|
|**Details**|Name/Description of the State Reason|

### New – State Definition Properties
This table contains extra metadata for each of the States

|**Field**|**Description**|
| :- | :- |
|**State Definition Properties**|ID (guid) for this Property|
|**Timeline Position**|Which order to display this state in the UI on the Progress Bar Timeline introduced in the Oct’22 release.|

### New – State Transition
This table contains a list of state transitions that will occur when a business event is raised. The business event will only set the state if the current state is in an allowable state.

|**Field**|**Description**|
| :- | :- |
|**State Transition**|ID (guid) of this State Transition|
|**Business Event Definition**|Lookup to the Business Event Definition table to determine which Business Event the record belongs to|
|**Source State**|The allowable source State to transition From|
|**Target State**|Target State to set if coming from an allowable Source State|
|**Target State Reason**|Target State Reason to set if coming from an allowable Source State|

An example of data in this table would look as follows

|**Business Event**|**Source**|**Target State**|**Target State Reason**|
| :- | :- | :- | :- |
|**On Hand Check Success**|In Progress|Fulfillment in Process|Inventory Check Successful|
|**On Hand Check Success**|On Hold|Fulfillment in Process|Inventory Check Successful|
|**On Hand Check Failed**|In Progress|On Hold|Backorder Hold|

## Scenario – No Transition exists for the Business Event
If no record is found in the State Transition table for the Business Event being raised, the validation will automatically succeed, but no State or State Reason will be set.
## Scenario - Adding a new State and Transition
To add a new State, the following steps would need to be taken

1. Add a new State Definition
1. Add a new State Reason Definition if needed
1. Add a new State Transition
   1. Associate it to a new Business Event
   1. Set the Source to what is allowed, one row per allowable source
   1. Set the State to what the State should be set to when this event is raised
   1. Set the State Reason to what you would like it to be when the event is raised
1. Add any Properties if needed. ReadOnly or Timeline
