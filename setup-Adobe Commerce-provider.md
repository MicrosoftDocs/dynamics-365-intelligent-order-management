---
author: sumanic
description: This topic provides information about how to set up the Adobe Commerce provider in Dynamics 365 Intelligent Order Management.
ms.date: 06/21/2022
ms.topic: how-to
ms.author: sumanic

title: Set up Adobe Commerce provider

---

# Set up Adobe Commerce provider

[!include [banner](includes/banner.md)]


This topic provides information about how to set up the Adobe Commerce provider in Dynamics 365 Intelligent Order Management.

Adobe Commerce, formerly Magento, is an e-commerce platform designed to provide online businesses with a flexible shopping cart system, plus management of the look, content, and features of a business's online store.

For more information about Adobe Commerce, see the [Adobe Commerce website](https://business.adobe.com/products/magento/magento-commerce.html). 

## Prerequisites 

You need to have a sample store set up. Go to the [Adobe Commerce website](https://devdocs.magento.com/cloud/bk-cloud.html) and follow the instructions to set up your account and sample store. 

## Set up the provider
To set up the provider, follow these steps: 

1.  In Intelligent Order Management, go to **Providers > Catalog**.

2.  Select **Add Provider** on the **Adobe Commerce** tile.

3.  Select **Create** on the **Terms and Conditions** page.

4.  There are two connections that you need to set up in the **Connections** section.

    1. Adobe Commerce Dataverse (current environment) Connection

    1. Adobe Commerce Connection:

        1. Click the connection.

        1. Click on 'Create'.

        1. Enter the following information: 

            - **Connection Name**: Enter a name of your choice.
            - **API Key**: Enter the BigCommerce API key.
            - **Store Host URL** : Enter the Adobe commerce Store host URL.

        1. Click on Create.

        1. Save the Connection.

        1. Select **Activate** to activate the connection.

        1. Select **Save and close**.

5.  Select **Activate** to activate the provider.

6.  Select **Save and close**.

7.  Go to **Providers > Installed** and validate that the provider you set up is listed with the status **Activated**.

## Out-of-box capabilities

The Adobe Commerce provider has the following capabilities:

|  Capability | Details |
| ------------------ | -------------------------------- |
| Transformation  |  **Adobe Commerce Sales Order to Dataverse Sales Order**: Transforms a sales order from Adobe Commerce into a sales order in Dataverse.|
| Transformation  |  **Adobe Commere Customer to Dataverse Account**: Transforms an Adobe Commerce customer into an account in Dataverse.|
| Transformation  |  **Dataverse Sales Order Status to Adobe Commerce Order Status**: Send order update status back to Adobe Commerce.|


## Run a sample transaction with Adobe Commerce ##

Once you have a store ready, follow the below steps in Adobe Commerce and Dynamics 365 Intelligent Order Management to setup data for a sample transaction:

## Create a customer in Adobe Commerce

The first step is to set up a customer in Adobe Commerce.

1. In Adobe Commerce, go to the **Customer** page.
2. Select **Add New Customers**
3. Enter details for the customer. 
4. Enter the customer's email address in the **Customer email** field and then select **Save**.
5. Add the **Customer Address Details**.
6. Enter the customer address information and then select **Save Customer**.
7. To use the customer for a transaction, you need to sign out of Adobe Commerce and then sign back in.

## Setup the mappings in Dynamics 365 Intelligent Order Management ##

1. In the lower-right corner of any Intelligent Order Management page, change the area from **IOM** to **Configurations**.

    > [!NOTE]
    > If you use a left-to-right (LTR) language, the setting is in the lower-left corner.

## Set up pricelist mapping

1. Go to **Mappings \> Price Lists**.
1. Select **New**.
1. On the **New Price List Mapping** page, enter the following information:

    1. In the **Mapping Group** field, enter **Default Mapping Group**.
    1. In the **Account** field, select the account created if you created one.
    1. In the **Price list** field, enter **MasterPriceList**.
    1. In the **External Field Name** field, enter **ProviderName**.
    1. In the **External Field Value** field, enter **Adobe Commerce**.

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
    1. In the **Product** field, enter **Airpot Duo**.
    1. In the **External Field Name** field, enter **productid**.
    1. In the **External Field Value** field, enter **WS03-XS-Red**.

1. Select **Save & close**.

## Create an order in Adobe Commerce

Next, create an order from the Adobe Commerce back-office experience to Intelligent Order Management.

1. Sign in to the Adobe Commerce store account that you previously set up.
1. Goto **Sales** --> **Orders** and click **Create New Order**.
1. From the list of customers in the below page, double click the **Customer** you created in the above steps.
1. Click on  **Add Products By SKU** or **Add Products**, enter the product that you set up in Intelligent Order Management and click Enter.
1. Scroll down, click on **Get shipping methods and rates**. Choose between **Table rate** and **Fixed Rate**.
1. Click on **Submit Order**.
1. An order number will be generated. [!Note]: Adobe Commerce order ids are not unique.
1. You can view the order in **Sales**-->**Orders**.

## View a Adobe Commerce order in Intelligent Order Management

To view the results of the orchestration and the flow, follow these steps.

1. In Intelligent Order Management, go to **Sales Orders**. Your Adobe Commerce order is shown in the **Name** column.
1. Select the order number to view the summary.
1. Select the **Orchestration Step Results** tab to view your results.

## Additional resources

- [Adobe Commerce API documentation](https://devdocs.magento.com/guides/v2.4/rest/bk-rest.html).
