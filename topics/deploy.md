---
author: josaw1
description: Learn how to deploy Dynamics 365 Intelligent Order Management.
ms.date: 01/27/2026
ms.custom: 
  - bap-template
ms.topic: article
ms.author: anvenkat
title: Deployment
---


# Deployment

[!include [banner](includes/banner.md)]

Intelligent Order Management is a software as a service (SaaS) app that runs on the Microsoft Azure infrastructure.

## Deployment options

You can deploy the preview release of Intelligent Order Management as a trial in two ways.

- Sign up for trial: Visit the [Dynamics 365 Intelligent Order Management marketing page](https://dynamics.microsoft.com/intelligent-order-management/). Select **Get started** to step through the process of creating a trial system. You're prompted to enter your email address and other information. To access Intelligent Order Management, you must meet at least one of the following requirements:
  - If you're not part of a Microsoft tenant: Microsoft creates a tenant for you and adds Intelligent Order Management to it. You're the admin of the tenant and environment.
  - If you're an admin of an existing Microsoft tenant: Microsoft provides a trial Microsoft Power Apps environment and installs Intelligent Order Management there. If you're part of an existing Microsoft tenant and not the admin, you can't get access to the trial.

- Power Platform Administration Center: If you're an existing Microsoft Power Platform admin, you can deploy a new environment for your organization for evaluation. Learn about Power Platform Administration Center in [Working with the admin portals](/power-platform/admin/wp-work-with-admin-portals). You can only deploy in trial environments. Learn more about deployment environments in [About trial environments](/power-platform/admin/trial-environments).

## System requirements

You deploy the preview release through the trial experience, which Microsoft provisions and manages. As a customer or a partner, there are no systems prerequisites for using the trial experience.

## Local requirements

You deploy Intelligent Order Management in the Microsoft Azure data centers. Admins and business users access the app by using a web browser. There are no components that must be downloaded and configured on a user machine. Use a common web browser of your choice, such as Microsoft Edge. Learn more about supported web browsers and hardware requirements in [Web application requirements](/power-platform/admin/web-application-requirements).

## Service protection limits

Service protection limits exist to protect the health of the service. These limits provide a level of protection against random and unexpected surges in request volumes that threaten the availability and performance characteristics of the Microsoft Dataverse platform. Microsoft publishes guidance on the limits for Intelligent Order Management when the app is released for general availability. For more information about this concept, see [Why choose Microsoft Dataverse?](/powerapps/maker/data-platform/why-dataverse-overview)

## Capacity add-ons

Microsoft manages the trial environments for customers to evaluate and provide feedback. More information is available when the app is released for general availability. For more information about this concept, see [Why choose Microsoft Dataverse?](/powerapps/maker/data-platform/why-dataverse-overview)

## Backups

Use trial environments for evaluation and feedback. They include demo data to support evaluations. If you provision a trial environment, Microsoft deletes the trial environment after the 30-day trial period unless your environment is designated to be recovered.

## Additional resources

[Set up an environment](setup.md)
