---
# required metadata
title: What's new or changed in Intelligent Order Management
description: This article points to articles that describe the new and changed features in each release of Intelligent Order Management.
author: johnmichalak
ms.author: johnmichalak
ms.reviewer: johnmichalak
ms.date: 05/27/2025
ms.update-cycle: 1095-days
ms.custom: 
  - bap-template
  - evergreen
ms.topic: whats-new

---

# What's new or changed in Intelligent Order Management

This section contains a table that lists the releases when available. 

| Version | Description | Date |
|---------|-------------|------|
| 1.1.1.744 | <ul><li> Improve resilience of orchestration by better handling of policy evaluation failures. <li> Introduce reprocess capability from sales order listings page. <li> Improve resilience of FinOps provider for Release to Fulfillment action when UpdateMultiple call fails. <li>Other performance and security improvements. |July 2025 |
| 1.1.1.630 | <ul><li>Operational visibility query bug fixes to handle dimension based lookup. <li> Fix split order child flow publishing. | May 2025 | 
| 1.1.1.541 | <ul><li>Update logic instance and workflow upsert to support ALM.<li>Fix issues related to inbound provider errors. | April 2025 |
| 1.1.1.461 | <ul><li>Allow you to turn off the state framework completely. <li>Add business rule to show the provider activation error logs in failed provider instance activation page.<li>Enable changing states associated with the custom business events in configuration.| March 2025 |
| 1.1.1.449 | <ul><li>Allow configuration for Send to finance and operations step to be successful even when one or more order lines fail to sync to finance and operations apps. | Feb 2025 |
| 1.1.1.431 | <ul><li>Improve Dual-write error handling by surfacing the dual-write error at the orderline entity in Microsoft Dynamics 365 Intelligent Order Management.</li><li>Improve batch handling of dual-write order lines, so that the failure of some lines doesn't cause the whole batch to fail.</li><li>Allow multiple provider instances with one active instance.</li><li>Update the orchestration logic to fix the **Orchestrate** button for manual bulk orchestration on the list page.</li><li>Filter out orders that don't have any order lines from dual-write to finance and operations apps.</li></ul> | December 2024 |
| 1.0.0.6962 | This build contains security improvements. | April 2024 |
| 1.0.0.6940 | <ul><li>Fix an issue where step failures can create duplicate business events.</li><li>Add a run history URL for unified flows.</li><li>Fix an issue where import of a solution can fail because shared variables aren't found in the plugin context.</li></ul> | March 2024 |
| 1.0.0.6909 | <ul><li>Enable the backorder service level agreement (SLA) to be set to up to 365 days.</li><li>Dual-write with sales orders now syncs all lines, even if one fails.</li><li>Fix an issue where SendForFulillment is marked as successful even though it failed.</li><li>Remove state updates for business events. We recommend that customers use the State Framework.</li></ul> | January 2024 |
| 1.0.0.6854 | <ul><li>Remove the UPS provider.</li><li>PREVIEW: Pause and resume for orchestrations.</li><li>Raise an aggregate event for in-process sales order fulfillment when all lines are in fulfillment.</li></ul> | December 2023 |
| 1.0.0.6738 | <ul><li>Enable Bing maps on sales orders.</li><li>Enable purchase order orchestration.</li><li>Enable a new action for creating purchase orders from sales orders.</li><li>Enable the Navisphere provider, and connect to its public APIs for create order, create order with quote, and rating requests.</li><li>A new working calendar control to support the addition of replenishment schedules in a modern user experience (UX) framework.</li><li>Preview DOM API to support "buy online, pickup in store" (BOPIS) and "buy online, ship to store" (BOSS) scenarios.</li></ul> | September 2023 |
| 1.0.0.6656 | <ul><li>Sales order form updates for better visibility of order to fulfillments on the same page. As a result, the number of taps or clicks that are required is reduced.</li><li>Support for Preview DOM API Payload Version 2 to support EDDs as a list for each rate.</li><li>DOM API Pick the closer fulfillment source when two fulfillment sources have the same ATP date.</li><li>Security updates and bug fixes.</li></ul> | July 2023 |
| 1.0.0.6606 | <ul><li>Enable entities for Copilot search.</li><li>Security updates and bug fixes.</li></ul> | June 2023 |

[!INCLUDE[footer-include](../includes/footer-banner.md)]
