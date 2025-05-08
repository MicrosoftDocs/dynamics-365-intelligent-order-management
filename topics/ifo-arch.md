---
title: Intelligent Fulfillment Optimization architecture
description: This topic provides an overview of the architecture for Intelligent Fulfillment Optimization in Microsoft Dynamics 365 Intelligent Order Management.
ms.date: 03/21/2025
ms.custom: 
  - bap-template
ms.author: anvenkat
author: anush6121
ms.topic: article
---

# Intelligent Fulfillment Optimization

[!include [banner](includes/banner.md)]

Intelligent Fulfillment Optimization is an intelligent optimization service that maximizes order fulfillment in the supply chain network. Intelligent Fulfillment Optimization helps you ensure that products are delivered to your customers in the correct quantities, from the correct sources, and at the correct time. Intelligent Fulfillment Optimization can help you maximize profits, minimize costs, and satisfy service-level requirements.

In a modern supply network where product fulfillment can be done from multiple channels, organizations must quickly adapt to order changes, supplier availability issues, or spikes in demand. Intelligent Fulfillment Optimization helps you maximize order fulfillment and find the best source for the delivery of products, based on different business constraints and business objectives, such as minimizing costs by fulfilling from the closest sources.

Intelligent Fulfillment Optimization is built as a microservice. It reads configuration data such as fulfillment sources, source lists, business constraints, and strategies from Microsoft Dataverse, and optimizes order fulfillment. It uses Azure Maps to geo-code shipping address information on orders and fulfillment sources. It also uses Azure Maps to find the distance between the shipping address and the fulfillment source.

## Set up Intelligent Fulfillment Optimization

To enable Intelligent Fulfillment Optimization as part of the order orchestration journey, follow the steps in [Set up Intelligent Fulfillment Optimization provider](set-up-ifo-provider.md) to set up and activate the Intelligent Fulfillment Optimization provider.

## Fulfillment sources

Fulfillment sources are entities that house inventory or provide products. Examples include warehouses, distribution centers, retail stores, drop-ship vendors, and virtual sites. Fulfillment sources can be created and modified on the **Sources** page in Intelligent Order Management (**Fulfillment \> Sources**).

For each of your fulfillment sources, you can define a name that uniquely identifies the source, the time zone where the source or location resides, the type of source (warehouse or other), its address, and its latitude and longitude. You can also specify whether the system should look up inventory in the Inventory Visibility service, for optimized fulfillment that's based on inventory availability.

To look up inventory from the Inventory Visibility service, set the **Use real inventory** field to **On**. To include inventory from a source and make the source available to fulfill the order, set the **Use real inventory** field to **Off** on the **Sources** page.

The system assumes unlimited inventory.

## Fulfillment source lists

Fulfillment source lists let you group a list of sources and manage the sources in a flexible manner, within specific constraints. Fulfillment source lists can be defined on the **Source Lists** page in Intelligent Order Management (**Fulfillment \> Source Lists**).

Depending on your business situation, you can define multiple source lists and use them as needed.

For example, in your strategy definition, you can include all the sources where fulfillment will occur. For your business constraints, you can use a different source list. You can also define different minimum inventory constraints for retail stores and warehouses, and assign your warehouses a higher fulfillment priority than your retail stores.

The **Source Lists** page shows active source lists. To create a new source list, select **New**. Enter a name that will help you easily identify the source list, and add new or existing sources on the **Sources** tab. To remove a source from a source list, select the source on the **Sources** tab, and then select **Remove**.

## Business constraints

Business constraints are an optional component for fulfillment optimization. They're controls that you put in the optimization strategy. The following business constraints are supported:

- Fulfillment location priority
- Maximum distance
- Maximum number of fulfillment sources and partial order

To create or modify constraints, use the **Constraints** page in Intelligent Order Management (**Fulfillment \> Constraints**). To create a constraint of a specific type, select the appropriate constraint type when you create the constraint.

All business constraints share a set of common attributes as part of their definition. The details differ, based on the type of business constraint. The following common attributes are applicable to all business constraints:

- **Name** and **Description** – These attributes identify the business constraint.
- **Start date** and **End date** – Every business constraint must have a period of days when it's enforced.
- **Constraint type** – This attribute indicates the type of business constraint.
- **Is enabled** – You can enable or disable a business constraint.
- **Hard constraint** – A business constraint can be a hard constraint or not a hard constraint.

Every optimization run goes through two iterations. During the first iteration, every business constraint is treated as a hard constraint, regardless of the **Hard constraint** setting. In other words, every constraint is applied. During the second iteration, business constraints that aren't defined as hard constraints are removed. The system then tries to use the reduced constraint set to assign orders or order lines that weren't assigned to sources when the business constraints were applied to sources.

You can define multiple business constraints of each type and apply them to different optimization strategies.

### Fulfillment location priority constraint

The fulfillment location priority constraint enables organizations to define a hierarchy of sources that's based on priority. The optimization service will then consider priority when it identifies fulfillment sources for specific products. Sources that have higher priority will be considered first. The optimization service will then consider other sources. A source that has a priority of **1** is higher priority than a source that has a priority of **2**.

You can define a location priority at the source list level and then define a more specific product-based constraint for sources and products in terms of priority. For write-in products or unknown products, the optimization service uses location priority and assumes that 100 percent of inventory is available at the fulfillment source.

### Maximum distance constraint

The maximum distance constraint enables organizations to define the maximum distance that a source or group of sources can extend to fulfill the order.

