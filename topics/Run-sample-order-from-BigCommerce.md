# Run sample order orchestration flow from BigCommerce to Microsoft Dynamics 365 Intelligent Order Management

[!include [banner](includes/banner.md)]

This topic describes the steps required to run a sample order orchestration flow  from in Microsoft Dynamics 365 Intelligent Order Management.

## Prerequisites
You will need to set up BigCommerce as a provider in Dynamics 365 Intelligent Order Management. Follow the instructions in [Set up BigCommerce provider](https://docs.microsoft.com/en-us/dynamics365/intelligent-order-management/set-up-bigcommerce-provider) to set up BigCommerce provider in Intelligent Order Management.

## Set up customer

To set up a customer, follow these steps.

1. Go to **Customers \> Accounts**.
1. Select **New**.
1. For **Account Name**, enter "TestBCAccount".
1. Select **Save & close**.

## Set up account mapping 

To set up account mapping, follow these steps.

1. In the lower right corner of your Intelligent Order Management application screen, change the area from **IOM** to **Configurations**. If you use a left-to-right (LTR) language, this setting is located in the lower left corner of your application screen. 
1. Go to **Mappings \> Accounts**.
1. Select **New**.
1. On the **New Account Mapping** page, do the following: 
    1. For **Mapping Group**, enter "Default Mapping Group".
    1. For **Provider**, enter "BigCommerce"
    1. For **Customer**, enter "TestBCAccount".
    1. For **External Field Name**, enter "ProviderName".
    1. For **External Field Value**, enter "BigCommerce".
1. Select **Save & close**.

## Set up pricelist mapping

To set up pricelist mapping, follow these steps.

1. Go to **Mappings \> Price Lists**.
1. Select **New**.
1. On the **New Price List Mapping** page, do the following:
    1. For **Mapping Group**, enter "Default Mapping Group".
    1. For **Provider**, enter BigCommerce
    1. For **Price list**, enter "MasterPriceList".
    1. For **External Field Name**, enter "ProviderName".
    1. For **External Field Value**, enter "BigCommerce".
1. Select **Save & close**.

## Set up unit mapping

To set up unit mapping, follow these steps.

1. Go to **Mappings \> Units**.
1. Select **New**.
1. On the **New Unit Mapping** page, do the following:
    1. For **Mapping Group** enter "Default Mapping Group"
    1. For **Provider**, enter "BigCommerce".
    1. For **Unit**, enter "ea".
    1. For **External Field Name**, enter "unit".
    1. For **External Field Value**, enter "each".
1. Select **Save & close**.

## Set up product mapping

To set up product mapping, follow these steps.

1. Go to **Mappings \> Products**.
1. Select **New**.
1. On the **New Product Mapping** page, do the following:
    1. For **Mapping Group**, enter "Default Mapping Group".
    1. For **Provider**, enter "BigCommerce".
    1. For **Product**, enter "Accu Scale".
    1. For **External Field Name**, enter "sku".
    1. For **External Field Value**, enter "ABS".
1. Select **Save & close**.

## Create an Order in BigCommerce portal:

1.	Login to BigCommerce store account that you had set up.
2.	Under **Orders** select **Add** 
3.	On the right-side screen, in **Search** enter the customer created or select New Customer and enter email id.
4.	Enter the billing information and select **Next**
5.	Under **Add Products**,in **Search** field enter the product that was set up in Intelligent Order Management and select **Next**.
6.	Select **Next** on the next screen where the Shipping address is displayed.
7.	Under **Finalize** select **Manual Payment** and select **Save and Process Payment**.
8.	Your order number will be displayed in **View Orders** page.

## View the Order from BigCommerce in Dyanmics 365 Intelligent Order Management:

1.	Go to **Sales Orders** in Intelligent Order Management
2.	Your BigCommerce order will be displayed in **Name** column.
3.	Select Order number to view **Summary**.
4.	Select **Orchestration Step Results** tab to view the results of the Orchestration and the flow.
