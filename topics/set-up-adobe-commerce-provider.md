---
author: sumanic
description: This article describes how to set up the Adobe Commerce provider in Microsoft Dynamics 365 Intelligent Order Management.
ms.date: 01/07/2026
ms.custom: 
  - bap-template
ms.topic: how-to
ms.author: sumanic

title: Set up Adobe Commerce provider

---

# Set up Adobe Commerce provider

[!include [banner](includes/banner.md)]

This article describes how to set up the Adobe Commerce provider in Microsoft Dynamics 365 Intelligent Order Management.

Adobe Commerce (formerly Magento) is an e-commerce platform that is designed to give online businesses a flexible shopping cart system, and enable them to manage the appearance, content, and features of an online store.

For more information about Adobe Commerce, see [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html).

## Prerequisites

To set up the Adobe Commerce provider, you must have a sample store set up. For information about how to set up your account and sample store, see [Cloud guide for Commerce](https://devdocs.magento.com/cloud/bk-cloud.html).

## Set up the provider

To set up the provider, follow these steps:

1. In Intelligent Order Management, go to **Providers \> Catalog**.
1. On the **Adobe Commerce** tile, select **Add Provider**.
1. On the **Terms and Conditions** page, select **Create**.
1. In the **Connections** section, you must set up two connections:

    - Adobe Commerce Dataverse (current environment) Connection
    - Adobe Commerce connection:

    To set up each connection, follow these steps:

    1. Select the connection.
    1. Select **Create**.
    1. Enter the following information:

        - **Connection Name** – Enter a name of your choice.
        - **API Key** – Enter the Adobe Commerce API key.
        - **Store Host URL** – Enter the Adobe Commerce Store Host URL.

    1. Select **Create**.
    1. Save the connection.
    1. Select **Activate** to activate the connection.
    1. Select **Save and close**.

1. Select **Activate** to activate the provider.
1. Select **Save and close**.
1. Go to **Providers \> Installed**, and validate that the provider that you set up is listed and has a status of **Activated**.

## Out-of-box capabilities

The Adobe Commerce provider has the following capabilities.

| Capability | Details |
| ---------- | ------- |
| Transformation | **Adobe Commerce Sales Order to Dataverse Sales Order** – Transform a sales order from Adobe Commerce into a sales order in Dataverse. |
| Transformation | **Adobe Commerce Customer to Dataverse Account** – Transform an Adobe Commerce customer into an account in Dataverse. |
| Transformation | **Dataverse Sales Order Status to Adobe Commerce Order Status** – Send the order update status back to Adobe Commerce. |

## Run a sample transaction by using Adobe Commerce

After your store is set up, you're ready to run a sample transaction by using Adobe Commerce. To set up data for the sample transaction, complete the following procedures in Adobe Commerce and Intelligent Order Management.

### Create a customer in Adobe Commerce

First, you must set up a customer in Adobe Commerce.

To set up a customer in Adobe Commerce, follow these steps:

1. In Adobe Commerce, open the **Customer** page.
1. Select **Add New Customers**.
1. Enter details for the customer.
1. In the **Customer email** field, enter the customer's email address. Then select **Save**.
1. Add **Customer Address Details**.
1. Enter the customer's address information, and then select **Save Customer**.
1. To use the customer for a transaction, you must sign out of Adobe Commerce and then sign back in.

### Configure the mappings in Intelligent Order Management

- In Intelligent Order Management, in the lower-right corner of any page, change the area from **IOM** to **Configurations**.

    > [!NOTE]
    > If you use a left-to-right (LTR) language, the setting is in the lower-left corner.

#### Set up price list mapping

Next, you must set up price list mapping.

To set up price list mapping, follow these steps:

1. Go to **Mappings \> Price Lists**.
1. Select **New**.
1. On the **New Price List Mapping** page, enter the following information:

    1. In the **Mapping Group** field, enter **Default Mapping Group**.
    1. In the **Account** field, select the account that you created (if you created one).
    1. In the **Price list** field, enter **MasterPriceList**.
    1. In the **External Field Name** field, enter **ProviderName**.
    1. In the **External Field Value** field, enter **Adobe Commerce**.

1. Select **Save and close**.

#### Set up unit mapping

After you set up price list mapping, you must set up unit mapping.

To set up unit mapping, follow these steps:

1. Go to **Mappings \> Units**.
1. Select **New**.
1. On the **New Unit Mapping** page, enter the following information:

    1. In the **Mapping Group** field, enter **Default Mapping Group**.
    1. In the **Account** field, select the account that you created (if you created one).
    1. In the **Unit** field, enter **ea**.
    1. In the **External Field Name** field, enter **unit**.
    1. In the **External Field Value** field, enter **each**.

1. Select **Save and close**.

#### Set up product mapping

Next, you must set up product mapping.

To set up product mapping, follow these steps:

1. Go to **Mappings \> Products**.
1. Select **New**.
1. On the **New Product Mapping** page, enter the following information:

    1. In the **Mapping Group** field, enter **Default Mapping Group**.
    1. In the **Account** field, select the account that you created (if you created one).
    1. In the **Product** field, enter **Airport Duo**.
    1. In the **External Field Name** field, enter **productid**.
    1. In the **External Field Value** field, enter **WS03-XS-Red**.

1. Select **Save and close**.

### Create an order in Adobe Commerce

Next, you must create an order in Adobe Commerce and submit it to Intelligent Order Management.

To create an order in Adobe Commerce, follow these steps:

1. Sign in to the Adobe Commerce store account that you previously set up.
1. Go to **Sales \> Orders**, and select **Create New Order**.
1. In the list of customers, double-tap (or double-click) the customer that you created earlier.
1. Select **Add Products By SKU** or **Add Products**, enter the product that you set up in Intelligent Order Management, and then select **Enter**.
1. Scroll down, select **Get shipping methods and rates**, and then select either **Table rate** or **Fixed Rate**.
1. Select **Submit Order**. An order ID is generated.

    > [!NOTE]
    > Adobe Commerce order IDs aren't unique.

1. To view the order, go to **Sales \> Orders**.

### View an Adobe Commerce order in Intelligent Order Management

To view the results of the orchestration and the flow, follow these steps:

1. In Intelligent Order Management, go to **Sales Orders**. Your Adobe Commerce order is shown in the **Name** column.
1. Select the order number to view the summary.
1. Select the **Orchestration Step Results** tab to view the results.

## Additional resources

- [Adobe Commerce API documentation](https://devdocs.magento.com/guides/v2.4/rest/bk-rest.html).
