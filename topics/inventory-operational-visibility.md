---
author: sumanic
description: This topic describes Inventory Operations Visibility query screen in Microsoft Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 10/14/2022
ms.topic: how-to
ms.author: sumanic
title: Inventory operations visibility

---

# Inventory operations visibility

Inventory visibility is a key enablement of Dynamics 365 Intelligent Order Management that enables end to end visibility of inventory across your organizational units. Having full visibility enables preparation for the unexpected and helps make better business decisions.

Three primary benefits can be attained with a proper operational visibility:

- Optimize stock levels.
- Reduce Supply chain costs.
- Improved decision making.

In order to give customers these benefits,we are introducing close to real-time inventory query screens that can be used across different areas of Dynamics 365 Intelligent Order Management.This will have information updated from your source system as a fundamental tenant for heterogeneous supply chain systems.

> [!NOTE]
> This is an intelligent query screen and automatically detects an enabled instance of Dynamics 365. Accordingly this query screen will leverage Dynamics 365 Finance and Operations inventory for querying and highlight the availability for the same.
In case **Available to Promise** is enabled, then this query screen will also allow to query incoming availability from **Dynamics 365 Finance and Operations**.

![Inventory Operational Visibility.](media/IVQuery.png)

## How to access the Inventory query screen?

This query screen can be accessed from multiple areas for different scenarios. Below are some usecases:

### Use case 1: An Inventory planner wants operational visibility

1. Go to the **sitemap** under **Demand planning** and select **Operational visibility**.
2. The left half of the screen is the query screen.
3. The right side of the screen displays the result.
4. The **Organization ID** will be auto populated with dataverse organization id when using Intelligent Order Management without Supply chain management and **Company Id** needs to entered in **Organization ID** when D365 Finance and Operations dual write is enabled.
5. Enter the below mandatory fields:

    5.1 **Site ID**
    
    5.2 **Location ID**. Please use the **Warehouse ID** here associated with a store or warehouse.

6. Enter the **Product ID** you want to search for. Please use the **ID** associated with product name in product master.
7. Check the **Query ATP** selection in case you have uploaded your demand and supply view using [Dynamics 365 Inventory Services.](/dynamics365/supply-chain/inventory/inventory-visibility-available-to-promise)
8. Select **Query**.
9. This will display the query results on the right side of the panel.
10. You could also choose to hide the query section and just display the results. For this on the top right of the screen, change the selection from **Combo** to **Hide search criteria**.
11. A sample example of this query run looks as below:

![Query Results.](media/QueryResult.png)
  
### Use case 2 : A customer representative wants to view availability from Products.

1. Go to the **sitemap** under **Demand planning** and select **Products**.
2. Select the product and select **View**.
3. On the upper menu bar, select **View Availability**.
4. This will open the same query screen with the **Organization ID** and **Product ID** auto populated. **Organization ID** will be auto populated with dataverse organization id for Dynamics 365 Intelligent Order Management and **Company Id** needs to be entered in **Organization ID** when dual write is enabled with Dynamics 365 Finance and Operations.
5. Enter the below mandatory fileds:
    1. **Site ID**   
    1. **Location ID**. Please use the **Warehouse ID** here associated with a store or warehouse.
6. Check the **Query ATP** selection in case you have uploaded your demand and supply view using [Dynamics 365 Inventory Services.](/dynamics365/supply-chain/inventory/inventory-visibility-available-to-promise)
7. Select **Query**.
8. This will display the query results on the right side of the panel.
9. You could also choose to hide the query section and just display the results. For this on the top right of the screen, change the selection from **Combo** to **Hide search criteria**.

### Use case 3 : A customer representative wants to view availability from Order Products screen.

1. Go to the **sitemap** under **Orders** and select **Sales Orders**.
2. Select  **New** to create a new order.
3. Enter the order details and **Save** the order header.
4. Go to the **Order \> Order Products** section and select **+ Add Products**.
    ![OrderProducts.](media/QuickForm.png)
6. This will open a quick form on the right side of the screen.
7. You will now be able to see a ![View Avail.](media/CheckAvail.png) button.
8. Enter the product. This could be an **Existing Product** or **Write-in Product**.
9. Add the **Unit**.
10. Select **Check Availability**. This will open the query screen.
    ![Query Autofill.](media/Autofill.png)
11. The **Organization ID** and **Product ID** will be auto populated. **Organizaion ID** will be auto populated with dataverse organization id for IOM and **Company Id** needs to be entered in **Organization ID** when dual write is enabled with Dynamics 365 Finance and Operations.
12. In case you have entered the **Fulfillment Source** as well, then the query screen will have the **Location ID** populated as well.
13. Enter the **Site ID**.
14. Check the **Query ATP** selection in case you have uploaded your demand and supply view using [Dynamics 365 Inventory Services.](/dynamics365/supply-chain/inventory/inventory-visibility-available-to-promise)
15. Select **Query**.
16. This will display the query results on the right side of the panel.
17. You could also choose to hide the query section and just display the results. For this on the top right of the screen, change the selection from **Combo** to **Hide search criteria**.
18. Review the availability. **Save** the **Order Products** form.

Query results are displayed based on the physical and calculated measures tha is setup as part of inventory setup configuration. For more information regarding the setup, see [Intelligent Order Management](/dynamics365/intelligent-order-management/)
