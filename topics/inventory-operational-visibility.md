---
author: sumanic
description: This article describes inventory operations visibility in Microsoft Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 10/18/2022
ms.topic: how-to
ms.author: sumanic
title: Inventory operations visibility

---

# Inventory operations visibility

[!include [banner](includes/banner.md)]

This article describes inventory operations visibility in Microsoft Dynamics 365 Intelligent Order Management.

Inventory operations visibility is a key feature of Intelligent Order Management that enables end-to-end visibility of inventory across your organizational units. Having full visibility enables you to prepare for the unexpected and helps you make better business decisions.

Three primary benefits can be attained with inventory operational visibility:

- Optimized stock levels
- Reduced supply chain costs
- Improved decision making

To provide customers with these benefits, Intelligent Order Management has introduced near real-time inventory query screens that can be used across different areas of the application. These inventory query screens are updated with information from your source system, which is a fundamental tenet of heterogeneous supply chain systems.

> [!NOTE]
> Intelligent Order Management query screens are intelligent and can automatically detect an enabled instance of Dynamics 365. Inventory query screen use Dynamics 365 Finance inventory capabilities for querying and highlighting product availability. If available-to-promise inventory capabilities are enabled, then an inventory query screen can also query incoming availability from Dynamics 365 Finance.

![Inventory Operational Visibility](media/IVQuery.png)

## How to access the inventory query screen?

You can access the inventory query screen from multiple areas for different scenarios. The following use cases highlight some of the methods.

### Use case #1: An inventory planner wants operational visibility

1. In the left navigation pane, select **Demand planning \> Operational visibility**. On the **Onhand Query** page that appears, the left half of the screen is for queries and the right side displays the results.
1. The **Organization ID** value will be automatically populated with the Dataverse organization ID when using Intelligent Order Management without Supply Chain Management. You must enter the **Company ID** value in the **Organization ID** field when dual-write is enabled.
1. Enter value for the following mandatory fields:
   1. **Site ID** 
   1. **Location ID**. Use the **Warehouse ID** associated with a store or warehouse.
1. For **Product ID**, enter the product ID you want to search for. Use the ID associated with product name in the product master.
1. If you've uploaded your demand and supply view using [Dynamics 365 Inventory Services.](/dynamics365/supply-chain/inventory/inventory-visibility-available-to-promise), select the **Query ATP** checkbox. 
1. Select **Query**. Query results appear on the right side of the page.
1. To hide the query section of the screen and just display the results, on the top right of the screen, select **Combo \> Hide search criteria**.

The following screenshot shows an example query result.

![Query Results](media/QueryResult.png)
  
### Use case #2: A customer representative wants to view availability from the Products screen.

1. In the left navigation pane, select **Demand planning \> Products**.
2. Select a product, and then select **View**.
3. On the upper menu bar, select **View Availability**.
4. This will open the same query screen with the **Organization ID** and **Product ID** auto populated. **Organization ID** will be auto populated with Dataverse organization id for Dynamics 365 Intelligent Order Management and **Company ID** must be entered in **Organization ID** when dual-write is enabled with Dynamics 365 Finance and Operations.
5. Enter the below mandatory fields:
    1. **Site ID**   
    1. **Location ID**. Please use the **Warehouse ID** here associated with a store or warehouse.
6. Check the **Query ATP** selection in case you've uploaded your demand and supply view using [Dynamics 365 Inventory Services.](/dynamics365/supply-chain/inventory/inventory-visibility-available-to-promise)
7. Select **Query**.
8. This will display the query results on the right side of the panel.
9. You could also choose to hide the query section and just display the results. For this on the top right of the screen, change the selection from **Combo** to **Hide search criteria**.

### Use case #3: A customer representative wants to view availability from Order Products screen.

1. Go to the **sitemap** under **Orders** and select **Sales Orders**.
2. Select  **New** to create a new order.
3. Enter the order details and **Save** the order header.
4. Go to the **Order \> Order Products** section and select **+ Add Products**.
    ![OrderProducts.](media/QuickForm.png)
6. This will open a quick form on the right side of the screen.
7. You'll now be able to see a ![View Avail.](media/CheckAvail.png) button.
8. Enter the product. This could be an **Existing Product** or **Write-in Product**.
9. Add the **Unit**.
10. Select **Check Availability**. This will open the query screen.
    ![Query Autofill.](media/Autofill.png)
11. The **Organization ID** and **Product ID** will be auto populated. **Organization ID** will be autopopulated with Dataverse organization id for IOM and **Company ID** must be entered in **Organization ID** when dual-write is enabled with Dynamics 365 Finance and Operations.
12. In case you've entered the **Fulfillment Source** as well, then the query screen will have the **Location ID** populated as well.
13. Enter the **Site ID**.
14. Check the **Query ATP** selection in case you've uploaded your demand and supply view using [Dynamics 365 Inventory Services.](/dynamics365/supply-chain/inventory/inventory-visibility-available-to-promise)
15. Select **Query**.
16. This will display the query results on the right side of the panel.
17. You could also choose to hide the query section and just display the results. For this on the top right of the screen, change the selection from **Combo** to **Hide search criteria**.
18. Review the availability. **Save** the **Order Products** form.

Query results are displayed based on the physical and calculated measures that are configured as part of inventory configuration.
