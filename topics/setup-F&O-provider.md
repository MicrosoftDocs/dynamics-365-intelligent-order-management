---
author: sumanic
description: This topic provides information about how to set up the Dynamics 365 Finance & Operations Provider provider in Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 02/08/2022
ms.topic: how-to
ms.author: josaw

title: Set up D365 Finance and Operations provider

---

# Set up Dynamics 365 Finance and Operations provider

[!include [banner](includes/banner.md)]


This topic provides information about how to set up the D365 Finance and Operations provider in Dynamics 365 Intelligent Order Management.

D365 Finance and Operations support businesses to manage their global financial systems, operational business processes, and streamlined supply chains to empower people to make fast, informed decisions The D365 FinOps provider enables Intelligent Order Management to write or consume orders from D365 FinOps and performs additional supply chain actions.  

For more information about D365 FinOps, see the [D365 FinOps](https://dynamics.microsoft.com/en-us/finance/overview/) website. 

## Prerequisites 

You need to have a sample store set up. Go to the [BigCommerce website](https://www.bigcommerce.com/dm/microsoft/) and select **Start your free trial**. Follow the instructions to set up your sample store. 

## Set up the provider
To set up the provider, follow these steps: 

1.  In Intelligent Order Management, go to **Providers > Catalog**.

2.  Select **Add Provider** on the **BigCommerce** tile.

3.  Select **Create** on the **Terms and Conditions** page.

4.  There are two connections that you need to set up in the **Connections** section.

    1. BigCommerce Common Data Service Connection;

    1. BigCommerce connection:

       1. Select the connection.

       1. Select the **Retrieve Connection Link** URL.

       1. Search for **BigCommerce** and then select the connector.

       1. Enter the following information: 
          - **Connection Name**: Enter a name of your choice.
          - **API Key**: Enter the BigCommerce API key. You can retrieve it by following the instructions here: https://\<your store hash code\>.mybigcommerce.com/manage/settings/auth/api-accounts.

       1. Save the connection.

       1. Test the connection by selecting **Test** in the top ribbon.

       1. Copy your URL.

       1. Go back to the **Connection URL** page in Intelligent Order Management and paste the URL.

       1. Select **Save**.

       1. Select **Activate** to activate the connection.

       1. Select **Save and close**.

5. Go to the **Parameters** tab and add the BigCommerce store hash.

6. Select **Save**.

7. Select **Activate** to activate the provider.

8. Select **Save and close**.

9. Go to **Providers > Installed** and validate that the provider you set up is listed with the status **Activated**.

## Out-of-box capabilities

The BigCommerce provider has the following capabilities:

|  Capability | Details |
| ------------------ | -------------------------------- |
|  Business events  | **Billing of order confirmed by billing provider**: Event that indicates that billing was confirmed by BigCommerce.</br><br>**Creation of fulfillment line succeeded**: Event that indicates that a fulfillment line was successfully created.</br><br>**Creation of fulfillment order failed**: Event that indicates that fulfillment of the order failed.</br><br>**Creation of fulfillment order succeeded**: Event that indicates that fulfillment of the order succeeded.</br>  |
| Transformation  |  **BigCommerce sales order to Microsoft Dataverse sales order**: Transforms a purchase order from BigCommerce into a sales order in Dataverse.|

## Additional resources

To learn more about BigCommerce's API, see the [BigCommerce API documentation](https://developer.bigcommerce.com/api-docs).
