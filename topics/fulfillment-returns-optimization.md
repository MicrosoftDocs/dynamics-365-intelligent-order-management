---
author: anvenkat
description: Learn about the Fulfillment and Returns Optimization provider in Microsoft Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 01/28/2026
ms.custom: 
  - bap-template
ms.topic: overview
ms.author: anvenkat
title: Fulfillment and Returns Optimization provider overview
---

# Fulfillment and Returns Optimization provider overview

[!include [banner](includes/banner.md)]

This article provides an overview of the Fulfillment and Returns Optimization provider in Microsoft Dynamics 365 Intelligent Order Management.

The Fulfillment and Returns Optimization provider is an intelligent optimization service that determines the source of order fulfillment while achieving required goals and respecting the desired configuration that the business determines. The Fulfillment and Returns Optimization provider helps you ensure that products are delivered to your customers in the right quantities, from the right sources, and at the right time. Therefore, it can help you maximize profits, minimize costs, and satisfy service-level requirements.

In a modern supply network where product fulfillment can come from multiple channels, organizations must quickly adapt to order changes, supplier availability issues, or spikes in demand. The Fulfillment and Returns Optimization provider helps you maximize order fulfillment and find the right source for the delivery of products based on different business constraints and business objectives such as minimizing costs by fulfilling orders from the closest sources.

The Fulfillment and Returns Optimization provider is built as a microservice and reads configuration data such as fulfillment sources, source lists, business constraints, and strategies from Microsoft Dataverse to optimize order fulfillment. The provider uses Azure Maps to provide geocode shipping address information for orders and fulfillment sources, and to provide the distance between those locations.

## Fulfillment and Returns Optimization provider settings

To enable the Fulfillment and Returns Optimization provider as part of the order orchestration journey, set up and activate the Fulfillment and Returns Optimization provider by following the instructions in [Set up Fulfillment and Returns Optimization provider](set-up-fro-provider.md). After the provider is activated, set the following settings to achieve business goals.


## Configurate Intelligent Order Management mappings

It's important to maintain the **Intelligent Order Management mappings** as a prerequisite for the fulfillment and returns optimization engine to work correctly. For more information, see [Set up inventory visibility provider](set-up-inventory-visibility-provider.md). 

> [!Note]
> You need to set up calculated measure mappings if fulfillment happens through Microsoft Dynamics 365 finance and operations apps.

### Sources

Fulfillment sources are entities that house inventory or provide products. Examples include warehouses, distribution centers, retail stores, drop-ship vendors, and virtual sites. You can create and modify fulfillment sources by selecting the area switcher at the bottom of the left navigation pane and switching to **Settings \> Fulfillment Settings**. Then, on the **Fulfillment settings** page, under **Sources**, select **Manage**.

For each fulfillment source, you can perform the following actions:

- Define a unique name.
- Set the time zone of the source.
- Set the type of source (warehouse or other).
- Specify where the source is located (latitude and longitude).
- Specify where the system should look for inventory in the Inventory Visibility service.

If you use Intelligent Order Management with finance and operations apps, map each fulfillment source to a shipping warehouse. Maintain the shipping warehouse assigned in fulfillment source settings.

Add details about the average processing time of orders in a warehouse. This information determines the planned shipment date of various orders. You can also set the cutoff time of a warehouse. This information is used if the **Respect warehouse timings constraint** setting is enabled, so that orders can be sent to a warehouse only between 12 AM and the cutoff time.

### Source lists

Fulfillment source lists let you group a list of sources and manage the sources in a flexible manner, within specific constraints. To define fulfillment source lists, on the **Fulfillment settings** page, under **Source lists**, select **Manage**.

Depending on your business situation, you can define multiple source lists and use them as needed.

For example, in your strategy definition, include all the sources where fulfillment occurs. For your business constraints, use a different source list. You can also define different maximum distance constraints for retail stores and warehouses, and restrict partial fulfillment for only your retail stores.

The **Manage** page shows active source lists (**Source Lists \> Manage**). To create a new source list, select **New**. Enter a name that helps you easily identify the source list, and then add new or existing sources on the **Sources** tab. To remove a source from a source list, select the source on the **Sources** tab, and then select **Remove**.

### Constraints

Constraints are an optional component of fulfillment optimization. The following business constraints are supported:

