---
title: Shipping rate factor table overview
description: This article explains the Shipping rate factor table.
ms.author: anvenkat
author: anush6121
ms.date: 01/28/2026
ms.custom: 
  - bap-template
ms.topic: how-to
---

# Shipping rate factor table overview

[!include [banner](includes/banner.md)]

As part of the April 2023 release, the Shipping rate factor table is now available in Microsoft Dynamics 365 Intelligent Order Management. This table lets you configure rate markups, static rates, and increments, based on weight thresholds for different carrier service levels. The Shipping rate factor table represents a fallback option when either the carrier rate API fails or the dynamic rate APIs aren't available for a carrier.

## Fields in the Shipping rate factor table

The following table describes the fields in the Shipping rate factor table.

| Field | Description |
| ----- | ----------- |
| Name | The name or description of the carrier service. |
| Fulfillment source type | The **Fulfillment source type** value in the fulfillment settings. Use this field when, for example, a store and a distribution center have different carrier services that are offered at different rates. |
| Address type | The destination address type (for example, **Business** or **Residence**). |
| Rate factor | A markup or markdown of the calculated rate from the carrier API, if applicable. |
| Free shipping | A flag that indicates whether the service is applicable for free shipping. |
| Fallback weight threshold | The weight threshold that a static rate is defined for. |
| Fallback rate | The static rate until the weight threshold is met. |
| Fallback increment rate factor | The rate factor that's applied for incremental weight over the threshold. For example, the weight threshold is 5 pounds, the static rate is $8, the increment rate factor is 0.75, and the total weight of the order is 10 pounds. In this case, the rate is calculated as 8 + (0.75 &times; 5) = 11.75. |

## Using the Shipping rate factor table in the Intelligent Order Management DOM API

The Intelligent Order Management Distributed Order Management (DOM) API calls the FedEx rate API to calculate the shipping rate. If the shipping rate can't be calculated because of an issue with the API, a fallback rate is calculated by using the **Fallback weight threshold** and **Fallback increment rate factor** values that are defined for each service level in the table. If the carrier API returns a valid rate, a markup or markdown percentage is applied by using the **Rate factor** percentage that's maintained in the table.
