---
author: josaw1
description: This topic describes the setup that is required to run a sample order orchestration flow from BigCommerce to Microsoft Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 03/21/2025
ms.custom: 
  - bap-template
ms.topic: how-to
ms.author: josaw

title: Run a sample order orchestration flow from BigCommerce

---

# Run a sample order orchestration flow from BigCommerce

[!include [banner](includes/banner.md)]

This topic describes the setup that is required to run a sample order orchestration flow from BigCommerce to Microsoft Dynamics 365 Intelligent Order Management.

## Prerequisites

Before you can begin, you must set up BigCommerce as a provider in Intelligent Order Management. For more information, see [Set up BigCommerce provider](set-up-bigcommerce-provider.md).

## Create a customer in BigCommerce

The first step is to set up a customer in BigCommerce.

1. In BigCommerce, go to the **Customer** page.
2. Select **Add**
3. Enter details for the customer. If the orders are from a company, enter the name of the company in the **Company Name** field, otherwise leave the field blank. 
4. Enter the customer's email address in the **Customer email** field and then select **Save**.
5. Select the **Customer Address Details** tab.
6. Enter the customer address information and then select **Save**.
7. To use the customer for a transaction, you need to sign out of BigCommerce and then sign back in.

> [!NOTE]
> If you provided a company name when you created a customer in BigCommerce, follow the steps in the "Set up account mappings" section below. Otherwise, go to the "Set up pricelist mapping" section.

## Set up a customer in Intelligent Order Management

1. Go to **Customers \> Accounts**.
1. Select **New**.
1. In the **Account Name** field, enter **TestBCAccount**.
1. Select **Save & close**.

## Set up account mapping

1. In the lower-right corner of any Intelligent Order Management page, change the area from **IOM** to **Configurations**.

    > [!NOTE]
    > If you use a left-to-right (LTR) language, the setting is in the lower-left corner.

1. Go to **Mappings \> Accounts**.
1. Select **New**.
1. On the **New Account Mapping** page, enter the following information:

    1. In the **Mapping Group** field, enter **Default Mapping Group**.
    1. In the **Account** field, select the account created if you created one.
    1. In the **Customer** field, enter **TestBCAccount**.
    1. In the **External Field Name** field, enter **ProviderName**.
    1. In the **External Field Value** field, enter **BigCommerce**.

1. Select **Save & close**.

## Set up pricelist mapping

1. Go to **Mappings \> Price Lists**.
1. Select **New**.
1. On the **New Price List Mapping** page, enter the following information:

    1. In the **Mapping Group** field, enter **Default Mapping Group**.
    1. In the **Account** field, select the account created if you created one.
    1. In the **Price list** field, enter **MasterPriceList**.
    1. In the **External Field Name** field, enter **ProviderName**.
    1. In the **External Field Value** field, enter **BigCommerce**.

1. Select **Save & close**.

## Set up unit mapping

After you set up pricelist mapping, you must set up unit mapping.

1. Go to **Mappings \> Units**.
1. Select **New**.
1. On the **New Unit Mapping** page, enter the following information:

    1. In the **Mapping Group** field, enter **Default Mapping Group**.
    1. In the **Account** field, select the account created if you created one.
    1. In the **Unit** field, enter **ea**.
    1. In the **External Field Name** field, enter **unit**.
    1. In the **External Field Value** field, enter **each**.

1. Select **Save & close**.

## Set up product mapping

1. Go to **Mappings \> Products**.
1. Select **New**.
1. On the **New Product Mapping** page, enter the following information:

    1. In the **Mapping Group** field, enter **Default Mapping Group**.
    1. In the **Account** field, select the account created if you created one.
    1. In the **Product** field, enter **Accu Scale**.
    1. In the **External Field Name** field, enter **sku**.
    1. In the **External Field Value** field, enter **ABS**.

1. Select **Save & close**.

## Create an order in BigCommerce

Next, create an order from the BigCommerce back-office experience to Intelligent Order Management.

1. Sign in to the BigCommerce store account that you previously set up.
1. Under **Orders**, select **Add**.
1. On the right side of the page, in the **Search** field, enter the customer that you created. Alternatively, select **New Customer**, and enter the email ID.
1. Enter billing information, and then select **Next**.
1. Under **Add Products**, in the **Search** field, enter the product that you set up in Intelligent Order Management. Then select **Next**.
1. When the shipping address is shown, select **Next**.
1. Under **Finalize**, select **Manual Payment**, and then select **Save and Process Payment**.

Your order number is shown on the **View Orders** page.

## View a BigCommerce order in Intelligent Order Management

To view the results of the orchestration and the flow, follow these steps.

1. In Intelligent Order Management, go to **Sales Orders**. Your BigCommerce order is shown in the **Name** column.
1. Select the order number to view the summary.
1. Select the **Orchestration Step Results** tab to view your results.