- Maximum distance
- Restrict partial fulfillment of orders
- Limit number of warehouses per order
- Respect warehouse timings
- Maximum order lines
- Limit number of warehouses per order line
- Safety stock constraint

To create or modify constraints, on the **Fulfillment settings** page, under **Constraints**, select **Manage**. To create a constraint of a specific type, select the appropriate constraint type when you create the constraint.

All business constraints share a set of common attributes as part of their definition. The details differ, based on the type of business constraint. The following common attributes are applicable to all business constraints:

- **Name** – This attribute is used to identify the business constraint.
- **Description** – This attribute is used to describe the business constraint.
- **Constraint type** – This attribute indicates the type of business constraint.
- **Is enabled** – This attribute is used to enable or disable a business constraint.

You can define multiple business constraints of each type and apply them to different optimization strategies.

#### Maximum distance constraint

The maximum distance constraint enables an organization to define the maximum distance that a source or group of sources can extend to fulfill an order. Currently, distance is considered as the straight-line distance between the source and the customer address, as calculated by Azure Maps.

You can define the maximum distance for a source or a source list. When you define the maximum distance for a source list that contains an individually defined source distance, there might be an overlapping maximum distance constraint defined for the source. In this case, the optimization service applies the lowest defined maximum distance for the sources.

The following illustration shows an example where the Seattle warehouse can deliver only up to 10 miles from its radius, even though it's part of the **All Sources** list, where the maximum distance is 50 miles. Because of the way that this constraint works, the shortest distance is used if there's a conflict.

:::image type="content" source="media/constraint-max-radius.png" alt-text="Screenshot of the maximum radius constraint example showing Seattle warehouse with a 10-mile delivery radius.":::

If, as a result of a constraint, no warehouse is suitable for a sales order, the system can't create any fulfillment order for the sales order. Instead, the status of the sales order changes to **Inventory not found**.

#### Restrict partial fulfillment of orders constraint

Sometimes, the Fulfillment and Returns Optimization provider must handle scenarios where demand exceeds supply. By default, when Intelligent Order Management receives orders that require more quantity than the available inventory, it splits sales orders by order line. Some lines of the order are then fulfilled, whereas others are either backordered or set to the **Inventory not found** order state. An individual order line can't be split further and partially assigned, but it can be assigned to different sources. When you enable the **Restrict partial fulfillment of orders constraint**, the Fulfillment and Returns Optimization provider ensures that either the entire order is fulfilled or the order isn't fulfilled at all.

#### Respect warehouse timings constraint

Businesses sometimes have delivery trucks that leave at a specific time every day. To optimize for this scenario, each source can be configured to have a different cutoff time. To ensure that this constraint works as expected, before you run it, add cutoff times to the warehouses that must respect them.

When you enable the **Respect warehouse timings constraint**, the Fulfillment and Returns Optimization provider ensures that sources create fulfillment orders only if those orders can be sent to the warehouse before the cutoff times. If they can't, the Fulfillment and Returns Optimization provider tries to assign the sales orders to warehouses that are still open to processing orders. In this way, the Fulfillment and Returns Optimization provider optimizes for faster fulfillment and delivery.

#### Limit number of warehouses per order constraint

There can be instances where not all inventory is available at a single source. To fulfill orders in these cases, the Fulfillment and Returns Optimization provider splits a single sales order and assigns different warehouses to different parts of it. The limit number of warehouses constraint lets you control the degree to which orders are split.

You can configure this constraint to specify the maximum number of warehouses that you want a single order to be split among. In other words, if you specify three warehouses for this constraint, every sales order must be fulfilled from one, two, or three different warehouses. If you prefer the whole sales order to be fulfilled from only one fulfillment source, specify one as the maximum number of warehouses. If fulfillment of a sales order requires more than three warehouses, the sales order isn't fulfilled at all unless the **Restrict partial fulfillment of orders** constraint is disabled and the **Limit number of warehouses** constraint is enabled.

By default, the Fulfillment and Returns Optimization provider splits a sales order among as many warehouses as are required, while also respecting inventory conditions and other constraints.

To specify the number of warehouses to split orders among, select **New Limit Number of Warehouses Constraint** to add an entry, and then select **Save**.

#### Limit number of warehouses per order line constraint

