---
ms.author: johnmichalak
author: johnmichalak
title: Fulfillment and Returns Optimization provider overview
description: This article provides an overview of the Fulfillment and Returns Optimization provider in Microsoft Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 02/22/2023
ms.topic: overview
ms.custom: bap-template

---

# Fulfillment and Returns Optimization provider overview

[!include [banner](includes/banner.md)]

This article provides an overview of the Fulfillment and Returns Optimization provider in Microsoft Dynamics 365 Intelligent Order Management.

The Fulfillment and Returns Optimization provider is an intelligent optimization service that determines the source of order fulfillment, while achieving required goals and respecting the desired configuration that is determined by the business. The Fulfillment and Returns Optimization provider helps you ensure that products are delivered to your customers in the right quantities, from the right sources, and at the right time. This can help you maximize profits, minimize costs, and satisfy service-level requirements.  

In a modern supply network where product fulfillment can come from multiple channels, organizations must quickly adapt to order changes, supplier availability issues, or spikes in demand. The Fulfillment and Returns Optimization provider helps you maximize order fulfillment and find the right source for the delivery of products based on different business constraints and business objectives such as minimizing costs by fulfilling orders from the closest sources.  

The Fulfillment and Returns Optimization provider is built as a microservice and reads configuration data such as fulfillment sources, source lists, business constraints, and strategies from Microsoft Dataverse to optimize order fulfillment. The provider uses Microsoft Azure Maps to provide geocode shipping address information on orders and fulfillment sources, and the distance between those locations.

## Fulfillment and Returns Optimization provider settings

To enable the Fulfillment and Returns Optimization provider as part of the order orchestration journey, set up and activate the Fulfillment and Returns Optimization provider by following the instructions in [Set up Fulfillment and Returns Optimization provider](set-up-fro-provider.md). Once the provider is activated, the following settings must be set up in order to achieve business goals.

### Sources 

Fulfillment sources are entities like warehouses, distribution centers, retail stores, drop-ship vendors, or virtual sites that house inventory or provide products. You can create and modify fulfillment sources by selecting the area switcher at the bottom of the left navigation pane and switching to **Settings \> Fulfillment Settings**. Then on the **Fulfillment settings** page under **Sources**, select **Manage**.

For each of your fulfillment sources, you can:

- Define a unique name.
- Set the time zone of the source.
- Set the type of source (warehouse or other).
- Specify where the source is located (latitude and longitude)
- Specify where the system should look for inventory in the Inventory Visibility service. 

You can add details on the average processing time of orders in a warehouse, which will be used to determine the planned shipment date of various orders. You can also set the **Cutoff time** of a warehouse, which is used if the **Respect warehouse timings constraint** setting is enabled to allow orders to only be sent to a warehouse between 12 AM and the cutoff time. 

### Source lists

Fulfillment source lists enable you to group a list of sources and manage sources in a flexible manner, within specific constraints. To define fulfillment source lists, on the **Fulfillment settings** page under **Source lists**, select **Manage**.
  
Depending on your business situation, you can define multiple source lists and use them as needed.  

For example, in your strategy definition, you can include all the sources where fulfillment will occur. For your business constraints, you can use a different source list. You can also define different maximum distance constraints for retail stores and warehouses, and restrict partial fulfillment for only your retail stores.  

Active source lists are displayed on the **Source Lists \> Manage** page. To create a new source list, select **New**. Provide a name to easily identify the source list, and then add existing or new sources on the **Sources** tab. To remove a source from a source list, select the source on the **Sources** tab and then select **Remove**.

### Constraints 

Constraints are an optional component of fulfillment optimization. The following business constraints are supported:  

- Maximum distance
- Restrict partial fulfillment of orders
- Limit number of warehouses
- Respect warehouse timings

To create or modify constraints, on the **Fulfillment settings** page under **Constraints**, select **Manage**. To create a specific constraint type, select the appropriate constraint type when you create the constraint.

Every business constraint shares a set of common attributes as part of its definition. The details differ based on the type of business constraint. The following common attributes are applicable to all business constraints: 

- **Name**: Used to identify the business constraint.
- **Description**: Used to describe the business constraint.
- **Constraint type**: Indicates the type of business constraint.
- **Is enabled**: Used to enable or disable a business constraint.  

You can define multiple business constraints of each type and apply them to different optimization strategies.  

#### Maximum distance constraint 

