---
title: Application Lifecycle Management feature walkthrough (preview)
description: This article describes the step by step walkthrough of Application Lifecycle Management.
author: sumanic
ms.author: anvenkat
ms.reviewer: johnmichalak
ms.service: dynamics-365-intelligent-order-management
ms.date: 10/24/2025
ms.custom: 
  - bap-template
ms.topic: overview
---

# Application Lifecycle Management feature walkthrough (preview)

[!INCLUDE[banner](includes/banner.md)]
[!INCLUDE [preview-banner](includes/preview-banner.md)]

This guide provides a walkthrough for enabling and using the Application Lifecycle Management (ALM) preview feature in Microsoft Dynamics 365 Intelligent Order Management. It's based on the ALM demonstration video and includes instructions for activating the feature, adding orchestration flows to a solution, and deploying across environments.

## Prerequisites

Access to **Dynamics 365 Intelligent Order Management** source and target environments.

## Step 1: Activate the ALM preview feature in the source environment

To activate the ALM preview feature in the source environment, follow these steps.

1. Sign in to your **Dynamics 365 environment** and the **Intelligent Order Management** app in the source environment.
1. From the landing page, select **Settings** > **Configure**.
1. Select **General** > **Manage**.
1. Select **Feature version controls** > **Manage**.
1. Find the setting for **Application Lifecycle Management Feature**.
1. Enable the feature and pick a name for the export solution.

## Step 2: Create the solution for export

To create the solution for export, follow these steps

1. From the Power Apps Maker portal, open the source environment.
1. Open the solution list.
1. Create a solution with the name you used in the previous configuration.

## Step 3: Open Dynamics 365 Intelligent Order Management and access orchestration flows

To open Dynamics 365 Intelligent Order Management and access orchestration flows, follow these steps.

1. Sign in to your **Dynamics 365 environment** and the **Intelligent Order Management** app in the source environment.
1. Go to **Intelligent Order Management** > **Orchestrations → Flows**.
1. Select the orchestration flow you want to manage.

## Step 4: Add flow to a solution

To add flow to a solution, follow these steps.

1. In the command bar, select **Add to Solution**.
1. Confirm the selection and proceed.

## Step 5: Export a solution

To export a solution, follow these steps.

1. Go to **Power Platform** > **Solutions**.
1. Select the solution containing your orchestration flow.
1. Select **Export**.
1. Choose **Managed**.
1. Download the exported package.

## Step 6: Import to target environment

To import to target environment, follow these steps.

1. Switch to your target environment.
1. Go to **Solutions** > **Import**.
1. Import the solution.

## Step 7: Validate and publish your changes

To validate and publish your changes, follow these steps.

1. Open Dynamics 365 Intelligent Order Management in the target environment.
1. Confirm the providers are created and activate them.
1. Confirm the policies are created and publish them.
1. Confirm the orchestration appears under **Intelligent Order Management** > **Orchestrations → Flows**.
1. Select **Publish** to activate the orchestration.
1. Test with sample orders.

[!INCLUDE[footer-include](includes/footer-banner.md)]
