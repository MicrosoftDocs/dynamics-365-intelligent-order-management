---
title: Copy environments that use Intelligent Order Management
description: Learn how to safely copy environments that use Dynamics 365 Intelligent Order Management, including required post-copy configuration steps for providers, orchestrations, and integrations.
author: anvenkat
ms.author: anvenkat
ms.topic: how-to
ms.date: 01/07/2026
ms.custom: bap-template
---

# Copy an environment with Intelligent Order Management

[!include [banner](includes/banner.md)]

This article describes the recommended steps for copying environments that use Dynamics 365 Intelligent Order Management. It covers copying both the finance and operations database and the associated Microsoft Dataverse environment that hosts the Intelligent Order Management app.

Use this guidance when performing environment refreshes for testing, validation, or disaster recovery purposes.

## Before you begin

- Ensure you have administrative access to:
  - Finance and operations apps
  - Power Platform admin center
- Confirm that Intelligent Order Management is installed in the target environment.
- Plan a validation window after the copy completes to reconfigure integrations and orchestrations.

## Step 1: Copy the finance and operations apps and Dataverse environments

1. Copy the finance and operations apps database by following the instructions in [Database refresh](/dynamics365/fin-ops-core/dev-itpro/database/database-refresh).
1. Copy the Power Platform Dataverse environment by following [Copy an environment](/power-platform/admin/copy-environment).

After the copy completes, the target environment is placed in **administration mode**, and all background operations are disabled.

## Step 2: Exit administration mode

To exit administration mode, follow these steps:

1. Go to the [Power Platform admin center](/power-platform/admin/admin-documentation).
1. Select the copied target environment.
1. In **Details**, select **Edit**.
1. Turn off **Administration mode** and save.

The environment must exit administration mode before Intelligent Order Management background processes can run.

## Step 3: Reconfigure Intelligent Order Management connections and system activation

To reconfigure Intelligent Order Management connections and system activation, follow these steps:

1. Open the Intelligent Order Management app.
1. When prompted, allow app permissions to access the environment.
1. Go to **Core settings > Admin home > Connection references**.
1. Open each connection reference and save it to ensure it's owned by the correct user.
1. Select **Activate system** to re-enable Intelligent Order Management.

## Step 4: Review and activate Power Automate flows

To review and activate Power Automate flows, follow these steps:

1. Go to the [Power Apps maker portal](/power-apps/maker/canvas-apps/sign-in-to-power-apps).
1. Select the target environment.
1. Review all flows and confirm they're active.
1. Update flows that use custom connectors or HTTP triggers as required.

For flow-specific guidance, see [Copy an environment – Flows](/power-platform/admin/copy-environment#flows).

## Step 5: Prepare orchestrations for provider reinstallation

To ensure clean provider reinstallation, remove provider actions from all orchestration flows. To prepare orchestrations for provider reinstallation, follow these steps:

1. In the Intelligent Order Management app, go to **Orchestrations > Flows**.
1. For each orchestration (published and unpublished):
   - Open the flow.
   - Exit read-only mode if necessary.
   - Record the provider actions used.
   - Remove all provider actions from the flow.
1. Save the updated flows.

This step is required because provider actions aren't valid after an environment copy.

## Step 6: Reinstall providers

To reinstall providers, follow these steps:

1. In the Intelligent Order Management app, go to **Providers > Installed**.
1. Delete all installed providers.
1. Go to **Providers > Library** and reinstall the required providers.

## Step 7: Restore provider actions and publish orchestrations

To restore provider actions and publish orchestrations, follow these steps:

1. Return to **Orchestrations > Flows**.
1. Add provider actions back to each orchestration.
1. When selecting provider actions, type to search and ensure you select newly created provider actions.
1. Save and publish each flow.

## Step 8: Reconfigure dual-write (if applicable)

If dual-write is enabled in the target environment:

1. Configure security roles by following [Set up dual-write security roles and permissions](/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/security-roles).
1. In Finance and Operations:
   - Go to **Data management > Dual-write**.
   - Select **Reset link**.
   - Run **Health check**.
1. Reconfigure dual-write as if setting it up in a new environment.

> [!NOTE]
> Initial synchronization might not be necessary if the data is already aligned.

### Dual-write initial sync fails due to missing reference data

You might encounter an error indicating that a team or business unit reference can't be resolved during initial sync. Although the data exists, the environment copy process might rename the default team associated with the root business unit. If this occurs, run **Reset link**, and then run **Health check**.

### Provider action **Send for Fulfillment** doesn't trigger

If the provider action execution history is empty and you see an *Event expired in the 'Ready' state* error, the Microsoft Finance and Operations apps provider might be incorrectly installed. If this occurs, delete the provider and then reinstall it from the provider library.

### Inspect provider action run history

To validate provider execution, follow these steps:

1. Open the Power Apps maker portal.
1. Select **Solutions > Default Solution**.
1. Filter **Cloud flows** by `msdyn_finops_releaseordertosync`.
1. Review execution status and connection references.

## Additional resources

[Troubleshoot issues during initial synchronization](/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/dual-write-troubleshooting-initial-sync)
[Troubleshoot live synchronization issues](/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/dual-write-troubleshooting-live-sync)
[Dual-write error codes reference](/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/dual-write-error-codes)

[!INCLUDE[footer-include](includes/footer-banner.md)]
