---
author: rinitha-reddy
description: This article describes how to set up and launch demo providers in Microsoft Dynamics 365 Intelligent Order Management. 
ms.author: rikothap
ms.date: 10/26/2022
ms.topic: conceptual

title: Set up and launch demo providers

---

# Set up and launch demo providers

[!include [banner](includes/banner.md)]

This article describes how to set up and launch demo providers in Microsoft Dynamics 365 Intelligent Order Management.

Demo providers are designed to help you see how orders flow between Intelligent Order Management and third-party connections. After setting up demo providers, you'll be able to generate a test order and monitor its status in Intelligent Order Management as it moves through each step of an orchestration flow from order validation through to fulfillment. 

The following demo provider applications are available:

- Demo e-commerce application (to generate an order)
- Demo fulfillment application (to process and fulfill an order)
- Demo inventory application (to update the inventory system after fulfillment)

## Set up demo providers

Before you can start using demo providers, you must set them up in four stages:

1. Activate connections.
1. Publish policies.
1. Add providers.
1. Activate and publish the demo orchestration flow.

### Activate connections

To activate connections, follow these steps.

1. From the Intelligent Order Management home page, select **Settings**, then select **Initial Connections**.  
1. Open each connection, wait for it to establish (confirmed by a green check mark), then select **Save and close**. 
1. After all the connections are established, on the top menu, select **Activate System**.

####	Change the fulfillment process policy

To change the fulfillment process policy, follow these steps.

1. Go to **Settings \> General app settings \> Order handling preferences**. 
1. In the **Fulfillment Process policy** section, select **Fulfillment Order Creation** (to change the policy from **Inventory Check and Fulfillment Order Creation**).

### Publish policies

To publish policies, follow these steps.
     
1. In the left navigation pane under **Orchestration**, select **Policies**.
1. Select and publish each policy in the list.

### Add providers

To add providers, follow these steps. 

1. In the left navigation pane under **Providers**, select **Library**.
1. Select and activate the **Internal Application Service**, **Demo Order Fulfillment**, **Demo Order Intake**, and **Demo Order Inventory** providers.
1. Select **Activate Providers**. The **Provider Activation** wizard appears.
1. On the **Terms and conditions** screen, read the terms and conditions. If you agree with the terms and conditions, select **Accept**.
1. Complete the **Provider Activation** installation wizard for each provider as follows:
    1. Ensure that the connection is established (confirmed by a green check mark).
    1. Keep the default settings for each provider. For the **Internal Application Service** provider, select **No** when asked to **Create New Split Order Lines**. 
    1. Select **Next**.
1. When you reach the end of the wizard, select **Activate**.

After you activate the providers, it takes approximately six minutes for changes to take effect. You can verify that all the providers are active by going to **Provider \> Installed** and viewing the status for each provider.

### Publish a demo orchestration flow

To publish a demo orchestration flow, follow these steps. 

1. Go to **Orchestrations \> Flows**.  
1. Select **Demo Order Journey** to open it.
1. Select **Save and Publish**.

> [!NOTE]
> If you experience issues while publishing the orchestration flow, reselect the provider action and policy, and then try again.

If the policy isn't published, confirm that the execution policies for **Demo Order Validate Header**, **Demo Order Validate Lines**, and **Simple Fulfillment Determination** are set correctly. 

## Launch the demo providers
     
Once the orchestration flow is published, the demo providers are ready to use.

### Launch the e-commerce demo app
     
Launch the e-commerce demo app to play the part of a consumer as you place an order at a simulated e-commerce store. The order will then flow into Intelligent Order Management, where you can view its status and details in the sales and fulfillment order tables.

To launch the e-commerce demo app, follow these steps.

1. In the left navigation pane, select the area switcher on the bottom left, and then select **Demo Providers**.
1. On the **Demo Providers** page, under **Ecommerce Store - Demo**, select **Launch Demo**. The e-commerce demo site appears.
1. Select a product from the home screen or from a category page.
1. Enter or select a quantity.
1. Select **Add To Cart**.
1. On the cart page, select **Place Order**.
1. A prefilled checkout form with demo customer information appears. Optionally, you can change the customer information before creating the order.
1. Select **Create Order**.
1. Once the order is created successfully, you're redirected to a confirmation screen.

#### Verify the order in the Intelligent Order Management

Once the order is placed, it can be verified inside the Intelligent Order Management sales table. 

To verify the order, follow these steps.

1. In the left navigation pane, select the area switcher on the bottom left, and then select **Sales orders**.
1. The order you created appears at the top of the list. Select the order to open it and review the order details.

When Intelligent Order Management receives an order, it runs an orchestration flow, eventually sending the order to the appropriate warehouse. 

### Launch the demo fulfillment app

Next, launch the demo fulfillment provider app to fulfill the order. 

To launch the demo fulfillment provider app, follow these steps.

1. In the left navigation pane, select the area switcher on the bottom left, and then select **Demo Providers**.
1. On the **Demo Providers** page, under **Fulfillment Center - Demo**, select **Launch Demo**.
1. Select the order you placed, then use the wizard to move through the fulfillment steps all the way to shipment. Once you've completed the wizard, you should be able to see the updated status reflected in the Intelligent Order Management sales order table.

#### Inbound Order

In the demo fulfillment application, select **Inbound Order** to view details about the inbound order on the **Inbound Order** screen, as shown in the following example image. 

![Demo fulfillment app Inbound Order screen](media/inboundaccept.png)

Select **Accept** to move to the next screen of the wizard.

#### Outbound Order

You can view details about the outbound order on the **Outbound Order** screen, as shown in the following example image.

![Demo fulfillment app Outbound Order screen](media/outboundaccept.png)

Select **Accept** to move to the next screen of the wizard.

#### Ready to Ship

You can view details about the ship status of the order on the **Ready to Ship** screen, as shown in the following example image.

![Demo fulfillment app Ready to Ship screen](media/readytoship.png)

Select **Ship Order** to move to the next screen of the wizard.

#### Order Complete

You can view details about the shipped order on the **Shipped** screen, as shown in the following example image.

![Demo fulfillment app Order Complete screen](media/ordershipped.png)

Select **Finish** to close the wizard. Return to the Intelligent Order Management and check the updated status of your order in the sales orders table. 

### Launch the demo inventory app
     
The demo inventory app is where you can see the information regarding different inventories and their respective products and warehouses. Once the order is shipped to the fulfillment center, the quantity of the product is decreased according to the sales order. 

To launch the demo inventory app, follow these steps.

1. In the left navigation pane, select the area switcher on the bottom left, and then select **Demo Providers**.
1. On the **Demo Providers** page, under **Inventory System - Demo**, select **Launch Demo**.

#### Inventory Dashboard

In the demo inventory app, select **Inventory Dashboard** to see a list of products with inventory, as shown in the following example image.

![Demo inventory app Inventory Dashboard screen](media/inventorysystem.png)

#### Products

Select **Products** to see a list of products and product IDs, as shown in the following example image.
 
![Demo inventory app Products screen](media/productlist.png)

#### Warehouses

Select **Warehouses** to see a list of warehouses, as shown in the following example image.

![Demo inventory app Warehouses screen](media/warehouses.png)
