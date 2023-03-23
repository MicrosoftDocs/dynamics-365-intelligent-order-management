## Calling Intelligent Order Management Fulfillment optimization (DOM) as API

As part of the April'23 release you can call intelligent order management Fulfillment optimization engine (DOM) from outside the sales order orchestration via Application process integration (API).
Any platform such as ecommerce, marketplace or ERP can make an API request to Intelligent Order Management to get the optimal fulfillment source with shipping options such as carrier shipping rates and estimated delivery dates information. 
The request API at the minimum should contain the shipping address, products and quantity when looking for just a fulfillment plan. In addition to fulfillment plan if you would like to get the carrier ship rates and estimated delivery dates, you must pass the carrier information.  Currently the API has been built to call Fedex rate API to get the shipping rates.

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

## Functionality description

When API request is made, Intelligent Order Management DOM engine is invoked to return the best fulfillment source for each of the lines based on the preconfigured fulfillment optimization strategies and constraints. If the request contains a carrier such as Fedex, the carrier pick up schedule is looked at in conjunction with the working calendar of the fulfillment source to send the next available pick up time to the carrier API's. The response to the DOM API will combine both a fulfillment plan and the carrier output and present back to the calling application.

## Sample request API

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

Sample Response API

{
    "fulfillmentPlan": {
        "executionId": "fc7fd8ad-8b5d-49de-a741-199faff2cc7f",
        "planLines": [
            {
                "orderId": "b16bd573-ad9a-4188-bc08-e5ac5eca776e",
                "lineId": "d5670621-910d-486b-90ca-61d739e9a92e",
                "quantityToFulfill": 2.0,
                "orderedQuantity": 2.0,
                "fulfillmentCenter": "12",
                "itemId": "USMF1000"
            },
            {
                "orderId": "b16bd573-ad9a-4188-bc08-e5ac5eca776e",
                "lineId": "5c8b423b-c9fe-4ff1-a16e-a75a35d7c424",
                "quantityToFulfill": 2.0,
                "orderedQuantity": 2.0,
                "fulfillmentCenter": "12",
                "itemId": "USMFA0001"
            }
        ],
        "notFulfilledLines": []
    },
    "shippingCarrierResponse": {
        "carrier": {
            "rateInfo": {
                "isFallbackResponse": false,
                "output": [
                    {
                        "serviceType": "PRIORITY_OVERNIGHT",
                        "serviceName": "FedEx Priority Overnight®",
                        "packagingType": "YOUR_PACKAGING",
                        "ratedShipmentDetails": {
                            "rateType": "ACCOUNT",
                            "ratedWeightMethod": "ACTUAL",
                            "totalDiscounts": 0.0,
                            "totalBaseCharge": 423.10799999999995,
                            "totalNetCharge": 509.628,
                            "totalNetFedExCharge": 509.628,
                            "shipmentRateDetail": {
                                "rateZone": "05",
                                "dimDivisor": 139,
                                "fuelSurchargePercent": 18.5,
                                "totalSurcharges": 86.52,
                                "totalFreightDiscount": 0.0,
                                "surCharges": [
                                    {
                                        "type": "FUEL",
                                        "description": "Fuel Surcharge",
                                        "amount": 79.55999999999999
                                    },
                                    {
                                        "type": "RESIDENTIAL_DELIVERY",
                                        "description": "Residential delivery surcharge",
                                        "amount": 6.96
                                    }
                                ],
                                "pricingCode": "PACKAGE",
                                "totalBillingWeight": {
                                    "units": "LB",
                                    "value": 40.0
                                },
                                "currency": "USD",
                                "rateScale": "1552"
                            }
                        },
                        "fulfillmentCenter": "12",
                        "carrierEdd": {
                            "packageservice": "PO",
                            "eddConfidenceScore": 0.5881563150482412,
                            "edtwConfidenceScore": 0.8745849622670719,
                            "edd": "2023-03-20T00:00:00",
                            "edtwhistorical": [
                                "2023-03-20T07:39:00",
                                "2023-03-20T11:39:00"
                            ]
                        }
                    },
                    {
                        "serviceType": "STANDARD_OVERNIGHT",
                        "serviceName": "FedEx Standard Overnight®",
                        "packagingType": "YOUR_PACKAGING",
                        "ratedShipmentDetails": {
                            "rateType": "ACCOUNT",
                            "ratedWeightMethod": "ACTUAL",
                            "totalDiscounts": 0.0,
                            "totalBaseCharge": 402.648,
                            "totalNetCharge": 485.388,
                            "totalNetFedExCharge": 485.388,
                            "shipmentRateDetail": {
                                "rateZone": "05",
                                "dimDivisor": 139,
                                "fuelSurchargePercent": 18.5,
                                "totalSurcharges": 82.74,
                                "totalFreightDiscount": 0.0,
                                "surCharges": [
                                    {
                                        "type": "FUEL",
                                        "description": "Fuel Surcharge",
                                        "amount": 75.78
                                    },
                                    {
                                        "type": "RESIDENTIAL_DELIVERY",
                                        "description": "Residential delivery surcharge",
                                        "amount": 6.96
                                    }
                                ],
                                "pricingCode": "PACKAGE",
                                "totalBillingWeight": {
                                    "units": "LB",
                                    "value": 40.0
                                },
                                "currency": "USD",
                                "rateScale": "1349"
                            }
                        },
                        "fulfillmentCenter": "12",
                        "carrierEdd": {
                            "packageservice": "SO",
                            "eddConfidenceScore": 0.8621038875178946,
                            "edtwConfidenceScore": 0.5791687950336222,
                            "edd": "2023-03-20T00:00:00",
                            "edtwhistorical": [
                                "2023-03-20T09:10:00",
                                "2023-03-20T13:10:00"
                            ]
                        }
                    },
                    {
                        "serviceType": "FEDEX_2_DAY",
                        "serviceName": "FedEx 2Day®",
                        "packagingType": "YOUR_PACKAGING",
                        "ratedShipmentDetails": {
                            "rateType": "ACCOUNT",
                            "ratedWeightMethod": "ACTUAL",
                            "totalDiscounts": 0.0,
                            "totalBaseCharge": 228.07500000000002,
                            "totalNetCharge": 278.8625,
                            "totalNetFedExCharge": 278.8625,
                            "shipmentRateDetail": {
                                "rateZone": "05",
                                "dimDivisor": 139,
                                "fuelSurchargePercent": 18.5,
                                "totalSurcharges": 50.7875,
                                "totalFreightDiscount": 0.0,
                                "surCharges": [
                                    {
                                        "type": "FUEL",
                                        "description": "Fuel Surcharge",
                                        "amount": 43.537499999999994
                                    },
                                    {
                                        "type": "RESIDENTIAL_DELIVERY",
                                        "description": "Residential delivery surcharge",
                                        "amount": 7.25
                                    }
                                ],
                                "pricingCode": "PACKAGE",
                                "totalBillingWeight": {
                                    "units": "LB",
                                    "value": 40.0
                                },
                                "currency": "USD",
                                "rateScale": "6046"
                            }
                        },
                        "fulfillmentCenter": "12",
                        "carrierEdd": {
                            "packageservice": "ES",
                            "eddConfidenceScore": 0.5292284666411166,
                            "edtwConfidenceScore": 0.602369554989657,
                            "edd": "2023-03-21T00:00:00",
                            "edtwhistorical": [
                                "2023-03-21T10:22:00",
                                "2023-03-21T14:22:00"
                            ]
                        }
                    },
                    {
                        "serviceType": "GROUND_HOME_DELIVERY",
                        "serviceName": "FedEx Home Delivery®",
                        "packagingType": "YOUR_PACKAGING",
                        "ratedShipmentDetails": {
                            "rateType": "ACCOUNT",
                            "ratedWeightMethod": "ACTUAL",
                            "totalDiscounts": 0.0,
                            "totalBaseCharge": 45.263999999999996,
                            "totalNetCharge": 59.808,
                            "totalNetFedExCharge": 59.808,
                            "shipmentRateDetail": {
                                "rateZone": "5",
                                "dimDivisor": 0,
                                "fuelSurchargePercent": 16.25,
                                "totalSurcharges": 14.543999999999999,
                                "totalFreightDiscount": 0.0,
                                "surCharges": [
                                    {
                                        "type": "FUEL",
                                        "description": "Fuel Surcharge",
                                        "level": "PACKAGE",
                                        "amount": 8.363999999999999
                                    },
                                    {
                                        "type": "RESIDENTIAL_DELIVERY",
                                        "description": "Residential surcharge",
                                        "level": "PACKAGE",
                                        "amount": 6.180000000000001
                                    }
                                ],
                                "totalBillingWeight": {
                                    "units": "LB",
                                    "value": 40.0
                                },
                                "currency": "USD"
                            }
                        },
                        "fulfillmentCenter": "12",
                        "carrierEdd": {
                            "packageservice": "HD",
                            "eddConfidenceScore": 0.3794860861205141,
                            "edtwConfidenceScore": 0.6564261560728266,
                            "edd": "2023-03-20T00:00:00",
                            "edtwhistorical": [
                                "2023-03-20T10:33:00",
                                "2023-03-20T14:33:00"
                            ]
                        }
                    }
                ]
            }
        }
    }
}
