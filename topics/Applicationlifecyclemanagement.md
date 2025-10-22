---
author: sumanic
description: This article describes the step by step walkthrough of Application Lifecyle Management preview.
ms.service: dynamics-365-intelligent-order-management
ms.date: 10/21/2025
ms.custom: 
  - bap-template
ms.topic: overview
ms.author: anvenkat
title: IOM application life cycle management.

---


# Dynamics 365 IOM Application Lifecycle Management (ALM) – Preview Feature Walkthrough

## Overview
This guide provides a step-by-step walkthrough for enabling and using the **Application Lifecycle Management (ALM)** preview feature in **Dynamics 365 Intelligent Order Management (IOM)**. It is based on the ALM demonstration video and includes instructions for activating the feature, adding orchestration flows to a solution, and deploying across environments.

---

## Prerequisites
Access to **Dynamics 365 Intelligent Order Management** source and target environments.
 
---
 
## Step 1: Activate the ALM Preview Feature in the source environment
1. Sign in to your **Dynamics 365 environment** and the **Intelligent Order Management** app in the source environment.
1. From the landing page, click **Settings** > **Configure**.
1. Then click **General** > **Manage**.
1. Then click **Feature version controls** > **Manage**.
1. Find the setting for **Application Lifecycle Management Feature (preview)**.
1. Enable the feature and pick a name for the export solution.
 
 
---
 
## Step 2: Create the solution for export
1. From the Power Apps Maker Portal, open the source environment.
1. Open the solution list.
1. Create a solution with the name you used in the previous configuration.
 
---
 
## Step 3: Open IOM and Access Orchestration Flows
1. Sign in to your **Dynamics 365 environment** and the **Intelligent Order Management** app in the source environment.
1. Go to **Intelligent Order Management → Orchestrations → Flows**.
2. Select the orchestration flow you want to manage.
 
---
 
## Step 4: Add Flow to a Solution
1. In the command bar, click **Add to Solution**.
2. Confirm addition.
 
---
 
## Step 5: Export the Solution
1. Navigate to **Power Platform → Solutions**.
2. Select the solution containing your orchestration flow.
3. Click **Export**.
   - Choose **Managed**.
4. Download the exported package.
 
 
---
 
## Step 6: Import to Target Environment
1. Switch to your **target environment**.
2. Go to **Solutions → Import**.
3. Import the solution.
 
 
---
 
## Step 7: Validate and Publish
1. Open IOM in the target environment.
1. Confirm the Providers are created and activate them.
1. Confirm the Policies are created and publish them.
2. Confirm the Orchestration appears under  **Intelligent Order Management → Orchestrations → Flows**.
3. Click **Publish** to activate the orchestration.
4. Test with sample orders.
 
