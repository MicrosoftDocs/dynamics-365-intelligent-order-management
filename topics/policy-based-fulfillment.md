---
author: anvenkat
ms.author: anvenkat
title: Policy-based fulfillment
description: This article provides an overview of the settings and pre-requisites to consider when setting up policy-based fulfillment within Microsoft Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 02/24/2023
ms.topic: how-to
ms.custom: bap-template

---

# Policy-based fulfillment

This article provides an overview of the settings and pre-requisites to consider when setting up policy-based fulfillment within Microsoft Dynamics 365 Intelligent Order Management.

Policy-based fulfillment describes using execution policy for setting the fulfillment source at line level. Businesses can choose this option when the rules are simple, or number of sources are limited. 

## General settings for policy-based fulfillment

To configure your preferences for policy-based fulfillment, follow these steps.

1. Go to **Settings** > **General Settings** > **Order handling preferences** >**Manage**.
1. Under **Fulfillment process policy**, select one of the following options:
   - **Inventory On hand check** - This option checks inventory availability on the selected fulfillment source, but does not create a fulfillment order.
             Suggestion: Use the **Send sales order to fulfillment** action if using this option to send the whole sales order to Microsoft Dynamics 365 Supply Chain Management. Note, you need to assign both a fulfillment source and a shipping warehouse using this execution policy.
   - **Fulfillment order creation - Fulfillment order creation without inventory check** - This option allows creation of a fulfillment order without an availability check. This option is best suited for when fulfillment happens with ERP and the fulfillment order needs to be created to record the status of the fulfillment from ERP.
   - **Inventory check and fulfillment order creation** - This option is best suited if sales order needs to be sent to warehouse management or Enterprise resource planning applications post fulfillment determination. 
             Suggestion: Use the **Send sales order liens to billing** action if using this option to send all sales order lines that have fulfillment order to Supply Chain Management.

Action type used for policy-based fulfillment is **Send fulfillment process request** for all of the above selections.

## Sample flow for policy-based fulfillment

![Sample flow for policy-based fulfillment.](media/flow-with-policy-based-source-assignment.png)


