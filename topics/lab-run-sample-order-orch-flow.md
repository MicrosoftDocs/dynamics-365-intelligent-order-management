---
author: josaw1
description: This topic describes the steps required to run a sample order orchestration flow in Microsoft Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 09/01/2021
ms.topic: how-to
ms.author: josaw

title: Run sample order orchestration flow

---

# Run sample order orchestration flow

[!include [banner](includes/banner.md)]

This topic describes the steps required to run a sample order orchestration flow in Microsoft Dynamics 365 Intelligent Order Management.

## Set up customer

To set up a customer, follow these steps.

1. Go to **Customers \> Accounts**.
1. Select **New**.
1. For **Account Name**, enter "DefaultAccount-IOMLabOrderIntakeProvider".
1. Select **Save & close**.

## Set up account mapping 

To set up account mapping, follow these steps.

1. In the lower right corner of your Intelligent Order Management application screen, change the area from **IOM** to **Configurations**. If you use a left-to-right (LTR) language, this setting is located in the lower left corner of your application screen. 
1. Go to **Mappings \> Accounts**.
1. Select **New**.
1. On the **New IOM Account Mapping** page, do the following: 
    1. For **IOM Provider**, enter "IOMLabOrderIntakeProvider".
    1. For **Customer**, enter "DefaultAccount-IOMLabOrderIntakeProvider".
    1. For **External Field Name**, enter "ProviderName".
    1. For **External Field Value**, enter "IOMLabOrderIntakeProvider".
1. Select **Save & close**.

## Set up pricelist mapping

To set up pricelist mapping, follow these steps.

1. Go to **Mappings \> Price Lists**.
1. Select **New**.
1. On the **New IOM Price List Mapping** page, do the following:
    1. For **IOM Provider**, enter "IOMLabOrderIntakeProvider".
    1. For **Price list**, enter "MasterPriceList".
    1. For **External Field Name**, enter "ProviderName".
    1. For **External Field Value**, enter "IOMLabOrderIntakeProvider".
1. Select **Save & close**.

## Set up unit mapping

To set up unit mapping, follow these steps.

1. Go to **Mappings \> Units**.
1. Select **New**.
1. On the **New IOM Unit Mapping** page, do the following:
    1. For **IOM Provider**, enter "IOMLabOrderIntakeProvider".
    1. For **Unit**, enter "ea".
    1. For **External Field Name**, enter "unit".
    1. For **External Field Value**, enter "each".
1. Select **Save & close**.

## Set up product mapping

To set up product mapping, follow these steps.

1. Go to **Mappings \> Products**.
1. Select **New**.
1. On the **New IOM Product Mapping** page, do the following:
    1. For **IOM Provider**, enter "IOMLabOrderIntakeProvider".
    1. For **Product**, enter "Barista Home".
    1. For **External Field Name**, enter "sku".
    1. For **External Field Value**, enter "883988211855".
1. Select **Save & close**.

## Sample sales order payload

```JSON
{
  "ordernumber": "IOMLabOrder001",
  "shiptocity": "BELLEVUE",
  "shiptostateorprovince": "WA",
  "shiptocountry": "US",
  "shiptozip": "98007",
  "billtocity": "BELLEVUE",
  "billtostateorprovince": "WA",
  "billtocountry": "US",
  "billtozip": "98007",
  "orderdetails": [
    {
      "sku": "883988211855",
      "unit": "each",
      "quantity": 110
    }
  ]
}
```

## Lab scenario

1. Order comes into Intelligent Order Management as email attachment.
1. Validate order header to make sure "ship to"" country is US.
1. Validate order line to make sure quantity is greater than 1.
1. Route order based on quantity.
    1. If quantity \>= 100, send to Seattle store.
    1. If quantity \< 100, send to Chicago store.
1. If order is routed to Seattle store, emails with fulfillment order attached will be sent.
1. If order is routed to Chicago store, requests with fulfillment order as payload will be sent to RequestBin.

## Test runs

### Test run 1

To complete test run 1, follow these steps.

1. Save the sample sales order payload as a JSON file and attach it to an email with the subject "IOMLabOrderIntakeOrder".
1. Send the email to the Outlook account used previously to set up IOMLabOrderIntake provider. 

You will receive two emails back with attachment with fulfillment details. The order status reason will be set to "Sent To Fulfillment".

### Test run 2

To complete test run 2, follow these steps.

1. Change the **ordernumber** value to "IOMLabOrder002" and the **quantity** value to 10.
1. Save the sample sales order payload as a JSON file and attach it to an email with the subject "IOMLabOrderIntakeOrder".
1. Send the email to the Outlook account used previously to set up IOMLabOrderIntake provider.

You will receive two requests with fulfillment details in your RequestBin. The order status reason will be set to "Sent To Fulfillment".

### Test run 3

To complete test run 3, follow these steps.

1. Change the **ordernumber** value to "IOMLabOrder003" and the **quantity** value to "1".
1. Save the sample sales order payload as a JSON file and attach it to an email with the subject "IOMLabOrderIntakeOrder".
1. Send the email to the Outlook account used previously to set up IOMLabOrderIntake provider.

The order will fail the line minimum quantity validation, with the header status reason "Order Validation Failed" and the line status reason "Order Line Validation Failed".

### Test run 4

To complete test run 4, follow these steps.

1. Change the **ordernumber** value to "IOMLabOrder004" and the **shiptocountry** value to "CA".
1. Save the sample sales order payload as a JSON file and attach it to an email with the subject "IOMLabOrderIntakeOrder".
1. Send the email to the Outlook account used previously to set up IOMLabOrderIntake provider.

The order will fail the header ship to country validation, with status reason "Order Validation Failed".
