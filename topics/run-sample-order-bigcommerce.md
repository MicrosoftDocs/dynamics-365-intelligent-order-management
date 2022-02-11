---
author: josaw1
description: This topic describes the steps required to run a sample order orchestration flow from BigCommerce to Microsoft Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 02/11/2022
ms.topic: conceptual
ms.author: josaw

title: Run sample order orchestration flow from BigCommerce

---

# Run sample order orchestration flow from BigCommerce

[!include [banner](includes/banner.md)]

This topic details the setup steps required to run a sample order orchestration flow from BigCommerce to Dynamics 365 Intelligent Order Management. 

## Prerequisites

You must set up BigCommerce as a provider in Intelligent Order Management before you can proceed. To set up BigCommerce as a provider, see [Set up BigCommerce provider](set-up-bigcommerce-provider.md).

## Set up customer

First, you need to set up a customer in Intelligent Order Management. To set up a customer, follow these steps.

1. Go to **Customers \> Accounts**.
1. Select **New**.
1. In the **Account Name** field, enter "TestBCAccount".
1. Select **Save & close**.

## Set up account mapping 

Next, set up account mapping.

1. In the lower right corner of any Intelligent Order Management page, change the area from **IOM** to **Configurations**. If you use a left-to-right (LTR) language, the setting is located in the lower left corner. 
1. Go to **Mappings \> Accounts**.
1. Select **New**.
1. On the **New Account Mapping** page, do the following: 
    1. In the **Mapping Group** field, enter "Default Mapping Group".
    1. In the **Provider** field, enter "BigCommerce".
    1. In the **Customer** field, enter "TestBCAccount".
    1. In the **External Field Name** field, enter "ProviderName".
    1. In the **External Field Value** field, enter "BigCommerce".
1. Select **Save & close**.

## Set up pricelist mapping

To set up pricelist mapping, follow these steps.

1. Go to **Mappings \> Price Lists**.
1. Select **New**.
1. On the **New Price List Mapping** page, do the following:
    1. In the **Mapping Group** field, enter "Default Mapping Group".
    1. In the **Provider** field, enter "BigCommerce".
    1. In the **Price list** field, enter "MasterPriceList".
    1. In the **External Field Name** field, enter "ProviderName".
    1. In the **External Field Value** field, enter "BigCommerce".
1. Select **Save & close**.

## Set up unit mapping

After you set up pricelist mapping, you need to set up unit mapping.

1. Go to **Mappings \> Units**.
1. Select **New**.
1. On the **New Unit Mapping** page, do the following:
    1. In the **Mapping Group** field, enter "Default Mapping Group".
    1. In the **Provider** field, enter "BigCommerce".
    1. In the **Unit** field, enter "ea".
    1. In the **External Field Name** field, enter "unit".
    1. In the **External Field Value** field, enter "each".
1. Select **Save & close**.

## Set up product mapping

To set up product mapping, follow these steps.

1. Go to **Mappings \> Products**.
1. Select **New**.
1. On the **New Product Mapping** page, do the following:
    1. In the **Mapping Group** field, enter "Default Mapping Group".
    1. In the **Provider** field, enter "BigCommerce".
    1. In the **Product** field, enter "Accu Scale".
    1. In the **External Field Name** field, enter "sku".
    1. In the **External Field Value** field, enter "ABS".
1. Select **Save & close**.

## Create an order in BigCommerce

Next, create an order from the BigCommerce backoffice experience to Intelligent Order Management.

1. Log in to the BigCommerce store account that you previously set up.
1. Under **Orders**, select **Add**.
1. On the right-side of the page, in the **Search** field, enter the customer you created, or select **New Customer** and enter the **Email ID**.
1. Enter billing information, and select **Next**
1. Under **Add Products**, in the **Search** field, enter the product that you set up in Intelligent Order Management. Select **Next**.
1. Where the **Shipping address** is displayed, select **Next**.
1. Under **Finalize**, select **Manual Payment**, and then select **Save and Process Payment**.
   
Your order number is displayed on the **View Orders** page.

## View BigCommerce order in Intelligent Order Management

To view the results of the orchestration and the flow, do the following.

1.	In Intelligent Order Management, go to **Sales Orders**. Your BigCommerce order is displayed in **Name** column.
3.	Select **Order number** to view **Summary**.
4.	Select **Orchestration Step Results** tab to display your results.
