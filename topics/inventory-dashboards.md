---
author: josaw1
description: This topic provides an overview of inventory-related dashboards in Microsoft Dynamics 365 Intelligent Order Management.
ms.date: 05/28/2022
ms.topic: conceptual
ms.author: josaw

title: Inventory dashboards
---

# Inventory dashboards

[!include [banner](includes/banner.md)]

This topic provides an overview of inventory-related dashboards in Microsoft Dynamics 365 Intelligent Order Management.

Inventory management is one of the most expensive parts of the order management process. Intelligent Order Management's inventory dashboards can provide you with visibility into which items your business has in stock versus the demand for those items, and can also provide other relevant key performance indicators (KPIs) that can help you lower costs. 

The following example image shows an Intelligent Order Management's inventory dashboard.

![Screenshot of inventory dashboard.](media/InventoryDashboard.png)

The following sections cover prerequisites, setup, and the various KPIs and graphs described in the dashboard.

## Prerequisites and setup

To view inventory dashboards on an Intelligent Order Management organization, you must first ensure that your organization's Intelligent Order Management build version is 1.0.0.4354 or above.

Dashboards can only provide useful information if your business is using Intelligent Order Management with the Inventory Visibility service and has it configured to work. For more information, see [Inventory Visibility Add-in overview](/dynamics365/supply-chain/inventory/inventory-visibility).

To configure the Inventory Visibility service for your Intelligent Order Management organization, follow these steps.

1. In Intelligent Order Management for your organization, on the bottom of the left navigation pane, select the area switcher, and then select **Configurations**.
1. Under **Inventory visibility**, go to the **Index and reservation** section.
1. On the far right, select the **Feature management** tab.
1. Turn on the **xx** toggle. This ensures that data flows from the Inventory Visibility service into Intelligent Order Management for consumption by the dashboard.
1. Next, you must enable Microsoft Power BI Insights. On the left navigation pane, select **Power BI Insights**
1. Select **Manage**, set the status to **Enabled**, and then select **Save & Close**.

## Visualizations

The following sections provide information on inventory dashboard visualizations such as filters, KPIs, graphs, and tables. 

### Filters

Two filters are provided out-of-the-box: **Product name** and **Location ID**. When you need to drill down on one or more products or locations, these interactive dashboard filters will refine your data to show the KPIs and graphs for the selected products or locations.

#### Product name

Product name information flows into the inventory dashboard from the **Products** section of Intelligent Order Management. The **Products** section contains data for all products for which sales orders can be created and inventory can be recorded.

#### Location ID

The location ID data flows into the inventory dashboard from the inventory dashboard configuration page.

### KPIs

- **Physical available**: This value is the sum of all units that are physically available in the warehouse. It includes items that are "soft" reserved. Whenever there's an upload of inventory data to the system, this KPI value is updated. When items are shipped out of warehouses, the number of items is deducted from the KPI value.
- **Soft reserved**: Once fulfillment optimization occurs and the warehouse(s) are determined for sales orders, the respective items in that warehouse are "soft reserved". When items are soft reserved, the number of these items is added to this KPI value, which ensures that the same items don't get double booked against two different orders. Once soft reserved items are shipped, the number of these items is deducted from this KPI value.
- **Onhand inventory**: This value shows the number of units actually available when evaluating the warehouse source for sales orders. It's calculated by subtracting the **Soft reserved** KPI value from the **Physical available** KPI value. When a fulfillment optimization runs, the **Onhand inventory** KPI value is the inventory value that is considered.
- **New order line qty**: This value calculates the total number of units of product in demand by looking at all order lines in a new state and adding all of their quantity values. 
- **Returned**: This value shows the number of product units that have been returned to the warehouse after being sold to customers.
- **Return rate**: This value shows the rate of return of units of products that have been returned to the warehouse after being sold to customers. It's calculated as (units returned/units sold) x 100.
- **Sell rate**: This value shows the rate of items being sold to customers. It's calculated as (units sold - units returned)/(units in stock + units sold)] x 100.
- **Out-of-stock**: This value shows the number of units of products that have to be replenished in order to fulfill demand. It's calculated as (units in supply - units in demand).

### Graphs

- **Supply by product name**: This stacked bar chart shows a breakdown of the inventory supply by product name. It shows the distribution of on hand, soft reserved, and returned quantities of the product. Each bar total represents the physical available KPI for the product.
- **Supply by location ID**: This stacked bar chart shows a breakdown of the inventory supply by location. It shows the distribution of on hand, soft reserved, and returned quantities of the product. Each bar total represents the physical available KPI for location.
- **Return rate by product name**: This bar chart shows the rate of return broken down by product name.
- **Stockout and near stockout item**: This chart shows the number of product units that are understocked or nearing that state as compared to demand. The bars below the zero line represent the products that are understocked, and the values on the bar represent the number for those product units that need immediate attention. The bars above the zero line represent the products that are nearing the understocked state, and the values on the bar represent the number of those product units that will remain once the current demand is satisfied.

### Table

- **Products**: This is a tabular representation of all products and their individual KPIs as described in the KPIs section above.

## Frequently asked questions

#### How long does it take after setup for the dashboard to provide useful information on the organization?

It can take up to 24 hours after the initial setup for the reports to be provisioned. If it takes longer, contact Microsoft Support for assistance.

#### Does the inventory dashboard represent data in real time?

At this time, the inventory dashboard is more suitable to be used as a daily report to assess the health of a business's inventory rather than as a real-time representation of inventory information. You can expect to see a 4-10 hour latency on the information flowing into the inventory dashboard. A feature to provide real-time information on the inventory dashboard is planned for an upcoming release.

#### Can I see data for specific products that I care about?

Yes, there are product name and location ID filters that can be used to refine the product data being represented in the KPIs and graphs.

#### Can I sort the data differently than what is made available out-of-box?

Yes. When you hover on a graph, you'll see a vertical ellipsis on the top right corner of the graph. To resort the data, select the ellipsis, select **Sort axis**, and then select the option that you want.

#### Can I modify the KPIs that the dashboard provides?

At this time, the KPIs provided are the only ones currently available. After doing market research, these KPIs were determined to be the most useful for most businesses. If you have suggestions regarding adding or modifying the KPIs or graphs, reach out to the team at <D365OMS@microsoft.com>.

#### I'm unsure how some of these KPIs are being calculated, how do I get more information?

The way these KPIs are calculated is described in the [KPIs](#kpis) section above. You can also hover on an inventory dashboard KPI number (not the KPI name) to see a tooltip that describes how that KPI is being calculated.

#### Can I look for historical information of the inventory?

All data displayed on the inventory dashboard is a current representation of the inventory system (keeping in mind a latency time of 4-10 hours). Looking at previous states of the inventory system isn't currently supported.
