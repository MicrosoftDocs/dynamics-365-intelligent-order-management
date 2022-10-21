---
author: anvenkat
description: This article describes manual order orchestration in Microsoft Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 10/20/2022
ms.topic: conceptual
ms.author: anvenkat

title: Manual order orchestration in Intelligent Order Management

---

# Manual order orchestration in Intelligent Order Management

[!include [banner](includes/banner.md)]

This article describes manual order orchestration in Microsoft Dynamics 365 Intelligent Order Management.

Manual order orchestration has been introduced in Intelligent Order Management to support a customer service persona in the application.

Manual order orchestration supports the following features:

- The ability to create a manual order and send it through orchestration
- New page fields that can be manually updated during order entry
- Support for bulk changes on **Sales order** and **Order product** pages, based on the order state
- A view for inventory availability checks that is accessible from the **Sales order** and **Product** pages
- Notifications on the order page if the account is on credit hold during order creation
- Support for simple product substitution in manual and e-commerce orders
- Clone order functionality that supports reordering

## Create a new manual order and send it through orchestration

To create a new manual order and send it through orchestration, follow these steps.

1. On the **Sales** page, select **New**.
1. On the **Order** page, enter values for the mandatory fields, and then select **Save**.
1. On the **Order product** page, enter values for the mandatory fields, and then select **Save**.
1. When the order is ready to be processed, select **Orchestrate** so that the order will flow through the published orchestration flow. All the updates that are related to the orchestration run will then be visible in the **Orchestration Step Results** and **Timeline** views on the page.

## New page fields that help improve visibility

The following table describes some of the new page fields.

| Field | Description |
| ----- | ----------- |
| Order type | E-commerce orders will set this field to **Sales order**. A batch job that processes subscription contracts will set it to **Subscription**. For all manually created orders, this field is automatically set to **Sales order**, and it will be read-only. |
| Sales origin | This field is available on the order header and is used to select the order channel that an order is placed through. If dual-write is installed for Intelligent Order Management, this field will show preconfigured values from Dynamics 365 Supply Chain Management. Examples of **Sales origin** values include **e-commerce**, **email**, **phone**, and **fax**. |
| Fulfillment source | This field is available on the **Order product** page, and specifies the warehouse or the store name that the order will be fulfilled from. This field can be manually set during order creation or overwritten during an update. Alternatively, it can be set through orchestration policy or fulfillment optimization. |
| Shipping warehouse | This field is used to specify the warehouse code that matches the warehouse code in Supply Chain Management. The relationship of the **Fulfillment source** value to the **Shipping warehouse** code is maintained at **Settings \> Order settings \> Fulfillment settings \> Sources**. This field can't be manually set. A default value is automatically entered based on the fulfillment source.|
| Bill to address | This field is available on the **Order header** page. The value can be captured either from e-commerce or manually. If the value of this field differs from the **Ship to address** value for the order, the values can be manually captured. |
| Is manual | This flag is set to **Yes** for any orders that are manually created through the **Order** page. It can be used to configure separate orchestration flows for manual orders as required. |
| Customer order reference | This field is used to specify the customer reference for the sales order. It's available for input in a dual-write-enabled instance of the application and maps to the same field in Supply Chain Management. |
| Invoice account | This field specifies the account that is financially responsible for the transaction. By default, the value of this field matches the **Customer Account** value, but it can be manually overwritten to specify a different account. This field is available for input in a dual-write-enabled instance of the application and maps to the same field on the header in Supply Chain Management. This field is mandatory in Supply Chain Management. |
| Shipping site | This field is used to specify the shipping site. It can be manually set in a dual-write-enabled instance, or it can be set through orchestration policy. |

> [!NOTE]
> **Company** is a mandatory field in Supply Chain Management that specifies the legal entity of the customer and the sale transaction. It must be set through orchestration policy. For example, you can use a rule-based policy to set the **Company** field based on the "ship to" country/region or the customer group. After this field is set via orchestration, it will be available on **Order header** and **Order product** pages as a read-only field.

## Support for bulk changes on the Order products page based on the order state

### Bulk-update Fulfillment source values on the Order products page

To do a bulk update of **Fulfillment source** values on the **Order products** page, follow these steps.

1. In the left navigation pane, select **Intelligent Order Management \> Order types \> Orders \> Order Products**.
1. Apply a filter to the **Order product** rows that you want to change, and then select **Edit**.
1. In the dialog box, enter the new field value to apply to all the selected **Order product** rows, and then select **Save**. Only rows that are writable (that is, not read-only) are updated with new values. If an **Order product** row has been sent to fulfillment, the **Edit** button won't be visible, and the following message will be shown at the top of the page: "One or more records are read only. Records cannot be changed."

## Manually cancel rows on the Order products page

To manually cancel one or more rows on the **Order products** page, follow these steps.

1. Go to **Sales order**, and then select the **Order product** rows that you want to cancel.
1. Select **Cancel**. The status of the selected **Order product** rows is changed to **Canceled**. Any **Order product** rows that are already in fulfillment or that have already been delivered will be locked for editing as defined by the order state.

## Determine when an account is on credit hold

To determine when a customer account is on credit hold, follow these steps.

1. Go to **Account \> Accounting tab \> On hold status**. 
1. If the **On hold status** field is set to any value other than **No**, the customer is on credit hold.

As part of the sales order save operation, a check is made against the **On hold status** value of the customer account. If the account is on credit hold, a notification message is shown.

## Simple substitution

The Simple substitution feature lets you substitute and maintain products in the product master data, and reference substitute products during order creation. This feature can be turned on when you must substitute one product with another product for a limited period.

To turn on the Simple substitution feature, follow these steps.

1. Go to **Settings \> General App Settings \> Order handling preferences**.
1. Select **Manage**.
1. Select **Simple Substitution**, and then set the option to **On**.

To maintain the substitute product in **Products**, follow these steps.

1. Go to **Demand Planning \> Products \> Additional Details \> Product Relationships**.
1. Select **New Product Relationship**.
1. In the **Related Product** field, select a substitute product.
1. In the **Sales Relationship Type** field, select **Substitute**.
1. In the **Direction** field, select **Uni-Directional**.

If you maintain more than one substitute item, the application will select the first item that is found.

### How simple substitution works

During order creation (either manual or through an intake provider), a plug-in checks for a substitute product for the requested customer product in the product master data. If a substitute product is found, it appears in the **Existing Product** field, and the requested customer product appears in the **Requested Product** field. Additionally, the **Is Substitute** option on the **Order product** page is set to **Yes**, and both the **Requested Product** and **Is Substitute** fields can viewed on that page. These fields are locked for editing to help prevent unintentional updates. The plug-in runs only during order creation. It doesn't run during order changes.

> [!NOTE]
> If you delete or change a substitute product, you must also delete or change the product relationship accordingly.

## On-hand inventory query on the Sales order products page

An on-hand inventory check is available on both the **Sales order products** page and the **Products** page to provide inventory visibility during order creation. For more information, see [Inventory operations visibility](inventory-visibility.md).

## Clone an order

The Clone order feature supports cloning existing sales orders so that they can be reordered.

To clone an existing sales order, follow these steps.

1. On the **Order listing** page, select the order to clone.
1. On the top menu, select **Clone**. The following message appears: "Cloning in progress. Please wait."

After the message disappears, you will see the new order and order products that were cloned from the selected existing order. Only the mandatory fields are copied from the source order.
