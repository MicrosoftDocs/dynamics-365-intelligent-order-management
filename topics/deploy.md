---
author: josaw1
description: This topic provides information about how to deploy Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 05/17/2021
ms.topic: conceptual
ms.author: josaw

title: Deployment

---


# Deployment

[!include [banner](includes/banner.md)]


Intelligent Order Management is a Software as a Service (SaaS) app that runs on the Microsoft Azure infrastructure.

## Deployment options

The preview release of Intelligent Order Management can be deployed as a trial in two ways.

-   Sign up for trial: Visit the [Dynamics 365 Intelligent Order Management marketing page](https://dynamics.microsoft.com/intelligent-order-management/). Select **Get started** to step through the process of creating a trial system. You'll be prompted to enter your email address and other information. To access Intelligent Order Management, you must meet at least one of the following requirements: 
    - If you aren't a part of a Microsoft tenant: Microsoft will create a tenant for you, and add Intelligent Order Management to it. You'll be the admin of the tenant and environment. 
    - If you're an admin of an existing Microsoft tenant: Microsoft will provide a trial Microsoft Power Apps environment and install Intelligent Order Management there. If you're a part of an existing Microsoft tenant and not the admin, you won't be able to get access to the trial. 

-   Power Platform Administration Center (PPAC): If you're an existing Microsoft Power Platform admin, you can deploy a new environment for your organization for evaluation. To learn more about PPAC, see [Working with the admin portals](https://docs.microsoft.com/power-platform/admin/wp-work-with-admin-portals). You'll only be able to deploy in trial environments. To learn more about deployment environments, see [About trial environments](https://docs.microsoft.com/power-platform/admin/trial-environments).

## System requirements

You can deploy the preview release through the trial experience, which is provisioned and managed by Microsoft. As a customer or a partner, there are no systems prerequisites for using the trial experience.

## Local requirements

Intelligent Order Management is deployed in the Microsoft Azure data centers. Admins and business users access the app by using a web browser. There are no components that must be downloaded and configured on a user machine. Use a common web browser of your choice, such as Microsoft Edge. For more information about supported web browsers and hardware requirements, see [Web application requirements](https://docs.microsoft.com/power-platform/admin/web-application-requirements).

## Service protection limits

Service protection limits exist to protect the health of the service. These limits provide a level of protection against random and unexpected surges in request volumes that threaten the availability and performance characteristics of the Microsoft Dataverse platform. Microsoft will publish guidance on the limits for Intelligent Order Management when the app is released for general availability. To learn more about this concept, see [Why choose Microsoft Dataverse?](https://docs.microsoft.com/powerapps/maker/data-platform/why-dataverse-overview)

## Capacity add-ons

Microsoft is managing the trial environments for customers to evaluate and provide feedback. More information will be available when the app is released for general availability. To learn more about this concept, see [Why choose Microsoft Dataverse?](https://docs.microsoft.com/powerapps/maker/data-platform/why-dataverse-overview)

## Backups

Trial environments are for evaluation and feedback purposes and come with demo data to support evaluations. Trial environments will be deleted after the 30-day trial period if you provision a trial environment and your environment isn't designated to be recovered after the 30-day trial period has ended.

## Additional resources
[Set up an environment](setup.md)
