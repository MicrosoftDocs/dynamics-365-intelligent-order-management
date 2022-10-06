---
author: raybennett-msft
description: This topic provides information on Intelligent Order Management Power Automate Flows that you can use to develop your own custom solution.
ms.date: 10/06/2022
ms.topic: conceptual
ms.author: bennettray

title: Development

---

# Dynamics 365 Intelligent Order Management Power Automate Flows
This page lists flows that are available as part of the Dynamics 365 Intelligent Order Management product that allows you to build your own custom providers or solutions.

## Mapping Flows
### Create Account Mapping

Create Account Mapping allows you to create a Customer Account Mapping that will use the specified External Field Name and External Field Value for their lookup to map back to an Account ID.

| Parameter | Description | Required |
| :-------- | :---------- | :------- |
| Provider ID | The Provider ID the mapping is for | true |
| Mapping Group ID | The Mapping Group ID the mapping is for | true |
| Account ID | The Account ID to return when a match is found | true |
| External Field Name | The field name to check from the external datasource for the value | true |
| External Field Value | The field value in the external datasource to match | true |

**Returns:** The Account ID if created or if already existing. **Note**: this is the ID of the Mapping, not the Account

### Create Contact Mapping

Create Contact Mapping allows you to create a Customer Contact Mapping that will use the specified External Field Name and External Field Value for their lookup to map back to a Contact ID.

| Parameter | Description | Required |
| :-------- | :---------- | :------- |
| Provider ID | The Provider ID the mapping is for | true |
| Mapping Group ID | The Mapping Group ID the mapping is for | true |
| Contact ID | The Contact ID to return when a match is found | true |
| External Field Name | The field name to check from the external datasource for the value | true |
| External Field Value | The field value in the external datasource to match | true |

**Returns:** The Contact ID if created or if already existing. **Note**: this is the ID of the Mapping, not the Contact

### IOM Create Fulfillment Order Mapping

IOM Create Fulfillment Order Mapping allows you to create a Fulfillment Order Mapping that will use the specified External Field Name and External Field Value for their lookup to map back to a Fulfillment Order ID

| Parameter | Description | Required |
| :-------- | :---------- | :------- |
| Provider ID | The Provider ID the mapping is for | true |
| Mapping Group ID | The Mapping Group ID the mapping is for | true |
| Fulfillment Order ID | The Fulfillment Order ID to return when a match is found | true |
| External Field Name | The field name to check from the external datasource for the value | true |
| External Field Value | The field value in the external datasource to match | true |

**Returns:** The Fulfillment Order Mapping ID if created or if already existing. **Note**: this is the ID of the Mapping, not the Fulfillment Order

### IOM Create Fulfillment Order Product Mapping

IOM Create Fulfillment Order Product Mapping allows you to create a Fulfillment Order Product Mapping that will use the specified External Field Name and External Field Value for their lookup to map back to a Fulfillment Order Product ID

| Parameter | Description | Required |
| :-------- | :---------- | :------- |
| Provider ID | The Provider ID the mapping is for | true |
| Mapping Group ID | The Mapping Group ID the mapping is for | true |
| Fulfillment Order Product ID | The Fulfillment Order Product ID to return when a match is found | true |
| External Field Name | The field name to check from the external datasource for the value | true |
| External Field Value | The field value in the external datasource to match | true |

**Returns:** The Fulfillment Order Product Mapping ID if created or if already existing. **Note**: this is the ID of the Mapping, not the Fulfillment Order Product

### IOM Create Order Mapping

IOM Create Order Mapping allows you to create an Order Mapping that will use the specified External Field Name and External Field Value for their lookup to map back to an Order

| Parameter | Description | Required |
| :-------- | :---------- | :------- |
| Provider ID | The Provider ID the mapping is for | true |
| Mapping Group ID | The Mapping Group ID the mapping is for | true |
| Order ID | The Order ID to return when a match is found | true |
| External Field Name | The field name to check from the external datasource for the value | true |
| External Field Value | The field value in the external datasource to match | true |

**Returns:** The Order Mapping ID if created or if already existing. **Note**: this is the ID of the Mapping, not the Order

