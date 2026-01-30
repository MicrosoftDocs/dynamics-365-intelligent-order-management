---
author: raybennett-msft
description: Learn about Intelligent Order Management Power Automate flows that you can use to develop your own custom solution.
ms.date: 01/27/2026
ms.custom: 
  - bap-template
ms.topic: article
ms.author: anvenkat
title: Dynamics 365 Intelligent Order Management Power Automate flows
---

# Dynamics 365 Intelligent Order Management Power Automate flows

This article provides a list of the flows that are available as part of Microsoft Dynamics 365 Intelligent Order Management. Use these flows to build your own custom providers or solutions.

## Mapping flows

### Create account mapping

The **Create account mapping** flow creates a customer account mapping that uses the specified external field name and external field value for the lookup to map back to an account ID.

| Parameter | Description | Required |
| --------- | ----------- | -------- |
| Provider ID | The provider ID for the mapping. | True |
| Mapping Group ID | The mapping group ID for the mapping. | True |
| Account ID | The account ID to return when a match is found. | True |
| External Field Name | The name of the field to check for the value in the external data source. | True |
| External Field Value | The field value to match in the external data source. | True |

The mapping returns the account ID, whether it's just created or it already exists.

> [!NOTE]
> This value is the ID of the mapping, not the account.

### Create contact mapping

The **Create contact mapping** flow creates a customer contact mapping that uses the specified external field name and external field value for the lookup to map back to a contact ID.

| Parameter | Description | Required |
| --------- | ----------- | -------- |
| Provider ID | The provider ID for the mapping. | True |
| Mapping Group ID | The mapping group ID for the mapping. | True |
| Contact ID | The contact ID to return when a match is found. | True |
| External Field Name | The name of the field to check for the value in the external data source. | True |
| External Field Value | The field value to match in the external data source. | True |

The mapping returns the contact ID, whether it's new or already exists.

> [!NOTE]
> This value is the ID of the mapping, not the contact.

### Create fulfillment order mapping

The **Create fulfillment order mapping** flow creates a fulfillment order mapping that uses the specified external field name and external field value for the lookup to map back to a fulfillment order ID.

| Parameter | Description | Required |
| --------- | ----------- | -------- |
| Provider ID | The provider ID for the mapping. | True |
| Mapping Group ID | The mapping group ID for the mapping. | True |
| Fulfillment Order ID | The fulfillment order ID to return when a match is found. | True |
| External Field Name | The name of the field to check for the value in the external data source. | True |
| External Field Value | The field value to match in the external data source. | True |

The mapping returns the fulfillment order mapping ID, whether it's newly created or already exists.

> [!NOTE]
> This value is the ID of the mapping, not the fulfillment order.

### Create fulfillment order product mapping

The **Create fulfillment order product mapping** flow creates a fulfillment order product mapping that uses the specified external field name and external field value for the lookup to map back to a fulfillment order product ID.

| Parameter | Description | Required |
| --------- | ----------- | -------- |
| Provider ID | The provider ID for the mapping. | True |
| Mapping Group ID | The mapping group ID for the mapping. | True |
| Fulfillment Order Product ID | The fulfillment order product ID to return when a match is found. | True |
| External Field Name | The name of the field to check for the value in the external data source. | True |
| External Field Value | The field value to match in the external data source. | True |

The mapping returns the fulfillment order product mapping ID, whether it's just created or it already exists.

> [!NOTE]
> This value is the ID of the mapping, not the fulfillment order product.

### Create order mapping

The **Create order mapping** flow creates an order mapping that uses the specified external field name and external field value for the lookup to map back to an order.

| Parameter | Description | Required |
| --------- | ----------- | -------- |
| Provider ID | The provider ID for the mapping. | True |
| Mapping Group ID | The mapping group ID for the mapping. | True |
| Order ID | The order ID to return when a match is found. | True |
| External Field Name | The name of the field to check for the value in the external data source. | True |
| External Field Value | The field value to match in the external data source. | True |

The mapping returns the order mapping ID, whether it's just created or it already exists.

> [!NOTE]
> This value is the ID of the mapping, not the order.

### Get external mapping

