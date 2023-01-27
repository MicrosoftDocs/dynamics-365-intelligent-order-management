---
author: raybennett-msft
description: This article provides information on Intelligent Order Management Power Automate flows that you can use to develop your own custom solution.
ms.date: 01/27/2023
ms.topic: conceptual
ms.author: bennettray

title: Development

---

# Dynamics 365 Intelligent Order Management Power Automate flows
This article provides a list of the flows that are available as part of Dynamics 365 Intelligent Order Management. You can use these flows to build your own custom providers or solutions.

## Mapping flows
### Create account mapping

Create account mapping allows you to create a Customer account mapping uses the specified external field name and external field value for the lookup to map back to an Account ID.

| Parameter | Description | Required |
| --------- | ----------- | -------- |
| Provider ID | The Provider ID the mapping is for. | True |
| Mapping Group ID | The Mapping Group ID the mapping is for. | True |
| Account ID | The Account ID to return when a match is found. | True |
| External Field Name | The field name to check from the external datasource for the value. | True |
| External Field Value | The field value in the external datasource to match. | True |

The mapping returns the Account ID whether it's just created or already exists. 

>[!NOTE]
>This value is the ID of the mapping, not the account.

### Create contact mapping

Create contact mapping allows you to create a Customer contact mapping that uses the specified external field name and external field value for the lookup to map back to a Contact ID.

| Parameter | Description | Required |
| --------- | ----------- | -------- |
| Provider ID | The Provider ID the mapping is for. | True |
| Mapping Group ID | The Mapping Group ID the mapping is for. | True |
| Contact ID | The Contact ID to return when a match is found. | True |
| External Field Name | The field name to check from the external datasource for the value. | True |
| External Field Value | The field value in the external datasource to match. | True |

The mapping returns the Contact ID whether it's just created or already exists. 

> [!NOTE]
> This value is the ID of the mapping, not the contact.

### Create fulfillment order mapping

Create fulfillment order mapping allows you to create a fulfillment order mapping that uses the specified external field name and external field value for the lookup to map back to a Fulfillment order ID.

| Parameter | Description | Required |
| --------- | ----------- | -------- |
| Provider ID | The Provider ID the mapping is for. | True |
| Mapping Group ID | The Mapping Group ID the mapping is for. | True |
| Fulfillment Order ID | The Fulfillment Order ID to return when a match is found. | True |
| External Field Name | The field name to check from the external datasource for the value. | True |
| External Field Value | The field value in the external datasource to match. | True |

The mapping returns the Fulfillment order mapping ID if whether it's just created or it already exists. 

> [!NOTE]
> This value is the ID of the mapping, not the fulfillment order.

### Create fulfillment order product mapping

Create fulfillment order product mapping allows you to create a fulfillment order product mapping that uses the specified external field name and external field value for the lookup to map back to a Fulfillment order product ID.

| Parameter | Description | Required |
| :-------- | :---------- | :------- |
| Provider ID | The Provider ID the mapping is for. | True |
| Mapping Group ID | The Mapping Group ID the mapping is for. | True |
| Fulfillment Order Product ID | The Fulfillment Order Product ID to return when a match is found. | True |
| External Field Name | The field name to check from the external datasource for the value. | True |
| External Field Value | The field value in the external datasource to match. | True |

The mapping returns the Fulfillment order product mapping ID whether it's just created or it already exists. 

> [!NOTE]
>  This value is the ID of the mapping, not the fulfillment order product.

### Create order mapping

Create order mapping allows you to create an order mapping that uses the specified external field name and external field value for the lookup to map back to an order.

| Parameter | Description | Required |
| --------- | ----------- | -------- |
| Provider ID | The Provider ID the mapping is for. | True |
| Mapping Group ID | The Mapping Group ID the mapping is for. | True |
| Order ID | The Order ID to return when a match is found. | True |
| External Field Name | The field name to check from the external datasource for the value. | True |
| External Field Value | The field value in the external datasource to match. | True |

The mapping returns the Order mapping ID whether it's just created or it already exists. 

