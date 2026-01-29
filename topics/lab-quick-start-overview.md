---
author: josaw1
description: Learn about the quick start guide for Microsoft Dynamics 365 Intelligent Order Management.
ms.date: 01/28/2026
ms.custom: 
  - bap-template
ms.topic: overview
ms.author: anvenkat
title: Quick start overview
---

# Quick start lab overview

[!include [banner](includes/banner.md)]

This article provides an overview of the quick start lab for Microsoft Dynamics 365 Intelligent Order Management.

In this quick start lab, you learn how to:

- Create providers.
- Set up platform connection references.
- Set up Power Automate connections.
- Onboard providers.
- Set up policies.
- Set up order orchestration flows.
- Set up internal and external ID mappings.
- Test the end-to-end order orchestration at runtime.

## Lab scenarios  

The quick start lab includes the following scenarios.

- Order comes into IOM as email attachment.
- Validate order header to make sure ship to country/region is US.
- Validate order line to make sure quantity is more than 1.
- Route order based on quantity.
  - If quantity >= 100, send to Seattle store.
  - If quantity < 100, send to Chicago store.
- If order is routed to Seattle store, emails with fulfillment order attached are sent.
- If order is routed to Chicago store, requests with fulfillment order as payload are sent to RequestBin.

## Lab business components

The quickstart uses the following business components.

- Order capturing endpoint: Email
- Order fulfillment endpoints:
  - Orders fulfilled from Seattle: Email
  - Orders fulfilled from Chicago: Request Bin
- Order orchestration flow and central visibility: Dynamics 365 Intelligent Order Management app

## Lab flows

The quickstart demonstrates the following flows.

### Nominal business flow

The following illustration shows a nominal business flow in Intelligent Order Management.

:::image type="content" source="media/lab_flow_1.png" alt-text="Screenshot of the nominal business flow in Intelligent Order Management.":::

### Exception flow (order header validation failed)

The following illustration shows an nominal exception flow caused by an order header validation failure in Intelligent Order Management.

:::image type="content" source="media/lab_flow_2.png" alt-text="Screenshot of the exception flow caused by order header validation failure in Intelligent Order Management.":::

### Exception flow (order line validation failed)

The following illustration shows a nominal exception flow caused by an order line validation failure in Intelligent Order Management.

:::image type="content" source="media/lab_flow_3.png" alt-text="Screenshot of the exception flow caused by order line validation failure in Intelligent Order Management.":::

Next quick start lab step: [Create and configure connections](lab-create-configure-connections.md)