The maximum distance constraint enables an organization to define the maximum distance a source or group of sources can extend to fulfill an order. Currently, distance is considered the straight-line distance between the source and the customer address, as calculated by Azure Maps.  

You can define the maximum distance for a source or a source list. When the maximum distance is defined for a source list that contains an individually defined source distance, there may be an overlapping maximum distance constraint defined for this source. In such a case, the optimization service applies the lowest defined maximum distance for those sources. 

In the following example image, the Seattle warehouse can deliver only up to 10 miles from its radius even though it's part of the **All Sources** list because of the way that this constraint works. If there is a conflict, it uses the shortest distance.

![Screenshot of Maximum radius constraint screen](media/constraint-max-radius.png)

If a constraint results in no warehouse being suitable for the sales order(s), the system won't be able to create any fulfillment order for the sales order. Instead, the status of the sales order changes to **Inventory not found**.

#### Restrict partial fulfillment of orders constraint

Sometimes the Fulfillment and Returns Optimization provider is required to handle scenarios where demand is greater than supply. When Intelligent Order Management receives orders that require more quantity than the available inventory, by default sales orders are split by order line where some lines of the order are fulfilled while others are either backordered or set to the **Inventory not found** order state. An individual order line can't be split further and partially assigned, although it can be assigned to different sources. When **Restrict partial fulfillment of orders constraint** is enabled, the Fulfillment and Returns Optimization provider ensures that either the entire order is fulfilled or it isn't fulfilled at all. 

#### Respect warehouse timings constraint

Businesses sometimes have delivery trucks that leave at a certain time of day, every day. To optimize for this scenario, each source can be configured to have different cutoff times. To ensure this constraint works as expected, add cutoff times to the warehouses that need to respect them before running this constraint.

Enabling the **Respect warehouse timings constraint**, the Fulfillment and Returns Optimization provider ensures that sources only create fulfillment orders if they're able to be sent to the warehouse before the cutoff times. If not, the Fulfillment and Returns Optimization provider tries to assign the sales orders to warehouses that are still open to processing orders. This way, the Fulfillment and Returns Optimization provider optimizes for quicker fulfillment and faster delivery.

#### Limit number of warehouses constraint

There can be instances where not all inventory is available at a single source. To fulfill orders in these cases, the Fulfillment and Returns Optimization provider splits the order to assign different warehouses to different parts of a single sales order. By using the **Limit number of warehouses constraint**, you can control the degree to which orders get split. 

This constraint can be configured to specify the upper limit of the number of warehouses you want a single order to be split amongst. 

In other words, if this constraint is configured to specify three ('3') warehouses, every sales order must be fulfilled by one, two, or three different warehouses. If the sales order requires more than 3 warehouses to fulfill it, the sales order won't be fulfilled at all unless the **Restrict partial fulfillment of orders constraint** is disabled and the **Limit number of warehouses constraint** is enabled. 

By default, the sales order will be split among as many warehouses as is required, while respecting inventory conditions and other constraints.

To specify the number of warehouses to split between, select **+ New Limit Number of Warehouses Constraint** to add an entry, and then select **Save**.

### Strategies 

A strategy helps define the optimization configuration that achieves your business needs. A strategy brings together objectives, constraints, and sources to be considered, and specifies how inventory optimization should occur. To create and modify a strategy, on the **Fulfillment settings** page under **Strategies**, select **Manage**.

Fulfillment while minimizing distance is the predefined objective of every strategy.
  
Depending on the nature of your business, you can define multiple optimization strategies. You can define a list of fulfillment sources that participate in fulfillment and define constraints that the optimization service must enforce. Such constraints are hard constraints that the optimization service will mandatorily impose when it determines the optimal source. You can configure a strategy to be the default strategy, but only one strategy can be the default at any single time. 
  
A strategy can also be configured to run in real-time mode or batched mode. When running in batched mode, sales orders using this strategy will be queued until the configured time period is reached. Both real-time and batched modes result in the creation of a single fulfillment plan.

Within a single business, fulfillment optimization can differ based on the type of customer, channel, and other business attributes. Intelligent Order Management supports the use of multiple fulfillment strategies. Businesses can set up multiple fulfillment strategies with policies or by setting the fulfillment strategy attribute on a sales order during the order intake process. 

#### Set up a fulfillment strategy

To define a strategy, follow these steps.

1. On the **Fulfillment settings** page under **Strategies**, select **Manage**.
1. Select **New**. 
1. On the **Strategies** page, enter values for or set the following properties:

