---
author: anvenkat
description: This topic describes Manual Order Orchestration in Dynamics 365 intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 09/16/2022
ms.topic: conceptual
ms.author: anvenkat

title: Manual Order Orchestration in Dynamics 365 Intelligent Order Management

---

# Manual Order Orchestration
## This topic describes **manual order** orchestration within Dynamics 365 Intelligent Order Management.

**Manual order** orchestration is introduced to support a customer service persona within Intelligent Order Management.

Following are the features that come in support of **manual order** in Intelligent Order Management.
1. Create **manual order** and send it through orchestration.
2. New fields introduced in the form that can be captured manually during order entry.
3. Support bulk changes in **Sales order** and **Order products** based on the order **state**.
4. Inventory **Availability Check** view from within **sales order** and **product** forms.
5. Notification on the order form when the account is on **credit hold** during order creation.
6. Support for simple product substitution for **manual orders** and ecom orders.
7. **Clone** order functionality to support reordering.


## Create manual order and send it through orchestration

To create a new order , select **+New** on the sales form and enter the input fields on both **order** form and **order product** form and save. Once the order is ready to be processed, select **Orchestrate** so that the order will flow through published orchestration flow.  All of the updates related to the orchestration run will be visible on the **Orchestration Step Results** and the **Timeline** view on the form.

## New fields introduced in the form for better visibility.

Following are some of the new fields that we have introduced on the form.

1.  **Order type** is defaulted as a **Sales order** for all manually created orders and will be a read only field. This will be set by ecom orders as **Sales order** or by a batch job that processes subscription contracts as **subscription** order. 
1. **Sales origin** will be available on the order header to select the order channel through which an order is placed. If Intelligent Order Management has dual write installed, the **Sales origin** will show pre-configured values from Supply Chain Management. Examples of **Sales origin** values could be ecommerce, email, phone,fax.
1. **Fulfillment source** will be available on the **order product** form and denotes the warehouse or the store name that the order will be fulfilled from. This field can be set manually during order creation or overwritten on change. Alternatively it can also be set by orchestration policy or by fulfillment optimization.
1. **Shipping warehouse** will be used to denote warehouse code that matches the **warehouse** in Supply Chain Managemnt. Note that the relationship of the **Fulfillment source** to the **Shipping warehouse** code is maintained in the path **Settings**>**Order settings**>**Fulfillment settings**>**Sources**.
**Shipping warehouse** cannot be set manually but will default based on the **Fulfillment source** automatically. 
1. **Bill to address** will be available on the **order header** form and can either be captured from ecommerce or manually. If Bill to address is different than the ship to address for the order, they can be captured manually. 
1. **Is manual** will be a flag that will be set to **Yes** for any manually created orders through the **order** form. This field can be used to configure seperate orchestration flows for **manual orders** if required.
1. **Customer order reference** will be used to denote the customer reference for the sales order and maps to the field in Supply chain management. This will be available for input in a dual write enabled instance of the application and will map to the same field in Supply Chain Management.
1. **Invoice account** denotes the account that is financially responsible for the transaction. This will be defaulted on the form and will be the same as **Customer Account**. It can be overwritten to a different **account** manually. This will be available for input in a dual write enabled instance of the application and wll map to the same field on the header in Supply Chain Management.Also note that this is a mandatory field in Supply chain management.
1. **Shipping site** will be used to denote the **site** and can be set manually on a dual write enabled instance or through orchestration policy. 

Note **Company** is a required field in Supply Chain Management. It denotes the legal entity of the customer and the sale transaction.
It is a mandatory field in Supply Chain Management and need to be set through orchestration policy. Example, use a rule based policy to set **Company** based on the ship to country or the customer group, etc. Once this is set through Orchestration, it will be available on Order header and Order product forms as read only field.


## Support for bulk changes in Order products form based on order state.

### Bulk update of **Fulfillment Source** on **Order products**

1. To access **Order Products** on the site map go to **Intelligent Order Management > Order types > Orders > Order Products**
1. Apply filter on **Order Product** rows that need to be changed , and select **edit**. On the fly out screen, provide the new value of the field that will apply to all of the **Order Product** rows selected and then **save**. 
1. You will notice that only those rows that were open for edit would be changed with new value. If an **Order Product** row has been sent to fulfillment, the **edit** button will not be visible and a message **One or more records are read only. Records cannot be changed** will be displayed on the top of the screen..

## Cancelation of Order products

Follow the below procedure for cancelation of **Order products**
1. To cancel one or more **Order product** rows manually, go to **Sales order** and select the **Order product(s)** row(s) that need to be cancelled.
1. Select **Cancel**. The **Order product** row should change the state to **Cancelled**.
1. You will notice that the **Order product** rows that are already in fullfilment or delivered will be locked for edit as defined by the **state**.


## Notification on the order form when the account is on credit hold

1. To access if the customer **Account** is on credit hold, goto **Account** , **Accounting tab** and **On hold status**
1. If **On hold status** is set to anything other than **No**, the customer is on **Credit hold**
1. As part of sales order save, a check is made against the Customer Account **On hold status** and a notificaiton message is displayed informing the user if the Account is on **Credit hold**.

## Simple Substitution

Intelligent Order Management will allow the maintenance of substitute product in the **Products** master data and reference the same during the order creation. This feature can be turned on when there is a need to substitute one product with another for a limited period of time. To turn on the substitution follow the below steps.

1. Goto **Settings > General App Settings > Order handling preferences**. then select **Manage**
1. Select **Simple Substitution** and toggle the switch to **On**

Follow this procedure to maintain the substitute product in **Products**

1. To maintain substitute product goto **Demand Planning > Products > Additional Details >Product Relationships**
1. Select **+New Product Relationship**
1. Choose a substitute product in **Related Product**
1. In **Sales Relationship Type** choose **Substitute**
1. In **Direction** choose **Uni-Directional**

This feature will allow you to maintain one substitute product in Product master. Please note that by maintaining more than one substitute item, the application will only select the first one found.

### How does it work?

During order creation either manually or through an intake provider, a plugin will run to check for a subsitute product in the master data for the customer **requested product**. If there is one found, then the subsitute product will be replaced in **Existing Product** field and the customer requested product will be stored in a field **Requested Product**. A flag on the **order product** form  **Is Substitute** will be set to **Yes**. . Both the new fields **Requested Product** and **Is Substitute** will be available on the form for viewing purposes.These fields will be locked for edit to avoid unintentional user updates. Also the plugin will not run during order change and is set to run only during creation. 

Note: Please note that if the substitute need to be discontinued or changed, product relationship need to be deleted or changed accordingly.

## On hand inventory query on Sales order products form

**On hand inventory** check is available in both **sales order products** form and the **products** form to provide visibility to the inventory during order creation.
Please follow the link here [inventory operational visibility](inventory-operational-visibility.md)

## Clone order

To support reordering of a sales order, **Clone** order feature is introduced on the form. From the Order listing page select the **Order** that needs to be cloned and select **Clone** from the top menu option. You will see a message **Cloning in progress. Please wait**. Once the message disappears, you will see the new order and order products cloned from the selected order. Please note only all mandatory fields are copied from the source order.  