### IOM Get External Mapping

IOM Get External Mapping retrns the External Field Value that maps to the Internal Field Value for a specific Table and External Field Name

| Parameter | Description | Required |
| :-------- | :---------- | :------- |
| Mapping Table | The Mapping table to lookup for the external value | true |
| Provider ID | The Provider ID the mapping is for | true |
| Mapping Group ID | The Mapping Group ID the mapping is for | true |
| Internal Record Value | The value used internally to match | true |
| External Field Name | The field name to check from the external datasource for the value | true |

**Returns:** The record if a matching Table, Internal Record Value and External Field Name exists for the specified Provider or Mapping Group

### IOM Get Internal Mapping

IOM Get Internal Mapping retrns the Internal Field Value that maps to the External Field Value for a specific Table and External Field Name

| Parameter | Description | Required |
| :-------- | :---------- | :------- |
| Mapping Table | The Mapping table to lookup for the external value | true |
| Provider ID | The Provider ID the mapping is for | true |
| Mapping Group ID | The Mapping Group ID the mapping is for | true |
| External Field Name | The field name to check from the external datasource for the value | true |
| External Field Value | The value used externally to match | true |

**Returns:** The record if a matching Table, External Field Value and External Field Name exists for the specified Provider or Mapping Group

## Fulfillment Flows

### Create Fulfillment Tracking

Create Fulfillment Tracking creates a record in the tracking table to associate a tracking number to a Fulfillment Order or Fulfillment Return Order, as well as additional details.

| Parameter | Description | Required |
| :-------- | :---------- | :------- |
| Tracking Number | Tracking Number to set for the record | true |
| CarrierRecordId | A matching Record from the Shipping Carrier table | true |
| CarrierServiceId | A matching Record from the Carrier Service table | true |
| FulfillmentOrderRecordId | Fulfillment Order Record to set the Tracking Number on | false |
| FulfillmentLineRecordId | Fulfillment Order Line Record to set the Tracking Number on | false |
| ShipmentId | Associated Shipment ID if available | false |
| ShipmentCost | Associated Shipment Cost if available | false |
| InsuranceCost | Associated Insurance Cost if available | false |
| Tax | Assocciated Tax if available | false |
| SurchargeFee | Associated Surcharge Fee if available | false |
| FulfillmentReturnOrderRecordId | Fulfillment Return Order Record to set Tracking Number on | false |

**Note:** at least one of FulfillmentOrderRecordId or FulfillmentReturnOrderRecordId is needed.

**Returns:** The Tracking Number ID from the Fulfillment Trackings table

### Fulfillment Line and Aggregated Order Events

Raises a Business Event on a Fulfillment Order Line. When raising this event, a check is done to see if all lines have the same Status. If they have the same Status, the specified Fulfillment Order level Business Event is raised at the header level.

| Parameter | Description | Required |
| :-------- | :---------- | :------- |
| FulfillmentLineBusinessEventDefinitionId | Business Event to raise on the line Entity | true |
| FulfillmentLineRecordId | Fulfillment Order Line to raise the initial Business Event for | true |
| FulfillmentOrderBusinessEventDefinitionId | Business Event to raise on the Fulfillment Order if all lines are same status | true |
| FulfillmentOrderRecordId | Fulfillment Order to raise the Business Event for | true |
| Payload | Optional JSON payload to pass with the Business Event | false |

**Returns:** IsSuccessful true if the Business Event was successfully raised.

## Customer Account/Contact Flows
### Create or Update Account

Creates or updates an existing Account given the specified JSON payload.

| Parameter | Description | Required |
| :-------- | :---------- | :------- |
| Payload | JSON representation of the Account | true |
| Account Id | The ID of the Account to update | false |

**Note:** The Account table has specific fields that are required in the JSON payload. To see what fields are required, navigate to **Dataverse** > **Tables** > **All**, find your table, and click on **Columns**. Use the Required field to determine what is required.

**Returns:** The ID of the created or updated Account

### Create or Update Contact

Creates or updates an existing Contact given the specified JSON payload.

