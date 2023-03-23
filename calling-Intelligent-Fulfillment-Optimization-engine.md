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

When API request is made, Intelligent Order Management DOM engine is invoked o
