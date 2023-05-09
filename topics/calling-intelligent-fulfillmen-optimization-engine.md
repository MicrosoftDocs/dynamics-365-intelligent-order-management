# Calling Intelligent Order Management Fulfillment optimization (DOM) as API

As part of the April'23 release you can call intelligent order management Fulfillment optimization engine (DOM) from outside the sales order orchestration via Application process integration (API).
Any platform such as ecommerce, marketplace or ERP can make an API request to Intelligent Order Management to get the optimal fulfillment source with shipping options such as carrier shipping rates and estimated delivery dates information. 
The request API at the minimum should contain the shipping address, products and quantity when looking for just a fulfillment plan. In addition to fulfillment plan if you would like to get the carrier ship rates and estimated delivery dates, you must pass the carrier information.  Currently the API has been built to call Fedex rate API to get the shipping rates. However the payload response is quite generic for any carrier.

## Pre-requisites

1. Install latest version of Intelligent Order Management( version 1.0.0.6035)
2. Set up fulfillment settings such as Strategies, source lists and constraints. For more information please refer to [Fulfillment and Returns Optimization provider overview](fulfillment-returns-optimization.md)
3. Set up inventory visibility provider. For more information refer to [Inventory visibility](inventory-visibility.md)
4. Ensure that the **warehouse id** is mapped to each of the fulfillment sources in **Fulfillment source** settings.

If you are expecting the results with the shipping options from Fedex carrier you must ensure the following is set up.

1. Set up Fedex provider. For more information please refer to [Set up Fedex provider](set-up-fedex-provider.md)
2. Set up holiday calendar in **Settings**>**Fulfillment settings**>**Holiday calendar**. 
3. Set up carrier pick up schedules in **Settings**>**Fulfillment settings**>**Shipping carriers** Select carrier and go to pick up schedules and add new **pick up schedule**
4. Ensure atleast one calendar and pick up schedule is assigned to **Fulfillment source** settings.
5. . Ensure weights and dims are in **shared product** table of the product. 
6. Ensure the carrier shipping rate factors table is updated with the shipping rate factor and fall back rate information. To access the shipping rate factor tables go to **Settings**> **Fulfilment settings** > **Shipping carriers** > **Shipping rate factor**

## Functionality description

When API request is made, Intelligent Order Management DOM engine is invoked to return the best fulfillment source for each of the lines based on the preconfigured fulfillment optimization strategies and constraints. If the request contains a carrier such as Fedex, the carrier pick up schedule is looked at in conjunction with the working calendar of the fulfillment source to send the next available pick up time to the carrier API's. The response to the DOM API will combine both a fulfillment plan and the carrier output and present back to the calling application.

## Sample request API
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

## Sample response

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

## API reference guide

| Name | Data type | Description |
|-------------------------|-------------------------|--------------------------|
| fnoCompanyId | string, optional | Identifier for the company in the system. Required if Dataverse is linked to FNO. |
| salesOrderOrigin | string, optional | Identifier for the order origin in the system. Required if inventory must consume from allocated based on order origin. |
| orderId | guid string, required | A user-defined order number is used to identify an order or cart id in the originating system. |
| strategyId | guid string, optional | Identifier for the fulfillment strategy in IOM. If not provided, process will use the default strategy defined in system. |
| carrier | string, optional | Required to retrieve shipping rates and predictive delivery estimates. Supported value is FedEx |
| orderDestinationAddress | Address, required | The recipient's shipping address. Use the Address model. |
| customerInformation | CustomerInformation, optional | Customer Information of the Order. Use the Customer Information model. |
| lineItems | OrderDetail, required | An array of order detail objects. Use an array of Order Detail model. |

### Model
### Address
| Name | Data type | Description |
|-------------------------|-------------------------|--------------------------|
| addressType | string, optional Values: Business, Residence, Any| Specifies whether the given address is residential. |           
| name | string, optional | First line of address. | Name of person. |
| address1 | string, optional | First line of address. . |
| address2 | string, optional | Second line of address. |
| address3 | string, optional | Third line of address. |
| city | string, reqyured | City. |
| stateOrProvince | string, required | State. The two-letter ISO Origin State code is required. |
| postalCode | string, required | Postal Code |
| country | string, required | Country Code. The two-letter ISO Origin Country code is required. |
| phoneNumber | string, optional | Telephone number. |

### Order detail
| Name | Data type | Description |
|-------------------------|-------------------------|--------------------------|
| lineId | guid string, required | An identifier for the order line in the originating system.|
| itemId | string, required | The name of the product is associated with this line item. Cannot be null. |
| quantity | number, required | The quantity of products ordered. | 
| freeShipping | string, optional;values:Yes, No | Yes means product weight will be excluded when making rate request. |
| dimensions | ProductDimensions, optional | Product dimensions are characteristics that serve to identify a product variant. Use the Product Dimensions model.Required                                             if Dataverse is linked to FNO and select the product dimensions to identify the product variant. |

### Product Dimensions
| Name | Data type | Description |
|-------------------------|-------------------------|--------------------------|
| colorId | string, optional  | The value of the item color. Required if Dataverse is linked to FNO and select the product dimensions to identify the product variant                                   that you want to work with. |
| sizeId | string, optional | The value of the item size Required if Dataverse is linked to FNO and select the product dimensions to identify the product variant that                               you want to work with. |
| styleId | string, optional | The value of the item style Required if Dataverse is linked to FNO and select the product dimensions to identify the product variant                                    that you want to work with. |
| configId | string, optional | The value of the item configuration Required if Dataverse is linked to FNO and select the product dimensions to identify the product                                   variant that you want to work with. |