| Parameter | Description | Required |
| :-------- | :---------- | :------- |
| Payload | JSON representation of the Contact | true |
| Contact Id | The ID of the Account to update | false |

**Note:** The Contact table has specific fields that are required in the JSON payload. To see what fields are required, navigate to **Dataverse** > **Tables** > **All**, find your table, and click on **Columns**. Use the Required field to determine what is required.

**Returns:** The ID of the created or updated Contact

## Order/Order Product Flows
### IOM Sales Order Creation

Creates a Sales Order given the specified JSON payload.

| Parameter | Description | Required |
| :-------- | :---------- | :------- |
| Payload | JSON representation of the Sales Order and Lines | true |
| ProviderId | The ID of the calling Provider | false |

**Note:** Both Order and Order Line have specific fields that are required in the JSON payload. To see what fields are required, navigate to **Dataverse** > **Tables** > **All**, find your table, and click on **Columns**. Use the Required field to determine what is required.

**Returns:** The ID of the created Sales Order

### IOM Raise Lines and Aggregated Order Events

Raises a Business Event on a Sales Order Line. When raising this event, a check is done to see if all lines have the same Status. If they have the same Status, the specified Order level Business Event is raised at the header level.

| Parameter | Description | Required |
| :-------- | :---------- | :------- |
| LineBusinessEventId | Business Event to raise on the line Entity | true |
| LineRecordId | Order Line to raise the initial Business Event for | true |
| OrderBusinessEventId | Business Event to raise on the Order if all lines are same status | true |
| OrderRecordId | Order to raise the Business Event for | true |
| Payload | Optional JSON payload to pass with the Business Event | false |

**Returns:** IsSuccessful true if the Business Event was successfully raised.

### IOM Raise Sales Order Lines Business Event

Raises a Business Event for all Lines on a Sales Order

| Parameter | Description | Required |
| :-------- | :---------- | :------- |
| SalesOrderId | The Order Record to raise the Business Events for each of its lines | true |
| BusinessEventId | The Order Line Business Event to Raise for each line | true |

**Returns:** IsSuccessful true if the Business Event was successfully raised.

### IOM Unit Conversion

Converts a quantity from one unit to another using the Unit conversions setup on a Product.

| Parameter | Description | Required |
| :-------- | :---------- | :------- |
| Quantity | The quantity to convert | true |
| From unit | The unit to convert from | true |
| To unit | The unit to convert to | true |

**Returns:** the unit conversion if a conversion exists

## Miscellaneous Flows
### IOM Provider Transformer

IOM Provider Transformer applies a Power Query transformation defined on a Provider and returns the transformed data. This flow will lookup an active provider instance by ID, and check for a transformation with a matching Source Object Name and Destination Object Name.

If the type of transformation is a Dataverse Entity, a Record ID is required. If it is a JsonPayload, a value is required in the Payload field.

For a Dataverse Entity, the Record ID provided is looked up for the Entity defined on the Transformation. If a record is found, that record is used for the transformation.

| Parameter | Description | Required |
| :-------- | :---------- | :------- |
| Provider ID | Any valid GUID | true |
| Source Object Name | The Source Object Name to lookup in Provider Transformations | true |
| Destination Object Name | The Destination Object Name to lookup in Provider Transformations | true |
| Payload | JSON payload to transform if type is JsonPayload | false |
| Record ID | Record to lookup for the Entity associated with the transformation | false |

**Note:** at least one of Payload or Record ID is required.

**Note:** Provider ID is a GUID and is replaced when a Provider is activated. You can put any guid here

**Returns:** A JSON representation of the transformed record if successful.

### IOM Raise Business Event

Raises a Business Event for the supplied Entity Record with an optional payload.

| Parameter | Description | Required |
| :-------- | :---------- | :------- |
| BusinessEventDefinitionId | The GUID of an existing Business Event | true |
| EntityRecordId | The Record ID for the Entity associated to the Business Event | true |
| Payload | An optional payload to deliver with the business event | false |

**Note:** EntityRecordIds can be a comma-delimited list of Record IDs. If this is supplised, a Business Event is raised for each Record

**Returns:** IsSuccessful true if the Business Event was successfully raised.