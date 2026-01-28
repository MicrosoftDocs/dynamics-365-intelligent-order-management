---
title: Fulfillment entity relationships in Intelligent Order Management
author: anvenkat
description: Learn about entity relationships for out-of-box entities in Microsoft Dynamics 363 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 01/28/2026
ms.custom: 
  - bap-template
ms.topic: overview
ms.author: anvenkat
---

# Fulfillment entity relationships in Intelligent Order Management

[!include [banner](includes/banner.md)]

This article explains entity relationships for out-of-box entities in Microsoft Dynamics 363 Intelligent Order Management.

In Dynamics 365 Intelligent Order Management, order fulfillment is modeled through a set of interconnected entities that represent the customer order, its line items, fulfillment instructions, and tracking updates. These relationships enable traceability, support partial shipments, and provide visibility into fulfillment progress across systems.

The following table outlines the key entities involved in the fulfillment lifecycle, along with their relationship cardinality and foreign key mappings.

## Entity relationship table

| Parent entity ("One")         | Child entity ("Many")           | Foreign key in child entity           | Cardinality | Description                                                                 |
|-------------------------------|----------------------------------|----------------------------------------|-------------|-----------------------------------------------------------------------------|
| `Order`                       | `Order Product`                  | `salesorderid`                         | 1:N         | One order can contain multiple products.                                   |
| `Order`                       | `Fulfillment Order`              | `salesorderid`                         | 1:N         | One order can generate multiple fulfillment orders.                         |
| `Order Product`               | `Fulfillment Order Product`      | `orderproductid`                       | 1:N         | Each order product can be fulfilled in multiple ways.                       |
| `Fulfillment Order`          | `Fulfillment Order Product`      | `fulfillmentorderid`                   | 1:N         | One fulfillment order can include multiple fulfillment order products.      |
| `Fulfillment Order`          | `Fulfillment Tracking`           | `fulfillmentorderid`                   | 1:N         | One fulfillment order can have multiple tracking records.                   |
| `Fulfillment Tracking`       | `Fulfillment Tracking Line`      | `fulfillmenttrackingid`                | 1:N         | One tracking header can have multiple line-level updates.                   |
| `Fulfillment Order Product`  | `Fulfillment Tracking Line`      | `fulfillmentorderproductid`            | 1:N         | Each fulfillment order product can be tracked across multiple tracking lines. |

This schema supports extensible fulfillment workflows that enable systems to monitor progress, capture events, and reconcile fulfillment status back to the original order and product lines.
