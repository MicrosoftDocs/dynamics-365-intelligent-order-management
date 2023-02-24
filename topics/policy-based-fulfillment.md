---
author: anvenkat
description: This article describes policy based fulfillment within Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 02/24/2023
ms.topic: how-to
ms.author: anvenkat
title: Policy based fulfillment

---

# Policy based fulfillment

This topic describes overview of the settings and pre-requisites to consider when setting up policy based fulfillment. 
Policy based fulfillment describes using execution policy for setting the fulfillment source at line level. Businesses can choose this option when the rules are simple or number of sources are limited. 

## General settings for policy based fulfillment

Following options are available to configure your preferences for the polica based fulfillment.

1. Go to **Settings** > **General Settings** > **Order handling preferences** >**Manage**
1. Under **Fulfillment process policy** you can select one of the settings:
   - **Inventory On hand check** - This option will check inventory availability on the fulfillment source selected but does not create fulfillment order.
             Suggestion: Use action **Send sales order to fulfillment** if using this option to send the whole sales order to Dynamics 365 supply chain management. Please note you will need to assign both fulfillment source and shipping warehouse using execution policy.
   - **Fulfillment order creation - Fulfillment order creation without inventory check** - This option allows creation of fulfillment order without availability check. This is best suited for when fulfillment happens with ERP and the fulfillment order needs to be created to record the status of the fulfillment from ERP.
   - **Inventory check and fulfillment order creation** - This option is best suited if sales order needs to be sent to warehouse management or Enterprise resource planning applications post fulfillment determination. 
             Suggestion: Use action **Send sales order liens to billing** if using this option to send all sales order lines that have fulfillment order to Dynamics 365 supply chain management.

Action type used for policy based fulfillment is **Send fulfillment process request** for all of the above selections.

## Sample flow for policy based fulfillment

![Sample flow for policy based fulfillment.](media/flow-with-policy-based-source-assignment.png)


