---
author: raybennett-msft
description: This article details the release notes for intelligent order management.
ms.date: 04/30/2024
ms.custom: 
  - bap-template
ms.topic: conceptual
ms.author: bennettray

title: Release Notes

---

# Release Notes

[!include [banner](includes/banner.md)]

This page provides release notes of current and previous builds of Intelligent Order Management.

1.0.0.6962 (build 1.0.215.0)
 * This build contains security improvements.

1.0.0.6940 (build 1.0.202.0)
 * Fixed an issue where step failures can create duplicate business events
 * Added run history URL for Unified Flows
 * Fixed an issue where import of a solution could fail due to shared variables not found in plugin context

1.0.0.6909 (build 1.0.182.0)
 * Allow Backorder SLA to be set up to 365 days
 * Dual write with Sales orders now syncs all lines even if one fails
 * Fixed an issue where SendForFulillment was marked as successful even though it failed
 * Remove state updates for business events. Customers are advised to use the State Framework

1.0.06854 (build 1.0.152.0)
 * Removed the UPS Provider
 * PREVIEW: Pause and Resume for Orchestrations
 * Raise aggregate event for sales order fulfillment in process when all lines are in fulfillment