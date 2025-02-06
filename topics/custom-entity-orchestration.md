---
title: Custom entity orchestration
description: This topic provides information about orchestrating on custom entities within Microsoft Dynamics 365 Inetlligent Order Management
ms.date: 02/03/2025
author: anvenkat
ms.author: anvenkat
ms.custom: 
  - bap-template
ms.topic: how-to
---

# Custom entity orchestration

[!INCLUDE[banner](../includes/banner.md)]

Custom entity orchestration allows customers to orchestrate on the custom Microsoft Dataverse entities that are created for business purposes. For example, if there's a need to create a nonstandard entity for orchestrating fulfillment or transportation processes, custom entity orchestration would be a good choice. 

> [!NOTE]
> You can use a combination of custom and standard entities in your orchestration flow. 

## Enable custom entity orchestration

To enable custom entity orchestration, follow these steps.

1. Create a new custom table in Microsoft Power Apps. This table is any custom table that you would create outside of the out of box business Dataverse entities that are available for orchestration.
1. In Power Apps, go to **More**, select **Choices**, and then select **Associated Entity**. In the option set, add your custom table that you created.
1. Create a record in the **IOM entity metadata** table. These records can be looked up by looking at settings and columns on the custom entity:
   1. **Name**  is the logical name for the custom entity.
   1. **Associated Entity** is the option set entry you previously created.
   1. **Has Standard State** Select if the custom entity is using out of box state and status columns.
   1. **ID column name** is typically the logical name with ID suffix. It's the specific ID column of the custom entity.
   1. **Plural Name** is the plural logical name set on creation.
1. To use the custom entity in orchestration, you must create the following orchestration related entities for the newly created entity.
   - **Action type**
   - **Action type input business event**
   - **Business event definition**
   - **Business event input and output**

  
[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
