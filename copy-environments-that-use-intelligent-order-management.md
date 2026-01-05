---
title: Copy environments that use Intelligent Order Management
description: Learn how to safely copy environments that use Dynamics 365 Intelligent Order Management, including required post-copy configuration steps for providers, orchestrations, and integrations.
author: anvenkat
ms.author: anvenkat
ms.topic: how-to
ms.date: 01/05/2026
ms.custom: bap-template
---

# Copy an environment with Intelligent Order Management

This article describes the recommended steps for copying environments that use Dynamics 365 Intelligent Order Management (IOM). It covers copying both the Dynamics 365 Finance and Operations database and the associated Power Platform Dataverse environment that hosts the IOM app.

Use this guidance when performing environment refreshes for testing, validation, or disaster recovery purposes.

---

## Before you begin

- Ensure you have administrative access to:
  - Dynamics 365 Finance and Operations
  - Power Platform admin center
- Confirm that Intelligent Order Management is installed in the target environment.
- Plan a validation window after the copy completes to reconfigure integrations and orchestrations.

---

## Step 1: Copy Finance and Operations and Dataverse environments

1. Copy the Finance and Operations database by following the instructions in [Database refresh](https://learn.microsoft.com/dynamics365/fin-ops-core/dev-itpro/database/database-refresh). 
2. Copy the Power Platform Dataverse environment by following [Copy an environment](https://learn.microsoft.com/power-platform/admin/copy-environment). 

After the copy completes, the target environment is placed in **administration mode**, and all background operations are disabled. 

---

## Step 2: Exit administration mode

1. Go to the [Power Platform admin center](https://learn.microsoft.com/power-platform/admin/admin-documentation).
2. Select the copied target environment.
3. In **Details**, select **Edit**.
4. Turn off **Administration mode** and save.

The environment must exit administration mode before IOM background processes can run. 

---

## Step 3: Reconfigure IOM connections and system activation

1. Open the Intelligent Order Management app.
2. When prompted, allow app permissions to access the environment. 
3. Go to **Core settings > Admin home > Connection references**.
4. Open each connection reference and save it to ensure it is owned by the correct user. 
5. Select **Activate system** to re-enable IOM. 

---

## Step 4: Review and activate Power Automate flows

1. Go to the [Power Apps maker portal](https://learn.microsoft.com/power-apps/maker/canvas-apps/sign-in-to-power-apps).
2. Select the target environment.
3. Review all flows and confirm they are active.
4. Update flows that use custom connectors or HTTP triggers as required.

For flow-specific guidance, see [Copy an environment – Flows](https://learn.microsoft.com/power-platform/admin/copy-environment#flows). 

---

## Step 5: Prepare orchestrations for provider reinstallation

To ensure clean provider reinstallation, remove provider actions from all orchestration flows.

1. In the IOM app, go to **Orchestrations > Flows**.
2. For each orchestration (published and unpublished):
   - Open the flow.
   - Exit read-only mode if required.
   - Record the provider actions used.
   - Remove all provider actions from the flow.
3. Save the updated flows.

This step is required because provider actions do not remain valid after an environment copy. 

---

## Step 6: Reinstall providers

1. In the IOM app, go to **Providers > Installed**.
2. Delete all installed providers.
3. Go to **Providers > Library** and reinstall the required providers. 

---

## Step 7: Restore provider actions and publish orchestrations

1. Return to **Orchestrations > Flows**.
2. Add provider actions back to each orchestration.
3. When selecting provider actions, type to search and ensure newly created provider actions are selected.
4. Save and publish each flow. 

---

## Step 8: Reconfigure dual-write (if applicable)

If dual-write is enabled in the target environment:

1. Configure security roles by following [Set up dual-write security roles and permissions](https://learn.microsoft.com/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/security-roles). 
2. In Finance and Operations:
   - Go to **Data management > Dual-write**.
   - Select **Reset link**.
   - Run **Health check**. 
3. Reconfigure dual-write as if setting it up in a new environment.

> Initial synchronization may not be required if data is already aligned. 

---

## Troubleshooting

### Dual-write initial sync fails due to missing reference data

You might encounter an error indicating that a team or business unit reference cannot be resolved during initial sync. Although the data exists, the environment copy process may rename the default team associated with the root business unit.

**Workaround**:
- Run **Reset link**, followed by **Health check**.
---

### Provider action **Send for Fulfillment** does not trigger

If provider action execution history is empty and you see an *Event expired in the 'Ready' state* error, the Microsoft Finance and Operations apps provider may be incorrectly installed.

**Resolution**:
- Delete the provider.
- Reinstall it from the provider library. 

---

### Inspect provider action run history

To validate provider execution:

1. Open the Power Apps maker portal.
2. Select **Solutions > Default Solution**.
3. Filter **Cloud flows** by `msdyn_finops_releaseordertosync`.
4. Review execution status and connection references. 

---

## Additional resources

- [Troubleshoot issues during initial synchronization](https://learn.microsoft.com/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/dual-write-troubleshooting-initial-sync) 
- [Troubleshoot live synchronization issues](https://learn.microsoft.com/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/dual-write-troubleshooting-live-sync) 
- [Dual-write error codes reference](https://learn.microsoft.com/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/dual-write-error-codes) 