You can configure this constraint to specify the maximum number of warehouses that you want a single order line to be split among. In other words, if you don't want to fulfill a single order line from multiple sources, specify one as the maximum number of warehouses.

#### Maximum number of order lines constraint

Sometimes, fulfillment sources can't process more than some order lines on a given day because of capacity or resource limitations. Use the **Maximum number of order lines** constraint to limit the number of order lines that route to a single fulfillment source. You can configure this constraint to specify the maximum order lines per day, per fulfillment source, or per source list. After the number is reached for the fulfillment source or source list, order lines aren't considered for selection during that day.

#### Maintaining safety stock

Some businesses maintain safety stocks to efficiently manage customer demand and to avoid running too low on inventory. The Fulfillment and Returns Optimization provider lets you maintain safety stock at two levels for each of your fulfillment sources.

The Fulfillment and Returns Optimization provider excludes a fulfillment source if inventory for the product is below the safety stock level. To configure the safety stock constraint, perform the following setup steps:

- **Safety stock constraint:** Create a new constraint, and set the **Constraint type** field to **Safety stock Constraint**.
- **Safety stock at fulfillment source:** Maintain the safety stock on the fulfillment source.

After you complete this setup, the Fulfillment and Returns Optimization provider excludes the fulfillment source if on-hand inventory is below the safety stock limit.

#### Introducing soft constraints

Define constraints as **hard** or **soft** in the constraint setup. When you define a constraint as soft, the selection includes it only if it can be respected in the fulfillment source determination algorithm.

By default, constraints are hard constraints until you disable them. To define a constraint as a soft constraint, set the **Is hard constraint** option to **No** in constraint setup.

For example, **Limit to one warehouse** is set up as a soft constraint. Therefore, it first checks to determine whether the order can be fulfilled by a single source. If the order can't be fulfilled by a single source, multiple sources are used.

#### Activating and deactivating a fulfillment source

Sometimes businesses want to exclude certain fulfillment sources, due to various reasons, either temporarily or permanently. Fulfillment and returns optimization offers flexibility to turn on or off the fulfillment source based on your needs. To exclude the fulfillment source, select **Deactivate** on the fulfillment source settings. If you want to include it back again, select **activate** on the fulfillment source settings.

### Strategies

A strategy helps define the optimization configuration that achieves your business needs. A strategy brings together objectives, constraints, and sources that you should consider, and specifies how inventory optimization should occur. To create and modify a strategy, on the **Fulfillment settings** page, under **Strategies**, select **Manage**.

The predefined objective of every strategy is to fulfill orders while minimizing distance.

Depending on the nature of your business, you can define multiple optimization strategies. You can define a list of fulfillment sources that participate in fulfillment, and define constraints that the optimization service must enforce. Those constraints are hard constraints that the optimization service mandatorily imposes when it determines the optimal source. You can configure a strategy as the default strategy. However, only one strategy can be the default strategy at any single time.

You can configure a strategy to run in either real-time mode or batched mode. When a strategy runs in batched mode, sales orders that use it queue until the configured period is reached. Both real-time mode and batched mode result in the creation of a single fulfillment plan.

Within a single business, fulfillment optimization can vary, based on the type of customer, the channel, and other business attributes. Intelligent Order Management supports the use of multiple fulfillment strategies. Businesses can set up multiple fulfillment strategies either by using policies or by setting the fulfillment strategy attribute on a sales order during the order intake process.

#### Set up a fulfillment strategy

To define a strategy, follow these steps:

1. On the **Fulfillment settings** page, under **Strategies**, select **Manage**.
1. Select **New**. 
1. On the **Strategies** page, set the following fields:

    - **Name** – Enter the name of the strategy.
    - **Description** – Enter a description of the strategy.
    - **Source List** – Define the list of fulfillment sources that the optimization service must consider when performing optimization.
    - **Is default** – Specify whether the strategy is the default strategy. There must always be a default strategy, and only one strategy per organization can be set as the default strategy. The default strategy is used if a sales order doesn't specify which strategy must be used to perform optimization.
    - **Enable batch processing** – When this option is turned off, every order is processed in real time. When it's turned on, orders are collected in a queue and then processed periodically.
    - **Batch processing in minutes** – Specify the time interval for processing each queue, in minutes. The default interval is two minutes.
    - **Owner** – The user who created the strategy.