> [!NOTE]
> This value is the ID of the mapping, not the order.

### Get external mapping

Get external mapping returns the external field value that maps to the internal field value for a specific table and external field name.

| Parameter | Description | Required |
| --------- | ----------- | -------- |
| Mapping Table | The Mapping table to look up for the external value. | True |
| Provider ID | The Provider ID the mapping is for. | True |
| Mapping Group ID | The Mapping Group ID the mapping is for. | True |
| Internal Record Value | The value used internally to match. | True |
| External Field Name | The field name to check from the external datasource for the value. | True |

The mapping returns the record if a matching table, internal record value, and an external field name exists for the specified Provider or Mapping group.

### Get internal mapping

Get internal mapping returns the internal field value that maps to the external field value for a specific table and external field name.

| Parameter | Description | Required |
| --------- | ----------- | -------- |
| Mapping Table | The Mapping table to look up for the external value. | True |
| Provider ID | The Provider ID the mapping is for. | True |
| Mapping Group ID | The Mapping Group ID the mapping is for. | True |
| External Field Name | The field name to check from the external datasource for the value. | True |
| External Field Value | The value used externally to match. | True |

The mapping returns the record if a matching table, external field value and external field name exists for the specified Provider or Mapping group.

## Fulfillment flows

### Create fulfillment tracking

Create fulfillment tracking creates a record in the tracking table to associate a tracking number to a fulfillment order or fulfillment return order, and other details.

| Parameter | Description | Required |
| --------- | ----------- | -------- |
| Tracking Number | Tracking number to set for the record. | True |
| CarrierRecordId | A matching record from the **Shipping Carrier** table. | True |
| CarrierServiceId | A matching record from the **Carrier Service** table. | True |
| FulfillmentOrderRecordId | The fulfillment order record to set the tracking number on. | False |
| FulfillmentLineRecordId | The fulfillment order line record to set the tracking number on. | False |
| ShipmentId | The Associated shipment ID, if available. | False |
| ShipmentCost | The Associated shipment cost, if available. | False |
| InsuranceCost | The Associated insurance cost, if available. | False |
| Tax | The Associated tax, if available. | False |
| SurchargeFee | The Associated surcharge fee, if available. | False |
| FulfillmentReturnOrderRecordId | The fulfillment return order record to set the tracking number on. | False |

> [!NOTE]
> Either the **FulfillmentOrderRecordId** or **FulfillmentReturnOrderRecordId** is required.

The flow returns the Tracking number ID from the **Fulfillment Trackings** table.

### Fulfillment line and aggregated order events

This flow raises a business event on a fulfillment order line. When this event is raised, a check is done to verify that all lines have the same status. If they do have the same status, the specified fulfillment order level business event is raised at the header level.

| Parameter | Description | Required |
| --------- | ----------- | -------- |
| FulfillmentLineBusinessEventDefinitionId | A business event to raise on the line entity. | True |
| FulfillmentLineRecordId | The fulfillment order line to raise the initial business event for. | True |
| FulfillmentOrderBusinessEventDefinitionId | The business event to raise on the fulfillment order if all lines have the same status. | True |
| FulfillmentOrderRecordId | The fulfillment order to raise the business event for. | True |
| Payload | The optional JSON payload to pass with the business event. | False |

The flow returns **IsSuccessful true** if the business event was successfully raised.

## Customer account and contact flows
### Create or update an account

Creates or update an existing account given the specified JSON payload.

| Parameter | Description | Required |
| --------- | ----------- | -------- |
| Payload | The JSON representation of the account. | True |
| Account ID | The ID of the account to update. | False |

> [!NOTE]
> The **Account** table has specific fields that are required in the JSON payload. To see what fields are required, go to **Dataverse** > **Tables** > **All**, find your table, and select **Columns**. Use the **Required** field to determine what is required.

The flow returns the ID of the created or updated account.

### Create or update a contact

This flow creates or updates an existing contact given the specified JSON payload.

