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

Inventory management is one of the most expensive parts of the order management process. Intelligent Order Management's inventory dashboards can give you visibility into what items your business has in stock versus the demand for those items, and can also provide other relevant key performance indicators (KPIs) that can help you lower costs. 

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

The following sections provide information on inventory dashboard filters, KPIs, graphs, and tables. 

### Filters

Two filters are provided out-of-the-box: **Product name** and **Location ID**. When you need to drill down on one or more products or locations, these interactive dashboard filters will refine your data to show the KPIs and graphs for the selected products or locations.

#### Product name

Product name information flows into the inventory dashboard from the **Products** section of Intelligent Order Management. The **Products** section contains data for all products for which sales orders can be created and inventory can be recorded.

#### Location ID

The location ID data flows into the inventory dashboard from the inventory dashboard configuration page.

### KPIs

- **Physical available**: This value is the sum of all units that are physically available in the warehouse. It includes the items that are soft reserved. Whenever there is an upload of inventory data to the system, this KPI is updated. Once items get shipped out of the warehouse(s), this KPI is deducted.
- **Soft reserved**: Once fulfillment optimization happens and the warehouse(s) are determined for sales orders, the respective items in that warehouse are software reserved. When this happens, this KPI is added to. This is to ensure that the same items do not get double booked against two different orders. Once orders are shipped, this KPI is deducted.
- **Onhand inventory**: This value shows the number of units actually available for consideration when evaluating the warehouse source for sales orders. It is calculated as the $physical Available - soft Reserved$. When a fulfillment optimization runs, this is the inventory value that is considered.
- **New order line qty**: This value calculates the total number of units of product in demand by looking at all the order lines in new state and adding all its quantity values. 
- **Returned**: This value shows the number of units of products that have been returned to the warehouse after being sold to end customers.
- **Return rate**: This value shows the rate of return of units of products that have been returned to the warehouse after being sold to end customers. It is calculated as the total number of $(units Returned/units Sold) * 100 $.
- **Sell rate**: This value shows the rate of items being sold to end customers. It is calculated as $ [(unitsSold - unitsReturned)/(unitsInStock + unitsSold)] * 100 $.
- **Out-of-stock**: This value shows the number of units of products that have to be replenished in order to fulfill demand. It is calculated as a summation of $max[(supply - demand), 0]$.

### Graphs

- **Supply by product name**: This stacked bar chart shows a break down of the inventory supply by product name. It shows the distribution of onhand, soft reserved and returned quantities of the product. Each bar total represents the physical available KPI for the product.
- **Supply by location ID**: This stacked bar chart shows a break down of the inventory supply by the location. It shows the distribution of onhand, soft reserved and returned quantities of the product. Each bar total represents the physical available KPI for the location.
- **Return rate by product name**: This bar chart shows the rate of return broken down by product name.
- **Stockout and near stockout item**: This chart shows the number of units of products that are under stocked or nearing that state as compared to its demand. The bars below the zero line represent the products that are under stocked and the values on the bar represent the number of units of said products that need immediate attention. The bars above the zero line represent the products that are nearing the under stocked state and the values on the bar represent the number of units of said products that will be left once the current demand is satisfied.

### Table

- **Products**: This is a tabular representation of all the products and their individual KPIs as described in the KPI section above.

## Frequently asked questions

#### How long does it take after setup for the dashboard to light up on the org?

It can take up to 24 hours after initial set up for the reports to be provisioned. If it takes more than that, please contact Microsoft Support and we will help you out at the earliest.

#### Is this dashboard real time?

This dashboard is more suitable to be used as a daily report to assess the health of a business' inventory rather than as a real-time representation of the inventory information. One can expect to see a 4-10 hour latency on the information flowing in. We fully acknowledge that real-time data on inventory is very valuable to businesses and hence in our upcoming October 2022 wave, we are adding a feature to provide real-time information on inventory.

#### Can I see data for specific products that I care about?

Yes, we have filters on product name and location ID. They are multi-select filters and can be used to automatically slice up the data being represented in the KPIs and graphs.

#### Can I sort the data differently than what is made available out-of-box?

Yes, hover on the graph till you see three small icons appearing on the top right corner of the graph. Click on the three dots (third icon), go to *Sort axis* and choose the option you want.

#### Can I modify the KPIs that the dashboard provides today?

Unfortunately, the KPIs we provide today are the only ones available at the moment. Upon doing market research, these were determined to be most useful for majority of businesses, but we are always looking for suggestions. Log an idea here - if we want us to consider adding or modifying our KPIs or graphs.

#### I'm unsure of how some of these KPIs are being calculated. How do I get more information on that?

The way these KPIs are being derived is described in the section called *KPIs* above. Additionally, you can also hover on the KPI (not the KPI name) to see a tooltip that describes how the KPI is being calculated.

#### Can I look for historical information of the inventory?

All the data being displayed in this dashboard is a current representation of the inventory system. (Keep in mind that a latency of 4-10 hours is expected). We are not able to look into the past to see previous states of the inventory system.
