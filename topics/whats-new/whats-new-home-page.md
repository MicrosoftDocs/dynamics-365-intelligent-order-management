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

---

# What's new or changed in Intelligent Order Management

This section contains a table that lists the releases when available. 

| Version | Description | Date |
|---------|-------------|-------|
|            | - Improved dual write error handling by surfacing the dw error at orderline entity within IOM <br> - improved batch handling of DW order lines to not fail the whole batch if some lines have failed. <br> - Allow multiple provider instances with one active instance. <br> - Update orchestrate logic to fix list page orchestrate button for manual bulk orchestration. <br> - Filter out orders that dont have any order lines from dual write to Finance and operation. | Dec'24 |
| 1.0.0.6962 | This build contains security improvements.  | April'24 |
| 1.0.0.6940 | - Fixed an issue where step failures can create duplicate business events. <br> - Added run history URL for Unified Flows. <br> - Fixed an issue where import of a solution could fail due to shared variables not found in plugin context. | March'24 |
| 1.0.0.6909 | - Allow Backorder SLA to be set up to 365 days. <br> - Dual-write with Sales orders now syncs all lines even if one fails.  <br> - Fixed an issue where SendForFulillment was marked as successful even though it failed.  <br> - Remove state updates for business events. Customers are advised to use the State Framework. | Jan'24 |
| 1.0.0.6854 | - Removed the UPS Provider.  <br> - PREVIEW: Pause and Resume for Orchestrations.  <br> - Raise aggregate event for sales order fulfillment in process when all lines are in fulfillment. | Dec'23 |
| 1.0.0.6738 | - Enabled Bing maps on sales order. <br> -Enabled Purchase Order orchestration.<br> - Enabled a new action to create purchase order from sales order. <br> - Enabled Navisphere provider and have connected to their public APIs for create order, create order with quote and rating request. <br> - New working calendar control that allows support for adding replenishment schedule on a modern UX framework. <br> - Preview DOM API to support BOPIS (Buy online pickup in store) and BOSS (Buy online ship to store) | Sep '23 |
| 1.0.0.6656 | - Sales order form updates made for better visibility of order to fulfillments in the same page reducing number of clicks.  <br> -Support Preview DOM API Payload Verison 2 to support EDDs as a list for each Rate <br> - DOM API Pick the closer fulfillment source when two fulfillment sources have the same ATP date <br> - Security updates and bug fixes | July'23
| 1.0.0.6606 | - Enabled entities for copilot search <br> - Security updates and bug fixes | June'23



[!INCLUDE[footer-include](../includes/footer-banner.md)]
