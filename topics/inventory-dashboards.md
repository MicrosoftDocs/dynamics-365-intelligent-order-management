---
author: josaw1
description: This topic provides an overview of inventory-related dashboards in Dynamics 365 Intelligent Order Management.
ms.date: 05/28/2022
ms.topic: conceptual
ms.author: josaw

title: Inventory dashboards
---


# Inventory dashboards

[!include [banner](includes/banner.md)]

Inventory management is one of the most expensive pieces in an order management process. Having visibility into what your business has in stock vs the demand for that item and other relevant KPIs can provide a lot of value and savings. This is what Intelligent Order Management's dashboards will achieve for you. 

In this article let us understand the various KPIs and graphs described in the dashboard.

## Prerequisites and  setup
Please follow these steps to view inventory dashboards on an Intelligent Order Management org:
1. Please ensure that the org's build version is 1.0.0.4354 or above.
1. These dashboards can only light up with useful information if the business is using Intelligent Order Management with Inventory Visibility Service, and has it configured to work.
1. In your org, go to the area switcher on the bottom of the left navigation panel, and switch to *Configurations*.
1. From here, go to the *Index and reservation* section under *Inventory visibility*.
1. Go to the *Feature management* tab on the far right.
1. Here enable the xx toggle. Doing this will ensure that data is flowing from Inventory Visibility Service, into Intelligent Order Management, for consumption by this dashboard.

![Screenshot of inventory dashboard.](../media/InventoryDashboard.png)

1. Finally, the Power BI insights need to be enabled. To do this, go to Power BI Insights on the same left navigation panel. Click on *Manage*, set the status here to *Enabled*, then *Save & Close* on the ribbon.

## Visualizations
The following sections detail the KPIs and graphs that describe inventory information of the business using Intelligent Order Management. 
### Filters

We provide two multi-select filters out-of-box to our customers. One is on product name and the other is on location ID. This is an interactive dashboard, and therefore, when you need to drill down on one or more products/locations, the filters will slice your data to show the KPIs and graphs for the selected products/locations.

##### Product Name
The product names come from the 'Products' (link/ screenshot??) section of IOM. All the products that sales orders can be created for and inventory is recorded for should show up in this section. And this information flows into the Inventory dashboard.

##### Location ID
The location ID comes from the configuration on the inventory dashboard configuration page. (add more here)

### KPIs

1. **Physical available**: This value is the sum of all units that are physically available in the warehouse. It includes the items that are soft reserved. Whenever there is an upload of inventory data to the system, this KPI is updated. Once items get shipped out of the warehouse(s), this KPI is deducted.

1. **Soft reserved**: Once fulfillment optimization happens and the warehouse(s) are determined for sales orders, the respective items in that warehouse are software reserved. When this happens, this KPI is added to. This is to ensure that the same items do not get double booked against two different orders. Once orders are shipped, this KPI is deducted.

1. **Onhand inventory**: This value shows the number of units actually available for consideration when evaluating the warehouse source for sales orders. It is calculated as the $physical Available - soft Reserved$. When a fulfillment optimization runs, this is the inventory value that is considered.

1. **New order line qty**: This value calculates the total number of units of product in demand by looking at all the order lines in new state and adding all its quantity values. 

1. **Returned**: This value shows the number of units of products that have been returned to the warehouse after being sold to end customers.

1. **Return rate**: This value shows the rate of return of units of products that have been returned to the warehouse after being sold to end customers. It is calculated as the total number of $(units Returned/units Sold) * 100 $.

1. **Sell rate**: This value shows the rate of items being sold to end customers. It is calculated as $ [(unitsSold - unitsReturned)/(unitsInStock + unitsSold)] * 100 $.

1. **Out-of-stock**: This value shows the number of units of products that have to be replenished in order to fulfill demand. It is calculated as a summation of $max[(supply - demand), 0]$.

### Graphs

1. **Supply by product name**: This stacked bar chart shows a break down of the inventory supply by product name. It shows the distribution of onhand, soft reserved and returned quantities of the product. Each bar total represents the physical available KPI for the product.

1. **Supply by location ID**: This stacked bar chart shows a break down of the inventory supply by the location. It shows the distribution of onhand, soft reserved and returned quantities of the product. Each bar total represents the physical available KPI for the location.

1. **Return rate by product name**: This bar chart shows the rate of return broken down by product name.
1. **Stockout and near stockout item**: This chart shows the number of units of products that are under stocked or nearing that state as compared to its demand. The bars below the zero line represent the products that are under stocked and the values on the bar represent the number of units of said products that need immediate attention. The bars above the zero line represent the products that are nearing the under stocked state and the values on the bar represent the number of units of said products that will be left once the current demand is satisfied.


### Table

1. **Products**: This is a tabular representation of all the products and their individual KPIs as described in the KPI section above.

## FAQs
1. **How long does it take after setup for the dashboard to light up on the org?**
<br> It can take up to 24 hours after initial set up for the reports to be provisioned. If it takes more than that, please contact Microsoft Support and we will help you out at the earliest.

1. **Is this dashboard real time?**
<br> This dashboard is more suitable to be used as a daily report to assess the health of a business' inventory rather than as a real-time representation of the inventory information. One can expect to see a 4-10 hour latency on the information flowing in. We fully acknowledge that real-time data on inventory is very valuable to businesses and hence in our upcoming October 2022 wave, we are adding a feature to provide real-time information on inventory.

1. **Can I see data for specific products that I care about?**
<br> Yes, we have filters on product name and location ID. They are multi-select filters and can be used to automatically slice up the data being represented in the KPIs and graphs.

1. **Can I sort the data differently than what is made available out-of-box?**
<br> Yes, hover on the graph till you see three small icons appearing on the top right corner of the graph. Click on the three dots (third icon), go to *Sort axis* and choose the option you want.

1. **Can I modify the KPIs that the dashboard provides today?**
<br> Unfortunately, the KPIs we provide today are the only ones available at the moment. Upon doing market research, these were determined to be most useful for majority of businesses, but we are always looking for suggestions. Log an idea here - if we want us to consider adding or modifying our KPIs or graphs.

1. **I'm unsure of how some of these KPIs are being calculated. How do I get more information on that?**
<br> The way these KPIs are being derived is described in the section called *KPIs* above. Additionally, you can also hover on the KPI (not the KPI name) to see a tooltip that describes how the KPI is being calculated.

1. **Can I look for historical information of the inventory?**
<br> All the data being displayed in this dashboard is a current representation of the inventory system. (Keep in mind that a latency of 4-10 hours is expected). We are not able to look into the past to see previous states of the inventory system.
