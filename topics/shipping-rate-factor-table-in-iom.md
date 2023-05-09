---
title: Shipping rate factor table overview
description: This article explains the Shipping rate factor table.
ms.author: anvenkat
author: anush6121
ms.date: 05/06/2023
ms.topic: how-to
ms.custom: bap-template
---

# Shipping rate factor table overview

[!include [banner](includes/banner.md)]

As part of April 2023 release, the Shipping rate factor table is now available within Microsoft Dynamics 365 Intelligent Order Management. This table allows you to configure rate mark ups, static rates, and increments based on weight thresholds for different carrier service levels. The rate factor table represents a fallback option when either the carrier rate API fails, or when the dynamic rate APIs aren't available for a carrier.

## Description of fields within shipping rate factor table

The following table describes each of the fields in the shipping rate factor table.

| Field | Description |
| ----- | ----------- |
| **Name** | The name or description of the carrier service. |
| **Fulfillment source type** | The **Fulfillment source type** in the **Fulfillment settings**. For example, use this field when a store and distribution center has different carrier services that are offered with different rates. |
| **Address type** | The destination address type. For example, **Business** or **Residence**. |
| **Rate factor** | A mark up or mark down of the calculated rate from the carrier API, if applicable. |
| **Free shipping** | A flag that indicates if the service is applicable for free shipping. |
| **Fallback weight threshold** | The weight threshold for which a static rate is defined. |
| **Fallback rate** | The static rate until weight threshold is met. |
| **Fallback increment rate factor** | The rate factor that is applied for incremental weight over threshold. For example, if the weight threshold is 5 lbs, the static rate is $8, the increment rate factor is 0.75, and if the total weight of the order is 10 lbs, the rate is calculated as 8 + (0.75 \* 5) = 11.75. |

## Using the shipping rate factor table in Intelligent Order Management DOM(Distributed Order Management) API.

Intelligent Order Management DOM API calls the FedEx rate API to calculate the shipping rate. If the shipping rate couldn't be calculated for some reason due to an issue with the API, a fallback rate is calculate using the **fallback weight threshold** and the **fallback increment rate factor** that is defined for each service level in the table. If the carrier API returns a valid rate, a mark up or mark down percentage is applied using the **rate factor** percentage that is maintained in the table.





