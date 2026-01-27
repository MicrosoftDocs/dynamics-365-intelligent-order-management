---
title: Custom entity orchestration
description: Learn about orchestration on custom entities in Microsoft Dynamics 365 Intelligent Order Management.
ms.date: 01/27/2026
author: anvenkat
ms.author: anvenkat
ms.custom: 
  - bap-template
ms.topic: how-to
---

# Custom entity orchestration

[!INCLUDE[banner](includes/banner.md)]

Custom entity orchestration lets customers do orchestration on custom Microsoft Dataverse entities that are created for business purposes. For example, custom entity orchestration is a good choice if a nonstandard entity must be created to orchestrate fulfillment or transportation processes.

> [!NOTE]
> You can use a combination of custom and standard entities in your orchestration flow.

## Enable custom entity orchestration

To enable custom entity orchestration, follow these steps:

1. Create a custom table in Power Apps. This table is any custom table that you might create outside the out-of-box business Dataverse entities that are available for orchestration.
1. In Power Apps, go to **More**, select **Choices**, and then select **Associated Entity**. In the option set, add the custom table that you created.
1. Create a record in the **IOM entity metadata** table. Records can be looked up by using settings and columns on the custom entity:

    - **Name** is the logical name of the custom entity.
    - **Associated Entity** is the option set entry that you created.
    - **Has Standard State** indicates whether the custom entity uses out-of-box state and status columns.
    - **ID column name** is typically the logical name together with an ID suffix. It's the specific ID column of the custom entity.
    - **Plural Name** is the plural logical name that is set at creation.

1. To use the custom entity in orchestration, you must create the following orchestration-related entities for the new entity:

    - Action type
    - Action type input business event
    - Business event definition
    - Business event input and output

[!INCLUDE[footer-include](includes/footer-banner.md)]
