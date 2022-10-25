---
author: rinitha-reddy
description: This article describes demo providers in Microsoft Dynamics 365 Intelligent Order Management. It helps users ensure orders flow between Intelligent Order Management and other 3rd party providers.
ms.author: rikothap
ms.date: 10/25/2022
ms.topic: conceptual

title: Demo providers

---

# Demo providers for Dynamics 365 Intelligent Order Management

[!include [banner](includes/banner.md)]

Demo providers are designed to help you see how orders flow between IOM (Dynamics 365 Intelligent Order Management) and its 3rd party connections. After setting things up, you will be able to generate a test order and monitor its status in IOM as it moves through each step of an orchestration flow from order validation all the way to fulfillment. These simulated providers include:

- Demo E-commerce (to generate an order)
- Demo Fulfillment (tp process and fulfill an order)
- Demo Inventory (to update inventory system after fulfillment)

Before you can start using demo providers, you must set them up in four steps:

1. Activate connections.
2. Publish policies.
3. Add providers.
4. Activate demo order flow.

## Set up Demo Providers


### Activate connections

1.	Activate connections: 
 a.	From the IOM home page, select Settings, then click on Initial Connections
     b.	Open each connection and wait for it to establish, confirmed by a green check, then click “Save and close”. 

Home->configure->Manage

![IMG 1](media/configuration1.png)
![IMG 2](media/configuration2.png)
![IMG 3](media/configuration3.png)

After all the connections are established, click Activate System at the top.
2.	Change Fulfillment Process policy
a.	Go to Settings > General app settings > Order handling preferences 
b.	In the “Fulfillment Process policy”, change from the third option (Inventory check and Fulfillment Order Creation) to the second one (Fulfillment Order Creation)
![IMG 4](media/orderhandlingpreference.png)

### Publish Policies
     
a.	Under Orchestration in the site nav, select Policies, then select and publish each policy in the list.
![IMG 5](media/allproviders.png)

### Add Providers

Go to Library under Providers in the site nav, then select and activate Internal Application Service, Demo Order Fulfillment, Demo Order Intake, and Demo Order Inventory providers and press “Activate Providers” button. Complete the installation wizard for these providers, assure that the connection is made for each of the providers (marked by the green check mark). 

When activating the providers through the wizard, keep the default settings for each of the provider, and select “No” when asked to Create New Split Order Lines when setting up Internal Application Service provider. You need to press “Activate” for each of the providers when setting them up. 

![IMG 6](media/providers.png)
![IMG 7](media/providerterms.png)
![IMG 8](media/providerconnections.png)
![IMG 9](media/providersummary.png)

After you activate the providers, it takes 6 minutes approx. for changes to take effect. You can verify that all the providers are active by going into Provider > Installed and see the status for each of the providers.

![IMG 10](media/providerlist.png)

### Publish Demo Orchestration Flow

Go to Orchestrations > Flows, open “Demo Order Journey” and then Save and Publish. 
If an issue is faced while publishing the orchestration flow, reselect the provider action and policy and then try again.

![IMG 11](media/orchestration.png)

If the policy is not published, make sure that the execution policies for the “Demo Order Validate Header,” “Demo Order Validate Lines” and “Simple Fulfillment Determination” are correctly set. 

![IMG 12](media/orchestrationpolicies.png)
![IMG 13](media/orchestrationexecutionpolicies.png)
![IMG 14](media/orchestrationforfulfillment.png)

## Use Demo Providers
     
-	Once the orchestration flow is published, these Demo Providers are ready to use.
-	Click the area switcher on the bottom left and select Demo Providers from the list of areas.

![IMG 15](media/demoproviders.png)

### Step 1.1 Launch Ecommerce – Demo App
     
Play the part of a consumer as you place an order at a simulated e-commerce store. The order will then flow into IOM, where you can view its status and details in the sales and fulfillment order tables.

### Step 1.2. Select A product from home screen or their respective category page.
     
![IMG 16](media/contoso1.png)

### Step 1.3. Select quantity and add it to your cart, then Place Order.
     
![IMG 17](media/contoso2.png)

![IMG 18](media/contoso3.png)

### Step 1.4. You will see a prefilled checkout form with demo customer info. If you want, you can change the info and create an order.

![IMG 19](media/contoso4.png)

### Step 1.5. Once the order is created successfully, it will redirect to you to a confirmation screen.

![IMG 20](media/contoso5.png)

Once the order is placed, it can be verified inside the IOM sales table. Go back to IOM using the area switcher, then select Sales orders from the side navigation, and find the order you created at the top of the list. Click open the order and review order details.

![IMG 21](media/salesorders.png)

Once IOM receives an order it runs an orchestration flow, eventually sending it to the appropriate warehouse. Next, use the Demo Fulfillment Provider to fulfill the order. Use the area switcher to navigate back to Demo Providers and select Demo Fulfillment Provider.

### 2.1 Demo Fulfillment Application

![IMG 22](media/demoproviders.png)

Here you will select the order in question, then use the wizard to move it through fulfillment steps all the way to shipment. Once this is complete, you should be able to see the updated status reflected in IOM’s sales order table. 
Inbound Accept

![IMG 23](media/inboundaccept.png)

Outbound Accept

![IMG 24](media/outboundaccept.png)

Ready & ship

![IMG 25](media/readytoship.png)

Order Complete

![IMG 26](media/ordershipped.png)

Return to the IOM Sales orders table and check the updated status of your order. 

### 3.1 Demo Inventory Application
     
Here is where you can see the information regarding different inventories and their respective products and warehouses. Once the order is shipped to the Fulfillment Center, the quantity of the product is decreased according to the sales order. 
Inventory System

![IMG 27](media/inventorysystem.png)

Products
 
![IMG 28](media/products.png)

Warehouses

![IMG 29](media/warehouses.png)