You can define the maximum distance for a source list and override it for specific sources. If an overlapping maximum distance constraint is defined for a source, the optimization service will apply the lower of the defined maximum distances.

### Maximum number of fulfillment sources and partial order constraint

The maximum number of fulfillment sources and partial order constraint lets you define whether an order or order lines can be fulfilled by one or multiple sources, and whether they can be partially fulfilled.

When you create this constraint, in the **Maximum providers per order** field, set **Partial lines** and **Partial orders** to **Yes**.

## Fulfillment strategies

A fulfillment strategy helps define the optimization strategy. It brings together objectives, constraints, sources that should be considered, and information about how inventory optimization should occur. You can create and modify a strategy on the **Strategies** page in Intelligent Order Management (**Fulfillment \> Strategies**).

The strategy also defines whether unlimited product inventory or real product inventory is used with the Inventory Visibility service. You can define whether the optimization run is a simulation, whether it can be enabled or disabled, and whether it can be valid for a date range.

Depending on the nature of your business, you can define multiple optimization strategies. You can define the list of fulfillment sources that participate in fulfillment, and define constraints that the optimization service must consider. The constraints are hard constraints that the optimization service will mandatorily impose when it determines the optimal source.

**Fulfillment from the closest source** is supported as the predefined objective in every strategy.

Intelligent Fulfillment Optimization batches the orders that are provided as part of the order journey, to ensure that maximum optimization is obtained for the set of orders.

Within a single business, fulfillment optimization can vary, based on the type of consumer, the channel, and other business attributes. Intelligent Order Management supports the use of multiple fulfillment strategies. Businesses can set up multiple fulfillment strategies either by using policies or by setting the fulfillment strategy attribute on a sales order during the order intake process.

### Set up a fulfillment strategy

To define a strategy, go to the **Strategies** page in Intelligent Order Management (**Fulfillment \> Strategies**), and select **New**. For each strategy, you can enter a unique name and description, provide a source list that consists of fulfillment sources for the strategy, and configure the strategy to use real inventory.

On the **Strategies** page, enter the following information:

- **Source List** – Specify the fulfillment sources that must be considered when the optimization service performs the optimization.
- **Use real inventory** – Specify whether the optimization service should consider inventory from the Inventory Visibility service. If this setting is turned off, the system assumes unlimited inventory at the source. This setting overrides the setting that's defined at the source.
- **Simulation** – Specify whether the strategy should be used to simulate sourcing. In the fulfillment plan output, the system writes a flag to indicate that the processing run is a simulation.
- **Process with empty sales origin** – Set this field to **Yes** if the sales order and line that must be fulfilled don't have a sales origin.
- **Use road distance calculation** – The optimization service calculates the distance between the fulfillment source and the shipping address on the sales order to find the closest source. If you don't enable road distance calculation, the service uses the aerial distance between the two locations.
- **Owner** – The user who created the strategy.
- **Optimization service batching** – The optimization service batches orders that are provided as part of the order orchestration journey and optimizes them together in a batch. The **Aggregation interval minutes** task determines the time interval during which orders that are received are batched together. The **Maximum order line** task determines the number of tasks that should be created based on order lines that are received during the time interval.
- **Inventory visibility data source** – Specify the data source name that should be considered for inventory lookup.
- **Inventory visibility measure name** – Specify the measure name that contains the on-hand inventory for fulfillment optimization.

## Fulfillment optimization in order orchestration flows

For information about how to set up and activate the Intelligent Fulfillment Optimization provider, see [Set up the Intelligent Fulfillment Optimization provider](set-up-ifo-provider.md). After the provider is activated, you can enable intelligent optimization by using Intelligent Fulfillment Optimization as part of the order orchestration journey.

When order processing begins, the service will pick up orders that require optimization, and will determine the optimal location from the closest fulfillment source in the list of sources. Intelligent Fulfillment Optimization will calculate the latitude and longitude for the fulfillment source and the order line's shipping address. It will also calculate the road and aerial distances between the two. It will apply the constraints and then determine the optimal fulfillment source. The results are written to Dataverse for further processing as part of order orchestration flow.

Organizations can query the fulfillment plan to view the results. Fulfillment plans show the order line details, the original quantity on the line, the fulfilled quantity, and the fulfillment type (for example, fully sourced, partially sourced, not sourced, or exception).

## Multiple fulfillment strategies in order orchestration flows

Intelligent Fulfillment Optimization supports multiple fulfillment strategies that can be set up to meet the needs of different businesses. For example, a business might want to fulfill business-to-business (B2B) orders from its distribution centers only and business-to-consumer (B2C) orders from all its fulfillment sources (such as distribution centers, warehouses, and stores). By using multiple fulfillment strategies, organizations can employ different fulfillment approaches for different sales orders.

Businesses can set fulfillment strategy attributes for sales orders during the orchestration journey by adding the fulfillment strategy identifier to the sales order. The fulfillment strategy can be set on a sales order either based on the source or by using transformations as part of the order intake process. The fulfillment strategy can also be set with policy actions by using sales order attributes and other entities. By using policies, businesses can employ the attributes of different entities in condition builder to set the strategy. If multiple strategies are set up, but policy assignment isn't configured for the fulfillment strategy, the system will select the first strategy that's available.

## Additional resources

[Intelligent Fulfillment Optimization architecture](ifo-arch.md)

[Set up Intelligent Fulfillment Optimization provider](set-up-ifo-provider.md)

[Orchestration flows](orchestration-flows.md)