The **Get external mapping** flow returns the external field value that maps to the internal field value for a specific table and external field name.

| Parameter | Description | Required |
| --------- | ----------- | -------- |
| Mapping Table | The mapping table to look up for the external value. | True |
| Provider ID | The provider ID for the mapping. | True |
| Mapping Group ID | The mapping group ID for the mapping. | True |
| Internal Record Value | The value used internally to match. | True |
| External Field Name | The name of the field to check for the value in the external data source. | True |

The mapping returns the record if a matching table, internal record value, and external field name exist for the specified provider or mapping group.

### Get internal mapping

The **Get internal mapping** flow returns the internal field value that maps to the external field value for a specific table and external field name.

| Parameter | Description | Required |
| --------- | ----------- | -------- |
| Mapping Table | The mapping table to look up for the external value. | True |
| Provider ID | The provider ID for the mapping. | True |
| Mapping Group ID | The mapping group ID for the mapping. | True |
| External Field Name | The name of the field to check for the value in the external data source. | True |
| External Field Value | The value used externally to match. | True |

The mapping returns the record if a matching table, external field value, and external field name exist for the specified provider or mapping group.

## Fulfillment flows

### Create fulfillment tracking

The **Create fulfillment tracking** flow creates a record in the tracking table to associate a tracking number with a fulfillment order or fulfillment return order, and other details.

| Parameter | Description | Required |
| --------- | ----------- | -------- |
| Tracking Number | The tracking number to set for the record. | True |
| CarrierRecordId | A matching record from the **Shipping Carrier** table. | True |
| CarrierServiceId | A matching record from the **Carrier Service** table. | True |
| FulfillmentOrderRecordId | The fulfillment order record to set the tracking number on. | False |
| FulfillmentLineRecordId | The fulfillment order line record to set the tracking number on. | False |
| ShipmentId | The associated shipment ID, if it's available. | False |
| ShipmentCost | The associated shipment cost, if it's available. | False |
| InsuranceCost | The associated insurance cost, if it's available. | False |
| Tax | The associated tax, if it's available. | False |
| SurchargeFee | The associated surcharge fee, if it's available. | False |
| FulfillmentReturnOrderRecordId | The fulfillment return order record to set the tracking number on. | False |

> [!NOTE]
> Either a **FulfillmentOrderRecordId** value or a **FulfillmentReturnOrderRecordId** value is required.

The flow returns the tracking number ID from the **Fulfillment Trackings** table.

### Fulfillment line and aggregated order events

The **Fulfillment line and aggregated order events** flow raises a business event on a fulfillment order line. When this event is raised, the flow verifies that all lines have the same status. If they have the same status, the flow raises the specified fulfillment order–level business event at the header level.

| Parameter | Description | Required |
| --------- | ----------- | -------- |
| FulfillmentLineBusinessEventDefinitionId | The business event to raise on the line entity. | True |
| FulfillmentLineRecordId | The fulfillment order line to raise the initial business event for. | True |
| FulfillmentOrderBusinessEventDefinitionId | The business event to raise on the fulfillment order if all lines have the same status. | True |
| FulfillmentOrderRecordId | The fulfillment order to raise the business event for. | True |
| Payload | The optional JavaScript Object Notation (JSON) payload to pass together with the business event. | False |

The flow returns **IsSuccessful true** if the business event is successfully raised.

## Customer account and contact flows

### Create or update an account

The **Create or update an account** flow creates or updates an existing account, based on the specified JSON payload.

| Parameter | Description | Required |
| --------- | ----------- | -------- |
| Payload | The JSON representation of the account. | True |
| Account ID | The ID of the account to update. | False |

> [!NOTE]
> The **Account** table has specific fields that are required in the JSON payload. To see what fields are required, go to **Dataverse** > **Tables** > **All**, find your table, and select **Columns**. Use the **Required** field to determine what's required.

The flow returns the ID of the created or updated account.

### Create or update a contact

The **Create or update a contact** flow creates or updates an existing contact, based on the specified JSON payload.

| Parameter | Description | Required |
| --------- | ----------- | -------- |
| Payload | The JSON representation of the contact. | True |
| Contact ID | The ID of the account to update. | False |

