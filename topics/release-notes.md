---
title: What's new or changed for version 10.0.40 of Intelligent Order Management
description: This article lists the features that are included in version 10.0.40 of Intelligent Order Mangement.
author: raybennett-msft
ms.date: 04/30/2024
ms.custom: 
  - bap-template
  - evergreen
ms.topic: conceptual
ms.author: bennettray
ms.reviewer: johnmichalak
---

# What's new or changed for version 10.0.40 of Intelligent Order Management

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

This article lists the features that are included in the platform updates for version 10.0.40 of finance and operations apps. This version has a build number of 7.0.7279.17 and is available on the following schedule:

- **Preview of release:** April 2024
- **General availability of release (self-update):** May 2024
- **General availability of release (auto-update):** June 2024

## Features included in this release

This section contains a table that lists the features that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|


## Feature enhancements included in this release

This section contains a table that lists the enhancements that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics Lifecycle Services, and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=932660).

### Dynamics 365: 2024 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2024 release wave 1 plan](/dynamics365/release-plan/2024wave1/). All of the details, end to end, top to bottom, are captured in a single document that you can use for planning.

### Removed and deprecated platform features

The [Removed or deprecated platform features](../../fin-ops/get-started/removed-deprecated-features-platform-updates.md) topic describes features that have been removed, or that are planned for removal in platform updates of finance and operations apps.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

Deprecation notices are added in the [Removed or deprecated platform features](../../fin-ops/get-started/removed-deprecated-features-platform-updates.md) article 12 months before the removal of any feature from the product.

For breaking changes that affect only compilation time, but that are binary-compatible with sandbox and production environments, the deprecation time is less than 12 months. Typically, these changes are 
functional updates that must be made to the compiler.