| Parameter | Description | Required |
| :-------- | :---------- | :------- |
| Payload | The JSON representation of the contact. | True |
| Contact ID | The ID of the account to update. | False |

> [!NOTE]
> The **Contact** table has specific fields that are required in the JSON payload. To see what fields are required, go to **Dataverse** > **Tables** > **All**, find your table, and select **Columns**. Use the **Required** field to determine what is required.

The flow returns the ID of the created or updated contact.

## Order flows and Order product flows
### Sales order creation

Create a sales order given the specified JSON payload.

| Parameter | Description | Required |
| --------- | ----------- | -------- |
| Payload | the JSON representation of the sales order and lines. | True |
| ProviderId | The ID of the calling provider. | False |

> [!NOTE]
> Both **Order** and **Order Line** have specific fields that are required in the JSON payload. To see what fields are required, go to **Dataverse** > **Tables** > **All**, find your table, and select **Columns**. Use the **Required** field to determine what is required.

The flow returns the ID of the created sales order.

### Raise lines and Aggregated order events

This flow raises a business event on a sales order line. When this event is raised, a check is completed to verify that all the lines have the same status. If they have the same status, the specified Order level business event is raised at the header level.

| Parameter | Description | Required |
| --------- | ----------- | -------- |
| LineBusinessEventId | The business event to raise on the line entity. | True |
| LineRecordId | The order line to raise the initial business event for. | True |
| OrderBusinessEventId | The business event to raise on the order if all lines have the same status. | True |
| OrderRecordId | The order to raise the business event for. | True |
| Payload | The optional JSON payload to pass with the business event. | False |

The flow returns **IsSuccessful true** if the business event was successfully raised.

### Raise sales order lines business event

This flow raises a business event for all lines on a sales order.

| Parameter | Description | Required |
| --------- | ----------- | -------- |
| SalesOrderId | The order record to raise the business events for each of its lines. | True |
| BusinessEventId | The order line business rvent to taise for each line. | True |

The flow returns **IsSuccessful true** if the business event was successfully raised.

### Unit conversion

This flow onverts a quantity from one unit to another using the unit conversions set up for a product.

| Parameter | Description | Required |
| --------- | ----------- | -------- |
| Quantity | The quantity to convert. | True |
| From unit | The unit to convert from. | True |
| To unit | The unit to convert to. | True |

The flow returns the unit conversion, if a conversion exists.

## Miscellaneous flows
### Provider transformer

The Provider transformer applies a Power Query transformation that's defined on a provider and returns the transformed data. This flow looks up an active provider instance by ID and checks for a transformation with a matching Source object name**** and **Destination object name**.

If the type of transformation is a Dataverse entity, a Record ID is required. If it's a **JsonPayload**, a value is required in the **Payload** field.

For a Dataverse entity, the Record ID provided is looked up for the entity defined on the transformation. If a record is found, that record is used for the transformation.

| Parameter | Description | Required |
| :-------- | :---------- | :------- |
| Provider ID | Any valid GUID. | True |
| Source Object Name | The Source object name to look up in Provider transformations. | True |
| Destination Object Name | The Destination object name to look up in Provider transformations. | True |
| Payload | The JSON payload to transform if type is **JsonPayload**. | False |
| Record ID | The record to look up for the entity associated with the transformation. | False |

> [!NOTE]
> A **Payload** or **Record ID** is required.
>
> The **Provider ID** is a GUID and is replaced when a provider is activated. You can enter any GUID here.

If successful, the flow returns a JSON representation of the transformed record.

### Raise a business event

Raise a business event for the supplied entity record with an optional payload.

| Parameter | Description | Required |
| --------- | ----------- | -------- |
| BusinessEventDefinitionId | The GUID of an existing business event. | True |
| EntityRecordId | The Record ID for the entity associated to the business event. | True |
| Payload | An optional payload to deliver with the business event. | False |

> [!NOTE]
> **EntityRecordIds** can be a comma-delimited list of Record IDs. If a delimited list is supplied, a business event is raised for each record.

 The flow returns **IsSuccessful true** if the business event was successfully raised.
