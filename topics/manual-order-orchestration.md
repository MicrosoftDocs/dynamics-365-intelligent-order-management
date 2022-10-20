---
author: anvenkat
description: This topic describes manual order orchestration in Microsoft Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 10/20/2022
ms.topic: conceptual
ms.author: anvenkat

title: Manual order orchestration in Intelligent Order Management

---

# Manual order orchestration in Intelligent Order Management

[!include [banner](includes/banner.md)]

This topic describes manual order orchestration in Microsoft Dynamics 365 Intelligent Order Management.

Manual order orchestration has been introduced in Intelligent Order Management to support a customer service persona within the application.

Manual order orchestration supports the following features:

- The ability to reate a manual order and send it through orchestration.
- New form fields that can be manually captured during order entry.
- Support of bulk changes in **Sales order** and **Order product** forms, based on the order state.
- An inventory availability check view accessible from within the **Sales order** and **Product** forms.
- Notifications on the order form when the account is on credit hold during order creation.
- Support for simple product substitution in manual and e-commmerce orders.
- Clone order functionality to support reordering.

## Create a new manual order and send it through orchestration

To create a new manual order and send it through orchestration, follow these steps.

1. On the sales form, select **+New**  
1. On the  **Order** form, enter values for the mandatory fields, and then select **Save**.
1. On the **Order product** form, enter values for the mandatory fields, and then select **Save**.
1. When the order is ready to be processed, select **Orchestrate** so that the order will flow through the published orchestration flow. All of the updates related to the orchestration run will then be visible in the **Orchestration Step Results** and the **Timeline** views on the form.

## New fields introduced in the form for better visibility

Following are some of the new fields that we have introduced on the form.

| Field | Description |
| ----- | ----------- |
| **Order type** | Defaulted as a **Sales order** for all manually created orders and will be a read-only field. This will be set by e-commmerce orders as **Sales order** or by a batch job that processes subscription contracts as **subscription** order. |
| **Sales origin**  | Available on the order header to select the order channel through which an order is placed. If Intelligent Order Management has dual-write installed, the **Sales origin** will show preconfigured values from Supply Chain Management. Examples of **Sales origin** values could be e-commerce, email, phone, fax. |
| **Fulfillment source**  | Available on the **order product** form and denotes the warehouse or the store name that the order will be fulfilled from. This field can be set manually during order creation or overwritten on change. Alternatively it can also be set by orchestration policy or by fulfillment optimization. |
| **Shipping warehouse**  | Used to specify the warehouse code that matches the warehouse code in Supply Chain Managemnt. The relationship of the **Fulfillment source** to the **Shipping warehouse** code is maintained at **Settings \> Order settings \> Fulfillment settings \> Sources**.  Can't be set manually but will automatically default based on the fulfillment source.|
| **Bill to address**  | Available on the **Order header** form and can either be captured from e-commerce or manually. If the **Bill to address** value is different than the **Ship to address** value for the order, the values can be captured manually.  |
| **Is manual**  | A flag that will be set to **Yes** for any manually created orders through the **order** form. This field can be used to configure seperate orchestration flows for **manual orders** if required. |
| **Customer order reference**  | Used to specify the customer reference for the sales order and maps to the field in Supply chain management. This will be available for input in a dual write enabled instance of the application and will map to the same field in Supply Chain Management. |
| **Invoice account**  | Specifies the account that is financially responsible for the transaction. This will be defaulted on the form and will be the same as **Customer Account**. It can be overwritten to a different **account** manually. This will be available for input in a dual write enabled instance of the application and wll map to the same field on the header in Supply Chain Management.Also note that this is a mandatory field in Supply chain management. |
| **Shipping site**  | Used to specify the shipping site. Can be set manually on a dual-write enabled instance, or through orchestration policy. |

> [!NOTE]
> **Company** is a mandatory field in Supply Chain Management that denotes the legal entity of the customer and the sale transaction. It must be set through orchestration policy. For example, use a rule based policy to set **Company** based on the ship to country or the customer group, etc. Once this is set through Orchestration, it will be available on Order header and Order product forms as read only field.

## Support for bulk changes in Order products form based on order state

### Bulk update of Fulfillment Source on Order products

To do a bulk update of **Fulfillment Source** on the **Order products** form, follow these steps.

1. To access **Order Products** on the site map go to **Intelligent Order Management \> Order types \> Orders \> Order Products**.
1. Apply filter on **Order Product** rows that need to be changed , and select **edit**. On the fly out screen, provide the new value of the field that will apply to all of the **Order Product** rows selected and then **save**. 
1. You will notice that only those rows that were open for edit would be changed with new value. If an **Order Product** row has been sent to fulfillment, the **edit** button will not be visible and a message **One or more records are read only. Records cannot be changed** will be displayed on the top of the screen..

## Cancel Order product rows manually

To cancel **Order product** rows manually, follow these steps.

1. To cancel one or more **Order product** rows manually, go to **Sales order** and select the **Order product(s)** row(s) that need to be cancelled.
1. Select **Cancel**. The **Order product** row should change the state to **Cancelled**. The **Order product** rows that are already in fullfilment or delivered will be locked for edit as defined by the **state**.

## Determine when an account is on credit hold

To determine when a customer account is on credit hold, follow these steps.

1. Go to **Account \> Accounting tab \> On hold status**, To access if the customer **Account** is on credit hold, 
1. If **On hold status** is set to anything other than **No**, then the customer is on credit hold.

As part of the sales order save operation, a check is made against the customer account **On hold status** and a notification message that the account is on credit hold is displayed.

## Simple substitution

The simple substitution feature allows you to substitute and maintain products in the product master data and reference substitute products during order creation. This feature can be turned on when there is a need to substitute one product with another product for a limited period of time. 

To turn on the simple substitution feature, follow these steps.

1. Go to **Settings \> General App Settings \> Order handling preferences**.
1. Select **Manage**.
1. Select **Simple Substitution**, and then toggle the switch to **On**.

To maintain the substitute product in **Products**, follow these steps.

1. Go to **Demand Planning \> Products \> Additional Details \> Product Relationships**.
1. Select **+New Product Relationship**.
1. For **Related Product**, select a substitute product.
1. For **Sales Relationship Type**, select **Substitute**
1. For **Direction**, select **Uni-Directional**.

When maintaining more than one substitute item, the application will select the first item found.

### How does it work?

During order creation (either manually or through an intake provider), a plug-in runs to check for a substitute product for the requested customer product in the product master data. If a substitution is found, then the subsitute product appears in the **Existing Product** field and the requested customer product appears in the **Requested Product** field. Also, on the **Order product** form, the **Is Substitute** toggle is set to **Yes**, and both the **Requested Product** and **Is Substitute** fields will be viewable on the form. These fields will be locked to avoid unintentional updates. The plugin only runs during creation doesn't run during order change. 

> [!NOTE]
> If you delete or change a substitute product, you must also delete or change the product relationship accordingly.

## On hand inventory query on Sales order products form

An on hand inventory check is available on both the **Sales order products** and **Products** forms to provide inventory visibility during order creation.
For more information, see [Inventory operations visibility](inventory-visibility.md).

## Clone order

The clone order feature support the reordering of sales orders.

To clone an existing sales order, follow these steps.

1. On the **Order listing** page, select the order that you want to clone.
1. On the top menu, select **Clone**. A **Cloning in progress. Please wait** message appears. 

Once the message disappears, you will see the new order and order products cloned from the selected order. Only the mandatory fields are copied from the source order.  
