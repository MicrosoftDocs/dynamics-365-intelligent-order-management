---
author: sumanic
description: This topic describes the Internal External ID mapping in Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 07/29/2021
ms.topic: conceptual
ms.author: sumanic

title: Internal External ID mapping in Intelligent Order Management
---


# Internal External ID mapping in Intelligent Order Management

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

Dynamics 365 Intelligent Order Management comes with an Out of the box Internal External ID mappings. This will allow you to:

1. **Define** relationship between identities in an enterprise such that applications and operating systems from one user identity to another, related user identity
1. **Smooth** integration across multiple systems
1. Enable an **end to end visualization** of multiple systems representation for same entity.

# What is Intelligent Order Management Offering?

In order to be able to leverage the full potential of Internal External ID mapping, IOM offers the below:

1. Out of the box **configurable** mapping and mapping tables.
1. Easy **integration** across multiple systems.
1. **End to End visibility** in IOM on the connecting systems.
1. **Flexibility** to add your own mappings.

**Below are the Out of the Box configurations available:**

1. Accounts
2. Products
3. Price Lists
4. Warehouses
5. Currencies
6. Unit Groups
7. Units

You will now see an new page added into the IOM called as **Configuration**. This page will allow you to configure the mapping of columns and values across your different providers.

Each of the above Out of the Box configurations will map to a corresponding **dataverse mapping table** that will preserve these mappings for usability in various integrations with providers.

Below is a **sample example** of one of our provider warehouses being mapped to IOM warehouse.

![image](media/warehouseMapping.png)

**Note:** Provider based grouping of mappings is not available as part of current release. This will be covered in upcoming releases.
