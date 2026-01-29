---
author: josaw1
description: Learn about the steps required to run a sample order orchestration flow in Microsoft Dynamics 365 Intelligent Order Management.
ms.date: 01/28/2026
ms.custom: 
  - bap-template
ms.topic: how-to
ms.author: anvenkat
title: Run sample order orchestration flow

---

# Run sample order orchestration flow

[!include [banner](includes/banner.md)]

This article describes the steps required to run a sample order orchestration flow in Microsoft Dynamics 365 Intelligent Order Management.

## Set up customer

To set up a customer, follow these steps:

1. Go to **Customers \> Accounts**.
1. Select **New**.
1. For **Account Name**, enter "DefaultAccount-IOMLabOrderIntakeProvider".
1. Select **Save & close**.

## Set up account mapping

To set up account mapping, follow these steps:

1. In the lower right corner of your Intelligent Order Management application screen, change the area from **IOM** to **Configurations**. If you use a left-to-right (LTR) language, you find this setting in the lower left corner of your application screen.
1. Go to **Mappings \> Accounts**.
1. Select **New**.
1. On the **New IOM Account Mapping** page, enter the following information:
    1. For **Mapping Group**, enter "Default Mapping Group".
    1. For **Customer**, enter "DefaultAccount-IOMLabOrderIntakeProvider".
    1. For **External Field Name**, enter `ProviderName`.
    1. For **External Field Value**, enter `IOMLabOrderIntakeProvider`.
1. Select **Save & close**.

## Set up pricelist mapping

To set up pricelist mapping, follow these steps:

1. Go to **Mappings \> Price Lists**.
1. Select **New**.
1. On the **New IOM Price List Mapping** page, complete the following fields:
    1. For **IOM Provider**, enter `IOMLabOrderIntakeProvider`.
    1. For **Price list**, enter `MasterPriceList`.
    1. For **External Field Name**, enter `ProviderName`.
    1. For **External Field Value**, enter `IOMLabOrderIntakeProvider`.
1. Select **Save & close**.

## Set up unit mapping

To set up unit mapping, follow these steps:

1. Go to **Mappings \> Units**.
1. Select **New**.
1. On the **New IOM Unit Mapping** page, complete the following fields:
    1. For **IOM Provider**, enter `IOMLabOrderIntakeProvider`.
    1. For **Unit**, enter `ea`.
    1. For **External Field Name**, enter `unit`.
    1. For **External Field Value**, enter `each`.
1. Select **Save & close**.

## Set up product mapping

To set up product mapping, follow these steps:

1. Go to **Mappings \> Products**.
1. Select **New**.
1. On **New IOM Product Mapping**, complete the following steps:
    1. For **IOM Provider**, enter `IOMLabOrderIntakeProvider`.
    1. For **Product**, enter `Barista Home`.
    1. For **External Field Name**, enter `sku`.
    1. For **External Field Value**, enter `883988211855`.
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

1. An order arrives in Intelligent Order Management as an email attachment.
1. The system validates the order header to make sure the "ship to" country/region is US.
1. The system validates the order line to make sure the quantity is greater than 1.
1. The system routes the order based on quantity.
    1. If quantity is greater than or equal to 100, the order goes to the Seattle store.
    1. If quantity is less than 100, the order goes to the Chicago store.
1. If the order goes to the Seattle store, the system sends emails with the fulfillment order attached.
1. If the order goes to the Chicago store, the system sends requests with the fulfillment order as the payload to RequestBin.

## Test runs

### Test run 1

To complete test run 1, follow these steps:

1. Save the sample sales order payload as a JSON file. Attach the file to an email with the subject "IOMLabOrderIntakeOrder".
1. Send the email to the Outlook account that you previously used to set up the IOMLabOrderIntake provider. 

You receive two emails back with attachment with fulfillment details. The order status reason is set to "Sent To Fulfillment".

### Test run 2

To complete test run 2, follow these steps:

1. Change the **ordernumber** value to "IOMLabOrder002" and the **quantity** value to 10.
1. Save the sample sales order payload as a JSON file. Attach the file to an email with the subject "IOMLabOrderIntakeOrder".
1. Send the email to the Outlook account that you previously used to set up the IOMLabOrderIntake provider.

You receive two requests with fulfillment details in your RequestBin. The order status reason is set to "Sent To Fulfillment".

### Test run 3

To complete test run 3, follow these steps:

1. Change the **ordernumber** value to "IOMLabOrder003" and the **quantity** value to "1".
1. Save the sample sales order payload as a JSON file. Attach the file to an email with the subject "IOMLabOrderIntakeOrder".
1. Send the email to the Outlook account that you previously used to set up the IOMLabOrderIntake provider.

The order fails the line minimum quantity validation, with the header status reason "Order Validation Failed" and the line status reason "Order Line Validation Failed".

### Test run 4

To complete test run 4, follow these steps:

1. Change the **ordernumber** value to "IOMLabOrder004" and the **shiptocountry** value to "CA".
1. Save the sample sales order payload as a JSON file. Attach the file to an email with the subject "IOMLabOrderIntakeOrder".
1. Send the email to the Outlook account that you previously used to set up the IOMLabOrderIntake provider.

The order fails the header ship to country validation. The status reason is "Order Validation Failed".