- **Name**: Name of the strategy.
- **Description**: Description of the strategy.
- **Source List**: A list of the fulfillment sources that must be considered when performing the optimization.  
- **Is default**: Whether or not this strategy is the default strategy. There must always be a default strategy set, and only one strategy per organization can be listed as the default strategy. The default strategy is used if a sales order doesn't specify which strategy needs to be used to perform optimization.
- **Enable batch processing**: When this option is turned off, every order gets processed in real-time. When this option is turned on, orders get collected in a queue and are then processed periodically.
-	**Batch processing in minutes**: The time interval for processing each queue, in minutes. The default value is 2 minutes.
- **Owner**: The user who created the strategy. 

There isn't an inventory measure that explicitly needs to be added here. Instead, inventory used for the Fulfillment and Returns Optimization provider must be configured as follows:

To configure inventory in Intelligent Order Management, in the left navigation pane under **Order settings**, change the area to **Settings \> Index and reservation**,and then select **Intelligent Order Management mappings**. Here, you can configure the inventory source and the measure name. The measures used for the Fulfillment and Returns Optimization provider are **Onhand** and **ATP Onhand**. 

### Fulfillment optimization in order orchestration flows

To optimize fulfillment in order orchestration flows, you must first [set up and activate the Fulfillment and Returns Optimization provider](set-up-fro-provider.md).  After the provider is activated, you can enable intelligent optimization using the Fulfillment and Returns Optimization provider as part of the order orchestration journey. As order processing starts, the service picks up orders that need optimization and determines the optimal location from the closest fulfillment source from the list of sources. The Fulfillment and Returns Optimization provider then calculates the latitude and longitude for the fulfillment source address and the order line shipping address. It also calculates the aerial distances between the two addresses. The provider then applies the constraints and determines the optimal fulfillment source. The results are then written to Dataverse for further processing as part of the order orchestration flow.  

An organization can query the fulfillment plan to see the results. Fulfillment plans show the order line details, original quantity on the line, fulfilled quantity, and fulfillment type (fully sourced, partially sourced, not sourced, or exception).  

### Multiple fulfillment strategies in order orchestration flows

The Fulfillment and Returns Optimization provider supports multiple fulfillment strategies that can be set up based on the needs of different businesses. For example, a business may want to fulfill business-to-business (B2B) orders from their distribution centers only, and business-to-consumer (B2C) orders from all of their fulfillment sources (such as distribution centers, warehouses, and stores). With multiple fulfillment strategies, organizations can employ different fulfillment approaches for different sales orders. 

Businesses can set fulfillment strategy attributes for sales orders during the orchestration journey by adding the fulfillment strategy identifier to the sales order. The fulfillment strategy can be set on a sales order based on the source, or by using transformations as part of order intake process. The fulfillment strategy can also be set with policy actions by using sales order attributes and other entities. With policies, businesses can employ the attributes of different entities in the condition builder to set the strategy. If multiple strategies are set up but the policy assignment for the fulfillment strategy isn't configured, the system uses the configured default strategy. 

## Fulfillment plans

The result of any single fulfillment optimization (in batch mode or otherwise) results in a single fulfillment plan. This entity contains details of the breakdown between warehouses and assignment of sales orders to these warehouses. 

The fulfillment plan gets converted into fulfillment orders by an internal Power Automate flow. This entity is consumable by fulfillment providers and can be used by them to move the orchestration process to subsequent steps such as delivery carriers.

## Privacy notice

The Fulfillment and Returns Optimization provider uses the Azure Maps geolocation feature, which is governed by [Service Specific Terms](https://www.microsoft.com/licensing/terms/productoffering/MicrosoftAzure/MCA#ServiceSpecificTerms). The Azure Maps geolocation feature is powered in part by third parties that may operate outside of your tenant's geographic boundary. 

If you enable the Fulfillment and Returns Optimization provider, Microsoft shares your customer's address, city, state, and postal code with third parties to retrieve geolocation information, but doesn't share the email address, phone number, or name of the user who entered the information.

Your privacy is important to Microsoft. For more information, see the [Microsoft Privacy Statement)[https://go.microsoft.com/fwlink/?LinkId=521839].

## Additional resources

[Fulfillment and Returns Optimization architecture](ifo-arch.md)

[Set up Fulfillment and Returns Optimization provider](set-up-fro-provider.md)

[Orchestration flows](orchestration-flows.md)
