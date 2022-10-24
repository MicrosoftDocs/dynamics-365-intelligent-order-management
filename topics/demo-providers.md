---
author: rikothap
description: This article describes demo providers in Microsoft Dynamics 365 Intelligent Order Management. It helps users ensure orders flow between Intelligent Order Management and other 3rd party providers.
ms.author: rikothap
ms.date: 10/17/2022
ms.topic: conceptual

title: Demo providers

---

# Demo providers for Dynamics 365 Intelligent Order Management

[!include [banner](includes/banner.md)]

Demo Providers are designed to help you see how orders flow between IOM (Dynamics 365 Intelligent Order Management) and its 3rd party connections. After setting things up, you will be able to generate a test order and monitor its status in IOM as it moves through each step of an orchestration flow from order validation all the way to fulfillment. These simulated providers include:
1.	Demo Ecommerce (generate an order)
2.	Demo Fulfillment (process and fulfill an order)
3.	Demo Inventory (update inventory system after fulfillment)

Before you can start using Demo Providers, you will need to set them up in 4 steps:
1. Activate connections
2.	Publish policies
3.	Add providers
4.	Activate demo order flow

# Setting up Demo Providers
1.	Activate connections: 
<ul> a.	From the IOM home page, select Settings, then click on Initial Connections
     b.	Open each connection and wait for it to establish, confirmed by a green check, then click “Save and close”. 

Home->configure->Manage

![Configurations1](media/configuration1.png)
![Configurations2](media/configuration2.png)
![Configurations3](media/configuration3.png)

After all the connections are established, click Activate System at the top.
2.	Change Fulfillment Process policy
a.	Go to Settings > General app settings > Order handling preferences 
b.	In the “Fulfillment Process policy”, change from the third option (Inventory check and Fulfillment Order Creation) to the second one (Fulfillment Order Creation)
![orderhandlingpreference](media/orderhandlingpreference.png)

3.	Publish Policies
a.	Under Orchestration in the site nav, select Policies, then select and publish each policy in the list.
![List of providers](media/allproviders.png)

4.	Add Providers
Go to Library under Providers in the site nav, then select and activate Internal Application Service, Demo Order Fulfillment, Demo Order Intake, and Demo Order Inventory providers and press “Activate Providers” button. Complete the installation wizard for these providers, assure that the connection is made for each of the providers (marked by the green check mark). 
When activating the providers through the wizard, keep the default settings for each of the provider, and select “No” when asked to Create New Split Order Lines when setting up Internal Application Service provider. You need to press “Activate” for each of the providers when setting them up. 

![Providers](media/providers.png)
![Provider terms](media/providerterms.png)
![Provider connections](media/providerconnections.png)
![Provider summary](media/providersummary.png)

After you activate the providers, it takes 6 minutes approx. for changes to take effect. You can verify that all the providers are active by going into Provider > Installed and see the status for each of the providers.

![Provider list](media/providerlist.png)

5.	Publish Demo Orchestration Flow
Go to Orchestrations > Flows, open “Demo Order Journey” and then Save and Publish. 
If an issue is faced while publishing the orchestration flow, reselect the provider action and policy and then try again.

![Orchestration](media/orchestration.png)

If the policy is not published, make sure that the execution policies for the “Demo Order Validate Header,” “Demo Order Validate Lines” and “Simple Fulfillment Determination” are correctly set. 

![Orchestration order header](media/orchestrationpolicies.png)
![Orchestration order line](media/orchestrationexecutionpolicies.png)
![Orchestration fulfillment](media/orchestrationforfulfillment.png)

Using Demo Providers
-	Once the orchestration flow is published, these Demo Providers are ready to use.
-	Click the area switcher on the bottom left and select Demo Providers from the list of areas.

![Demo providers](media/demoproviders.png)

Step 1.1 Launch Ecommerce – Demo App
Play the part of a consumer as you place an order at a simulated e-commerce store. The order will then flow into IOM, where you can view its status and details in the sales and fulfillment order tables.

Step 1.2. Select A product from home screen or their respective category page.
![Contoso1](media/contoso1.png)

Step 1.3. Select quantity and add it to your cart, then Place Order.
![Contoso2](media/contoso2.png)

![Contoso3](media/contoso3.png)

Step 1.4. You will see a prefilled checkout form with demo customer info. If you want, you can change the info and create an order.

![Contoso4](media/contoso4.png)

Step 1.5. Once the order is created successfully, it will redirect to you to a confirmation screen.

![Contoso5](media/contoso5.png)

Once the order is placed, it can be verified inside the IOM sales table. Go back to IOM using the area switcher, then select Sales orders from the side navigation, and find the order you created at the top of the list. Click open the order and review order details.

![Sales orders](media/salesorders.png)

Once IOM receives an order it runs an orchestration flow, eventually sending it to the appropriate warehouse. Next, use the Demo Fulfillment Provider to fulfill the order. Use the area switcher to navigate back to Demo Providers and select Demo Fulfillment Provider.

2.1 Demo Fulfillment Application

![Demo providers](media/demoproviders.png)

Here you will select the order in question, then use the wizard to move it through fulfillment steps all the way to shipment. Once this is complete, you should be able to see the updated status reflected in IOM’s sales order table. 
Inbound Accept

![Inbound accept](media/inboundaccept.png)

Outbound Accept

![Outbound accept](media/outboundaccept.png)

Ready & ship

![Ready to ship](media/readytoship.png)

Order Complete

![Order shipped](media/ordershipped.png)

Return to the IOM Sales orders table and check the updated status of your order. 

3.1 Demo Inventory Application
Here is where you can see the information regarding different inventories and their respective products and warehouses. Once the order is shipped to the Fulfillment Center, the quantity of the product is decreased according to the sales order. 
Inventory System

![Inventory system](media/inventorysytem.png)

Products
 
![Products](media/products.png)

Warehouses

![Warehouses](media/warehouses.png)
