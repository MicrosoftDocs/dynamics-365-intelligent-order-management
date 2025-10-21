---
author: sumanic
description: This article describes the step by step walkthrough of Application Lifecyle Management preview.
ms.service: dynamics-365-intelligent-order-management
ms.date: 03/21/2025
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
- Access to **Dynamics 365 Intelligent Order Management** environment.
- Admin permissions for **Feature Management** and **Power Platform**.
- Installed **Power Automate** connectors for IOM.

---

## Step 1: Activate the ALM Preview Feature
1. Sign in to your **Dynamics 365 environment**.
2. Navigate to **Feature Management**.
3. Search for **Application Lifecycle Management (ALM)**.
4. Click **Enable** for the ALM preview feature.



---

## Step 2: Open IOM and Access Orchestration Flows
1. Go to **Intelligent Order Management → Orchestration Designer**.
2. Select the orchestration flow you want to manage.
3. Click **Edit** to open the flow details.



---

## Step 3: Add Flow to a Solution
1. In the flow details pane, click **Add to Solution**.
2. Choose an existing solution or click **New Solution**.
   - Enter **Name** and **Publisher** if creating a new solution.
3. Confirm addition.



---

## Step 4: Export the Solution
1. Navigate to **Power Platform → Solutions**.
2. Select the solution containing your orchestration flow.
3. Click **Export**.
   - Choose **Managed** or **Unmanaged**.
4. Download the exported package.



---

## Step 5: Import to Target Environment
1. Switch to your **target environment**.
2. Go to **Solutions → Import**.
3. Upload the exported package.
4. Validate and complete the import.



---

## Step 6: Validate and Publish
1. Open the solution in the target environment.
2. Confirm the orchestration flow appears under **IOM → Orchestration Designer**.
3. Click **Publish** to activate the flow.
4. Test with sample orders.



---

## Step 7: Monitor and Troubleshoot
- Use the **ALM dashboard** to:
  - Check deployment status.
  - Review error messages.
  - Validate workflow IDs and environment variables.
