---
author: anvenkat
description: This topic provides information about orchestrating on custom entities within IOM
ms.date: 02/03/2025
ms.custom: 
  - bap-template
ms.topic: conceptual
ms.author: anvenkat

title: Create orchestration flows
---

# Custom entity orchestration

Custom entity orchestration allows customers to orchestrate on the custom data verse entities that are created for business purposes. For example if there is a need to create a non standard entity for orchestrating
fulfillment or transportation processes, custom entity orchestration would be a good choice. Please note you can use a combination of custom and standard entities in your orchestration flow. 

## Steps to enable custom entity orchestration.

- Create a new custom table in power apps. This will be any custom table that you would create outside of the out of box business data verse entities that are availabel for orchestration.
- In power apps , go to **More** , select **Choices** and choose **Assoicated Entity** . Under the option set, add your custom table that you created.
- Create a record in the **IOM entity metadata** table. These can be looked up by looking at settings and columns on the custom entity:
      1. **Name**: logical name for the custom entity
      1. **Associated Entity**: the option set entry created above.
      1. **Has Standard State**: if the custom entity is using out of box state and status columns.
      1. **ID column name**: typically, logical name with Id suffix. It is the specific id column of the custom entity.
      1. **Plural Name**: the plural logical name set on creation.
- To finally use the custom entity in orchestration, it is required to create the following orchestration related entities for the newly created entity.
     -**Action type**
     -**Action type input business event**
     -**Business event definition**
     -**Business event input and output**

  
