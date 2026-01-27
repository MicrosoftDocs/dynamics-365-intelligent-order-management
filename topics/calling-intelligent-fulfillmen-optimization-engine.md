---
title: Call the Intelligent Order Management Fulfillment optimization engine (DOM) via API
description: This article explains how to call the Microsoft Dynamics 365 Intelligent Order Management Fulfillment optimization engine (DOM) via Application programming interface (API).
ms.author: anvenkat
author: anush6121
ms.date: 01/27/2026
ms.custom: 
  - bap-template
ms.topic: how-to
---

# Call the Intelligent Order Management Fulfillment optimization engine (DOM) via API

[!include [banner](includes/banner.md)]

As part of the April 2023 release, you can call the Microsoft Dynamics 365 Intelligent Order Management Fulfillment optimization engine (DOM) from outside the sales order orchestration via Application programming interface (API). Any platform, such as an e-commerce, marketplace, or enterprise resource planning (ERP) platform, can make an API request to Intelligent Order Management to get the optimal fulfillment source, together with shipping options such as carrier shipping rates and estimated delivery date information. If you want to get just a fulfillment plan, the API request should contain, at a minimum, the shipping address, products, and quantity. If you want to get the carrier ship rates and estimated delivery dates in addition to a fulfillment plan, you must pass the carrier information. Currently, the API has been built to call the FedEx rate API to get the shipping rates. However, the payload response is generic for any carrier.

## Prerequisites

The following prerequisites must be met before you use the Intelligent Order Management Fulfillment optimization engine (DOM) via API:

- Install the latest version of Intelligent Order Management (version 1.0.0.6035).
- Set up the fulfillment settings, such as strategies, source lists, and constraints. For more information, see [Fulfillment and Returns Optimization provider overview](fulfillment-returns-optimization.md).
- Set up an inventory visibility provider. For more information, see [Inventory visibility](inventory-visibility.md).
- Ensure that the warehouse ID is mapped to each fulfillment source in the fulfillment source settings.

If you're expecting results that have the shipping options from a FedEx carrier, you must ensure the following setup is completed.

1. Set up a FedEx provider. For more information, see [Set up FedEx provider](set-up-fedex-provider.md).
1. Set up a holiday calendar at **Settings** \> **Fulfillment settings** \> **Holiday calendar**. 
1. Set up a carrier pickup schedule at **Settings** \> **Fulfillment settings** \> **Shipping carriers**. Select the carrier, go to the pickup schedules, and add a new pickup schedule.
1. Ensure that at least one calendar and pickup schedule are assigned to the fulfillment source settings.
1. Ensure that weights and dimensions are in the Shared product table of the product.
1. Ensure that the carrier's Shipping rate factor table is updated with the shipping rate factor and fallback rate information. To access the Shipping rate factor tables, go to **Settings** \> **Fulfillment settings**\> **Shipping carriers** \> **Shipping rate factor**.

## Functionality description

When an API request is made, the Intelligent Order Management Fulfillment optimization engine (DOM) is invoked to return the best fulfillment source for each line, based on the preconfigured fulfillment optimization strategies and constraints. If the request contains a carrier such as FedEx, the carrier pickup schedule is looked at in conjunction with the working calendar of the fulfillment source, and the next available pickup time is sent to the carrier APIs. The response to the DOM API combines both a fulfillment plan and the carrier output, and presents them back to the calling application.

## Sample API request

Create a Power Automate flow–to–Dataverse unbound action to test in your environment.

```json
{{Dataverse URL}}/api/data/v9.2/msdyn_IomDomAPI  
**apiVersion**: 1.0 
{ 
    "fnoCompanyId": "USMF", 
    "orderId": "b16bd573-ad9a-4188-bc08-e5ac5eca776e", 
    "strategyId": null, 
    "carrier": "fedex", 
    "salesOrderOrigin": null, 
    "customerInformation": { 
        "name": "Whole sales", 
        "customerNumber": "US-001", 
        "customerGroup": "10", 
        "customerEmail": "test@microsoft.com" 
    }, 
    "orderDestinationAddress": { 
        "addressType": "Residence", 
        "address1": "537 N St. Francis", 
        "address2": null, 
        "address3": null, 
        "city": "Wichita", 
        "stateOrProvince": "KS", 
        "postalCode": "67214", 
        "phoneNumber": null, 
        "country": "US" 
    }, 
    "lineItems": [ 
        { 
            "lineId": "d5670621-910d-486b-90ca-61d739e9a92e", 
            "itemId": "1000", 
            "quantity": 2, 
            "freeShipping": "No" 
        }, 
        { 
            "lineId": "5c8b423b-c9fe-4ff1-a16e-a75a35d7c424", 
            "itemId": "T0001", 
            "quantity": 2, 
            "freeShipping": "Yes", 
            "dimensions": { 
                "sizeId": "10" 
            } 
        }, 
        { 
            "lineId": "a359a0ec-cded-4eda-b7b0-d7478dff48b9", 
            "itemId": "T0004", 
            "quantity": 2, 
            "freeShipping": "Yes", 
            "dimensions": { 
                "colorId": "black" 
            } 
        } 
    ] 
}
```

