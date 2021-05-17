---
author: josaw1
description: This topic provides an introduction to Distributed Order Management and instructions on how to set it up in Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 05/17/2021
ms.topic: conceptual
ms.author: josaw

title: Distributed Order Management (preview)
---


# Distributed Order Management (preview)

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

Dynamics 365 Distributed Order Management is an intelligent optimization service that maximizes order fulfillment within the supply chain network. Distributed Order Management helps you ensure that products are delivered to your customers with the right quantities, from the right sources, and at the right time. Distributed Order Management can help you maximize profits, minimize costs, and satisfy service-level requirements.  

In a modern supply network where product fulfillment can be from multiple channels, organizations must quickly adapt to order changes, supplier availability issues, or a spike in demand. Distributed Order Management helps you maximize order fulfillment and find the right source for delivery of products based on different business constraints and business objectives such as minimizing costs by fulfilling from the closest sources.  

Distributed Order Management is built as a microservice. It reads configuration data such as fulfillment sources, source lists, business constraints, and strategies from Microsoft Dataverse, and optimizes the order fulfillment. It uses Bing Maps to geo-code shipping address information on orders and fulfillment sources. It also uses Bing Maps to find the distance between the shipping address and fulfillment source.

> [!NOTE]
> Dynamics 365 Distributed Order Management is a preview service and can only be used in sandbox environments for non-production purposes.

## Set up Distributed Order Management

To enable Distributed Order Management as part of the order orchestration journey, set up the Dynamics 365 Distributed Order Management provider on the **Providers > Catalog** page in Dynamics 365 Intelligent Order Management. Find Dynamics 365 Distributed Order Management in the list of providers and select **Add Provider**. After you accept the terms and conditions, Distributed Order Management will be enabled in the list of installed providers under **Providers > Installed**.

When the Distributed Order Management provider is set up, you can enable the action **Send Order to DOM** in the order orchestration designer and use its capabilities to optimize orders.

## Fulfillment sources 

Fulfillment sources are entities like warehouses, distribution centers, retail stores, drop-ship vendors, or virtual sites that house inventory or provide products. Fulfillment sources can be created and modified on the **Fulfillment > Sources** page in Intelligent Order Management.

For each of your fulfillment sources, you can define a name to uniquely identify them, time zone where the source or location resides, type of source (warehouse or other), address where it is located, latitude and longitude, and whether the system should look up inventory in the Inventory Visibility service for optimized fulfillment based on inventory availability.

To look up inventory from the Inventory Visibility service, set the **Use real inventory** field to **On**. To include inventory from a source and make the source available to fulfill the order, on the **Fulfillment > Sources** page, set the **Use real inventory** field to **Off**.

For the preview release, the system assumes unlimited inventory. 

## Fulfillment source lists

Fulfillment source lists enable you to group a list of sources and manage sources in a flexible manner, within specific constraints. Fulfillment source lists can be defined on the **Fulfillment > Source Lists** page in Intelligent Order Management.

Depending on your business situation, you can define multiple source lists and use them as needed.  

For example, in your strategy definition, you can include all the sources where fulfillment will occur. For your business constraints, you can use a different source list. You can also define different minimum inventory constraints for retail stores and warehouses, and assign your warehouses a higher fulfillment priority than your retail stores.  

Active source lists are displayed on the **Fulfillment > Source Lists** page. To create a new source list, select **New**. Provide a name to easily identify the source list and add existing or new sources on the **Sources** tab. To remove a source from a source list, select the source on the **Sources** tab and then select **Remove**.

## Business constraints 

Business constraints are an optional component for fulfillment optimization. These are controls that you put in the optimization strategy. As part of the preview release, the following business constraints are supported.  

-   Location or source priority.

-   Maximum of fulfillment sources and partial order. 

-   Maximum distance.

To create or modify constraints, go to the **Fulfillment > Constraints** page in Intelligent Order Management. To create a specific constraint type, select the appropriate constraint type when you create the constraint.

Every business constraint shares a set of common attributes as part of its definition. The details differ based on the type of business constraint. The following are common attributes applicable to all business constraints. 

- **Name and Description**: A way to identify the business constraint.  

- **Start date / End date**: Every business constraint must have a period of days when the constraint is enforced.  

- **Constraint type**: This attribute indicates the type of business constraint.

- **Is enabled**: You can enable or disable a business constraint.  

- **Hard constraint**: A business constraint can be a hard constraint or not a hard constraint.  