> [!NOTE]
> The **Contact** table has specific fields that are required in the JSON payload. To see what fields are required, go to **Dataverse** > **Tables** > **All**, find your table, and select **Columns**. Use the **Required** field to determine what's required.

The flow returns the ID of the created or updated contact.

## Order flows and Order product flows

### Sales order creation

The **Sales order creation** flow creates a sales order, based on the specified JSON payload.

| Parameter | Description | Required |
| --------- | ----------- | -------- |
| Payload | The JSON representation of the sales order and lines. | True |
| ProviderId | The ID of the calling provider. | False |

> [!NOTE]
> Both the **Order** table and the **Order Line** table have specific fields that are required in the JSON payload. To see what fields are required, go to **Dataverse** > **Tables** > **All**, find your table, and select **Columns**. Use the **Required** field to determine what's required.

The flow returns the ID of the created sales order.

### Raise lines and aggregated order events

The **Raise lines and Aggregated order events** flow raises a business event on a sales order line. When this event is raised, the flow checks that all lines have the same status. If they have the same status, the flow raises the specified order-level business event at the header level.

| Parameter | Description | Required |
| --------- | ----------- | -------- |
| LineBusinessEventId | The business event to raise on the line entity. | True |
| LineRecordId | The order line to raise the initial business event for. | True |
| OrderBusinessEventId | The business event to raise on the order if all lines have the same status. | True |
| OrderRecordId | The order to raise the business event for. | True |
| Payload | The optional JSON payload to pass together with the business event. | False |

The flow returns **IsSuccessful true** if the business event is successfully raised.

### Raise sales order lines business event

The **Raise sales order lines business event** flow raises a business event for all lines on a sales order.

| Parameter | Description | Required |
| --------- | ----------- | -------- |
| SalesOrderId | The order record for which a business event should be raised for each line. | True |
| BusinessEventId | The order line business event to raise for each line. | True |

The flow returns **IsSuccessful true** if the business event is successfully raised.

### Unit conversion

The **Unit conversion** flow converts a quantity from one unit to another by using the unit conversions that you set up for a product.

| Parameter | Description | Required |
| --------- | ----------- | -------- |
| Quantity | The quantity to convert. | True |
| From unit | The unit to convert from. | True |
| To unit | The unit to convert to. | True |

The flow returns the unit conversion if a conversion exists.

## Miscellaneous flows

### Provider transformer

The **Provider transformer** flow applies a Power Query transformation that you define on a provider, and then returns the transformed data. This flow looks up an active provider instance by ID, and checks for a transformation that has a matching source object name and destination object name.

If the type of transformation is a Dataverse entity, a record ID is required. The flow looks up the record ID for the entity that's defined on the transformation. If a record is found, the flow uses it for the transformation.

If the type of transformation is **JsonPayload**, a value is required for the **Payload** parameter.

| Parameter | Description | Required |
| --------- | ----------- | -------- |
| Provider ID | Any valid globally unique identifier (GUID). | True |
| Source Object Name | The source object name to look up in provider transformations. | True |
| Destination Object Name | The destination object name to look up in provider transformations. | True |
| Payload | The JSON payload to transform if the transformation type is **JsonPayload**. | False |
| Record ID | The record to look up for the entity that's associated with the transformation. | False |

> [!NOTE]
> You must provide either a **Payload** value or a **Record ID** value.
>
> The system replaces the **Provider ID** value, which is a GUID, when you activate a provider. You can enter any GUID for this parameter.

If the flow is successful, it returns a JSON representation of the transformed record.

### Raise a business event

The **Raise a business event** flow raises a business event for the specified entity record and delivers an optional payload.

| Parameter | Description | Required |
| --------- | ----------- | -------- |
| BusinessEventDefinitionId | The GUID of an existing business event. | True |
| EntityRecordId | The record ID of the entity that's associated with the business event. | True |
| Payload | An optional payload to deliver together with the business event. | False |

> [!NOTE]
> The **EntityRecordId** value can be a comma-delimited list of record IDs. If you provide a delimited list, the flow raises a business event for each record.

The flow returns **IsSuccessful true** if the business event is successfully raised.