## Sample response

```json
Fulfillment Successful 
{ 
    "fulfillmentPlan": { 
        "executionId": "616d8797-0654-4ca7-bae2-c4771521e5f4", 
        "planLines": [ 
            { 
                "orderId": "47c1c1c6-5cc7-4691-a0ae-b50b83b2bba1", 
                "lineId": "34d8209b-3a4b-4c54-a666-76fef99bef63", 
                "quantityToFulfill": 1.0, 
                "orderedQuantity": 1.0, 
                "fulfillmentCenter": "127", 
                "itemId": "1000" 
            } 
        ], 
        "notFulfilledLines": [] 
    } 
} 
```

## API reference guide

This section describes the data type and the header fields in the API request.

| Name | Data type | Description |
|------|-----------|-------------|
| fnoCompanyId | string, optional | The identifier for the company in the system. This field is required if Dataverse is linked to finance and operations apps. |
| salesOrderOrigin | string, optional | The identifier for the order origin in the system. This field is required if inventory must consume from allocated, based on the order origin. |
| orderId | guid string, required | A user-defined order number that's used to identify an order or cart ID in the originating system. |
| strategyId | guid string, optional | The identifier for the fulfillment strategy in Intelligent Order Management. If this identifier isn't provided, the process uses the default strategy that's defined in the system. |
| carrier | string, optional | This field is required to retrieve shipping rates and predictive delivery estimates. The supported value is **FedEx**. |
| orderDestinationAddress | Address, required | The recipient's shipping address. Use the Address model. |
| customerInformation | CustomerInformation, optional | Customer information for the order. Use the Customer Information model. |
| lineItems | OrderDetail, required | An array of order detail objects. Use an array of the Order Detail model. |

### Model

This section describes the fields that use the data model in the API request.

#### Address

This section describes the fields in the address object in the API request.

| Name | Data type | Description |
|------|-----------|-------------|
| addressType | string, optional, values: Business, Residence, Any | A value that indicates whether the specified address is residential. |
| name | string, optional | The name of the person. |
| address1 | string, optional | The first line of the address. |
| address2 | string, optional | The second line of the address. |
| address3 | string, optional | The third line of the address. |
| city | string, required | The city. |
| stateOrProvince | string, required | The state or province. The two-letter ISO Origin State code is required. |
| postalCode | string, required | The postal code. |
| country | string, required | The country or region code. The two-letter ISO Origin Country code is required. |
| phoneNumber | string, optional | The telephone number. |

#### Order detail

This section describes the fields in the order detail section of the API request.

| Name | Data type | Description |
|------|-----------|-------------|
| lineId | guid string, required | The identifier for the order line in the originating system. |
| itemId | string, required | The name of the product that's associated with this line item. The value can't be null. |
| quantity | number, required | The quantity of products that was ordered. | 
| freeShipping | string, optional, values: Yes, No | A value of *Yes* means that product weight is excluded when a rate request is made. |
| dimensions | ProductDimensions, optional | Product dimensions are characteristics that identify a product variant. They use the Product Dimensions model. This field is required if Dataverse is linked to finance and operations apps. Select the product dimensions to identify the product variant. |

#### Product dimensions

This section describes the fields in the product dimensions table.

| Name | Data type | Description |
|------|-----------|-------------|
| colorId | string, optional | The value of the item color. This field is required if Dataverse is linked to finance and operations apps. Select the product dimensions to identify the product variant that you want to work with. |
| sizeId | string, optional | The value of the item size. This field is required if Dataverse is linked to finance and operations apps. Select the product dimensions to identify the product variant that you want to work with. |
| styleId | string, optional | The value of the item style. This field is required if Dataverse is linked to finance and operations apps. Select the product dimensions to identify the product variant that you want to work with. |
| configId | string, optional | The value of the item configuration. This field is required if Dataverse is linked to finance and operations apps. Select the product dimensions to identify the product variant that you want to work with. |
