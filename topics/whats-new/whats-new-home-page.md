---
# required metadata
title: What's new or changed in Intelligent Order Management
description: This article points to articles that describe the new and changed features in each release of Intelligent Order Management.
author: johnmichalak
ms.author: johnmichalak
ms.reviewer: johnmichalak
ms.date: 04/12/2024
ms.custom: 
  - bap-template
  - evergreen
ms.topic: whats-new
ms.collection:  #Required; The values for this attribute will be updated over time. For now, leave this value blank.
---

# What's new or changed in Intelligent Order Management

This section contains a table that lists the releases when available. 

| Version | Build number | Description |
|---------|--------------|---------------|
| 1.0.0.6962 | build 1.0.215.0 | This build contains security improvements.  |
| 1.0.0.6940 | build 1.0.202.0 | - Fixed an issue where step failures can create duplicate business events. <br> - Added run history URL for Unified Flows. <br> - Fixed an issue where import of a solution could fail due to shared variables not found in plugin context. |
| 1.0.0.6909 | build 1.0.182.0 | - Allow Backorder SLA to be set up to 365 days. <br> - Dual write with Sales orders now syncs all lines even if one fails.  <br> - Fixed an issue where SendForFulillment was marked as successful even though it failed.  <br> - Remove state updates for business events. Customers are advised to use the State Framework. |
| 1.0.06854 | build 1.0.152.0 | - Removed the UPS Provider.  <br> - PREVIEW: Pause and Resume for Orchestrations.  <br> - Raise aggregate event for sales order fulfillment in process when all lines are in fulfillment. |


[!INCLUDE[footer-include](../includes/footer-banner.md)]
