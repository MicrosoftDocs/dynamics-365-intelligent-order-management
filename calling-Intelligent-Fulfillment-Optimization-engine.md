## Calling Intelligent Order Management Fulfillment optimization (DOM) as API

As part of the April'23 release you can call intelligent order management Fulfillment optimization engine (DOM) from outside the sales order orchestration via Application process integration (API).
Any platform such as ecommerce, marketplace or ERP can make an API request to Intelligent Order Management to get the optimal fulfillment source with shipping options such as carrier shipping rates and estimated delivery dates information. 
The request API at the minimum should contain the shipping address, products and quantity when looking for just a fulfillment plan. In addition to fulfillment plan if you would like to get the carrier ship rates and estimated delivery dates, you must pass the carrier information.  Currently the API has been built to call Fedex rate API to get the shipping rates. However the payload respoonse is quite generic for any carrier.

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
  "strategyId": "5b9d0cf8-77bd-ed11-b596-0022480c45fe",
  "carrier": "fedex",
  "salesOrderOrigin": null,
  "orderDestinationAddress": {
    "addressType": "Residence",
    "address1": "537 N St. Francis",
    "city": "edina",
    "stateOrProvince": "MN",
    "postalCode": "55437",
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
      "itemId": "A0001",
      "quantity": 2,
      "freeShipping": "No",
     }
   ]
}


