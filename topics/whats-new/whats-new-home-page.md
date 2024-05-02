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

Wondering about upcoming and recently released capabilities in Intelligent Order Management? [Check out the release planner site](https://experience.dynamics.com/releaseplans/?app=Marketing). We've captured all the details, end to end, top to bottom, which you can use for planning.  

See the release plans for what's coming. Choose the following link to learn about the latest versions of this app.

- [2023 release wave 1](/dynamics365/release-plan/2023wave1/supply-chain-center/microsoft-supply-chain-center/dynamics-365-intelligent-order-management)  

## Releases of Dynamics 365 Intelligent Order Management

This section will contain a table that lists the releases when available. 

| Version | Build number | Descriptiop |
|---------|--------------|---------------|
| 1.0.0.6962 | build 1.0.215.0 | This build contains security improvements.  |
| 1.0.0.6940 | build 1.0.202.0 | -Fixed an issue where step failures can create duplicate business events. <br> - Added run history URL for Unified Flows. <br> - Fixed an issue where import of a solution could fail due to shared variables not found in plugin context. |
| 1.0.0.6909 | build 1.0.182.0 | - Allow Backorder SLA to be set up to 365 days. <br> - Dual write with Sales orders now syncs all lines even if one fails.  <br> - Fixed an issue where SendForFulillment was marked as successful even though it failed.  <br> - Remove state updates for business events. Customers are advised to use the State Framework. |
| 1.0.06854 | build 1.0.152.0 | - Removed the UPS Provider.  <br> - PREVIEW: Pause and Resume for Orchestrations.  <br> - Raise aggregate event for sales order fulfillment in process when all lines are in fulfillment. |


[!INCLUDE[footer-include](../includes/footer-banner.md)]