Don't explicitly add any inventory measure here. Instead, configure inventory for the Fulfillment and Returns Optimization provider in Intelligent Order Management as follows:

1. In Intelligent Order Management, in the left navigation pane, under **Order settings**, change the area to **Settings \> Index and reservation**, and then select **Intelligent Order Management mappings**.
1. Configure the inventory source and the measure name. The measures that the Fulfillment and Returns Optimization provider uses are **Onhand** and **ATP Onhand**.

### Fulfillment optimization in order orchestration flows

To optimize fulfillment in order orchestration flows, first [set up and activate the Fulfillment and Returns Optimization provider](set-up-fro-provider.md). After you activate the provider, you can enable intelligent optimization by using the Fulfillment and Returns Optimization provider as part of the order orchestration journey.

When order processing begins, the service picks up orders that require optimization and determines the optimal location from the closest fulfillment source in the list of sources. The Fulfillment and Returns Optimization provider then calculates the latitude and longitude for the fulfillment source address and the order line's shipping address. It also calculates the aerial distances between the two addresses. The provider then applies the constraints and determines the optimal fulfillment source. The results are written to Dataverse for further processing as part of the order orchestration flow.

An organization can query the fulfillment plan to view the results. Fulfillment plans show the order line details, original quantity on the line, fulfilled quantity, and fulfillment type (fully sourced, partially sourced, not sourced, or exception).

### Multiple fulfillment strategies in order orchestration flows

The Fulfillment and Returns Optimization provider supports multiple fulfillment strategies that you can set up based on the needs of different businesses. For example, a business might want to fulfill business-to-business (B2B) orders from its distribution centers only and business-to-consumer (B2C) orders from all its fulfillment sources (such as distribution centers, warehouses, and stores). By using multiple fulfillment strategies, organizations can employ different fulfillment approaches for different sales orders.

Businesses can set fulfillment strategy attributes for sales orders during the orchestration journey by adding the fulfillment strategy identifier to the sales order. Set the fulfillment strategy on a sales order based on the source, or by using transformations as part of the order intake process. You can also set the fulfillment strategy with policy actions by using sales order attributes and other entities. By using policies, businesses can employ the attributes of different entities in the condition builder to set the strategy. If you set up multiple strategies but don't configure the policy assignment for the fulfillment strategy, the system uses the configured default strategy.

#### Alternate strategy

The Fulfillment and Returns Optimization provider also supports defining an alternate strategy to allow for more flexibility in rule-based fulfillment. If the default strategy that you assign to the order is unsuccessful at determining the fulfillment source for the order or the order lines, the alternate strategy is used instead. For example, businesses might want to use retail store inventory by default to fulfill orders, but to use distribution centers if there's no retail store inventory. By having the flexibility to define an alternate strategy, organizations can multiply the options for rule-based fulfillment.

Specify an alternate strategy in the **General** section of the **Strategies** page.

## Fulfillment plans

The result of any single fulfillment optimization (in batch mode or otherwise) is a single fulfillment plan. This entity contains details of the breakdown between warehouses and the assignment of sales orders to these warehouses.

An internal Power Automate flow converts the fulfillment plan into fulfillment orders. Fulfillment providers can consume the entity and use it to move the orchestration process to subsequent steps, such as delivery carriers.

## Privacy notice

The Fulfillment and Returns Optimization provider uses the Azure Maps geolocation feature, which is governed by [Service Specific Terms](https://www.microsoft.com/licensing/terms/productoffering/MicrosoftAzure/MCA#ServiceSpecificTerms). Third parties power the Azure Maps geolocation feature, and they might operate outside of your tenant's geographic boundary.

If you enable the Fulfillment and Returns Optimization provider, Microsoft shares your customer's address, city, state, and postal code with third parties to retrieve geolocation information. Microsoft doesn't share the email address, phone number, or name of the user who entered the information.

Your privacy is important to Microsoft. For more information, see the [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?LinkId=521839).

## Additional resources

[Fulfillment and Returns Optimization architecture](ifo-arch.md)

[Set up Fulfillment and Returns Optimization provider](set-up-fro-provider.md)

[Orchestration flows](orchestration-flows.md)
