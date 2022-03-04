---
author: sumanic
description: This topic explains how to set up the Microsoft Dynamics 365 Finance + Operations (on-premises) provider in Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 03/03/2022
ms.topic: how-to
ms.author: sumanic
title: Set up the Dynamics 365 Finance + Operations provider

---

# Set up the Dynamics 365 Finance + Operations provider

[!include [banner](includes/banner.md)]

This topic explains how to set up the Microsoft Dynamics 365 Finance + Operations (on-premises) provider in Dynamics 365 Intelligent Order Management.

Finance + Operations helps businesses manage their global financial systems, operational business processes, and streamlined supply chains, so that business decision makers can make fast, informed decisions. The Finance + Operations provider enables Intelligent Order Management to write orders to Finance + Operations or consume orders from Finance + Operations. It also performs other supply chain actions.

For more information about Finance + Operations, see the [Dynamics 365 Finance](https://dynamics.microsoft.com/finance/overview/) website.

## Prerequisites

This setup will enable order synchronization between Intelligent Order Management and Finance + Operations, in both directions.

- Dual-write must be set up in your Finance + Operations instance. For information about how to set up dual-write, see [Guidance for dual-write setup](/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/connection-setup).
- Intelligent Order Management must be installed in the same Dataverse instance that Finance + Operations is installed in.
- Mappings that are associated with dual-write must be enabled in Intelligent Order Management.

    To enable mappings that are associated with dual-write, follow these steps.

    1. In Finance + Operations, go to **Workspaces \> Data management \> Dual-write**.
    1. Set the dual-write mappings to enable synchronization from Intelligent Order Management to Finance + Operations. Order mapping filters must be added to delay order synchronization to Finance + Operations when an order isn't ready to be synced.

        1. On the dual-write page, select **CDS sales order headers (saleorders)**.
        1. On the **CDS sales order headers (saleorders)** page, select the **Filter** button (funnel symbol) next to **Microsoft Dataverse.order** to edit the query.
        1. In the **Edit query** dialog box, enter the following query string:

            `msdyn_ordertype eq 192350000 and _msdyn_company_value ne null and msdyn_isreadytosync eq true and statuscode ne 100003`

        1. Select **Accept**.
        1. On the dual-write page, select **CDS sales order lines (saleorderdetails)**.
        1. On the **CDS sales order lines (saleorderdetails)** page, select the **Filter** button (funnel symbol) next to **Microsoft Dataverse.order** to edit the query.
        1. In the **Edit query** dialog box, enter the following query string:

            `msdyn_company_value ne null and _msdyn_shippingsite_value ne null and _msdyn_shippingwarehouse_value ne null and msdyn_isreadytosync eq true and msdyn_statuscode ne 192350001`

        1. Select **Accept**.
        1. On both the **CDS sales order headers (saleorders)** page and the **CDS sales order lines (saleorderdetails)** page, edit the **msdyn\_isreadytosync** entity fields, and set the following values:

            - **Sync direction:** Finance and Operations apps to Dataverse
            - **Transform type:** Default
            - **Default value:** true

- Order synchronization from Intelligent Order Management to Finance + Operations requires that some key parameters be sent in the order:

    - **Sales Order** policy parameters:

        - Company
        - Invoice Customer

    - **Sales Order Product** policy parameters:

        - Company
        - Shipping Site
        - Shipping Warehouse

    These parameter values can be passed through policy rule definitions in Intelligent Order Management, as shown in the following example for a sales order policy.

    ![Dual-write Sales Order entity mapping.](media/SOHeaderPolicy.png)

    For more information, see [Policies and rules](policies-rules.md).

## Set up the provider

To set up the Finance + Operations provider, follow these steps.

1. In Intelligent Order Management, go to **Providers \> Catalog**.
1. On the **Microsoft Finance and Operations apps** tile, select **Add Provider**.
1. On the **Terms and Conditions** page, select **Create**.
1. In the **Connections** section, you must set up one connection: **Microsoft Finance and Operations Dataverse (current environment) Connection**.

    1. Add the Dataverse connection.
    1. Select **Save**.
    1. Select **Activate** to activate the connection.
    1. Select **Save and close**.

1. Select **Save**.
1. Select **Activate** to activate the provider.
1. Select **Save and close**.
1. Go to **Providers \> Installed**, and verify that the provider that you set up is listed and has a status of **Activated**.

> [!NOTE]
> Only orders that have been confirmed in Finance + Operations can be synced to Intelligent Order Management. To help ensure that an order from Finance + Operations will be successfully synced to Intelligent Order Management, first verify that the order is confirmed in Finance + Operations.

To send an order from Intelligent Order Management to Finance + Operations, you must call the Finance + Operations provider action in the order orchestration flow, regardless of whether the order is sent to fulfillment or accounting.

The following illustration shows an example of an order processing orchestration flow that has a custom **Send Order to FinOps for Fulfillment** action.

![Orchestration flow with a custom Send Order to FinOps for Fulfillment action.](media/F&OFlow.png)