Every optimization run goes through two iterations. First, every business constraint is treated as a hard constraint regardless of the **Hard constraint** setting, so every constraint is applied. Then, the business constraints that aren't defined as hard constraints are removed. The system will attempt to assign order or order lines that weren't assigned to sources when the business constraints were applied to sources with the reduced constraint set. 

You can define multiple business constraints of each type and apply them to different optimization strategies.  

### Fulfillment location priority constraint 

The fulfillment location priority constraint type allows organizations to define a hierarchy of sources by using priority. The optimization service will then consider priority when identifying fulfillment sources for specific products. Sources with higher priority are considered first, then the optimization service will resolve to other sources. A source with a priority of **1** is higher priority than a source with priority **2**.  

You can define a location priority at the source list and then define a more specific product-based constraint for source and product in terms of priority.  For write-in products, or unknown products, the optimization service will use location priority and assume 100% inventory is available at the fulfillment source. 

### Maximum distance constraint 

The maximum distance constraint enables an organization to define the maximum distance a source or group of sources can extend to fulfill the order.  

You can define the maximum distance for a source list and override for a specific source. If there is an overlapping maximum distance constraint defined for a source, the optimization service will apply the lower of the defined maximum distance for those sources. 

### Maximum number of fulfillment sources and partial order constraint 

The maximum number of fulfillment sources and partial order constraint enables you to define whether an order or order lines can be fulfilled by one or multiple sources and whether it can be partially fulfilled.  

When you create this constraint, in the **Maximum providers per order** field, set **Partial lines** and **Partial orders** to **Yes.**

## Fulfillment strategies 

A fulfillment strategy helps define the optimization strategy. It brings together objectives, constraints, sources to be considered, and how inventory optimization should occur. You can create and modify a strategy on the **Fulfillment > Strategies** page in Intelligent Order Management.

The strategy also defines whether unlimited product inventory is used, or real product inventory is used with the Inventory Visibility service. You can define whether the optimization run is a simulation, if it can be enabled or disabled, and if it can be valid for a date range. 

Depending on the nature of your business, you can define multiple optimization strategies. You can define the list of fulfillment sources that participates in fulfillment and define constraints that the optimization service must consider. The constraints are hard constraints that the optimization service will mandatorily impose when it determines the optimal source.  

For the preview release, **Fulfillment from the closest source** is supported as the pre-defined objective in every strategy.

Distributed Order Management batches the orders that are provided as part of the order journey to ensure maximum optimization is obtained for these set of orders. 

### Set up a fulfillment strategy

To define a strategy, go to the **Fulfillment > Strategies** page in Intelligent Order Management and select **New**. For each strategy, you can provide a unique name, description, source list consisting of fulfillment sources for the strategy, and you can configure the strategy to use real inventory.   

On the **Strategies** page, enter values for the following.

- **Source List**: The fulfillment sources that must be considered when the optimization service is performing the optimization.  

- **Use real inventory**: Indicates whether the optimization service should consider inventory from the Inventory Visibility service. If this setting is turned off, the system assumes unlimited inventory at the source. This setting overrides the setting that is defined at the source.  

- **Simulation**: Indicates if the strategy will be used to simulate sourcing. In the **Fulfillment plan** output, the system writes a flag to indicate that the processing run is a simulation. 

- **Process with empty sales origin**: Set this field to **Yes** if the sales order and line to be fulfilled don't contain a sales origin.  

- **Use road distance calculation**: The optimization service calculates the distance between fulfillment source and shipping address on the sales order to find the closest source. If road distance calculation is not enabled, the service uses aerial distance between the two locations.

- **Owner**: The user who created the strategy.  

- **Optimization service batching**: The optimization service batches orders that are provided as part of the order orchestration journey and optimizes them together in a batch. The **Aggregation interval minutes** task determines the time window within which orders received are batched together. The **Maximum order line** task determines the number of tasks that should be created based on order lines that are received within the time interval.  

## Fulfillment optimization as part of order orchestration flows

To enable intelligent optimization using Distributed Order Management as part of the order orchestration journey, add the **Send to DOM** node to the journey designer on the **Orchestration > Flows page**. As order processing starts, the service will pick up orders that need optimization and determine the optimal location from the closest fulfillment source from the list of sources. Distributed Order Management will calculate the latitude and longitude for the fulfillment source and the order line shipping address. It will also calculate the road and aerial distances between the two. It will apply the constraints and then determine the optimal fulfillment source. The results are written to Dataverse for further processing as part of order orchestration flow.   

An organization can query the fulfillment plan to see the results. Fulfillment plans show the order line details, original quantity on the line, fulfilled quantity, and fulfillment type including fully sourced, partially sourced, not sourced, or exception.  
