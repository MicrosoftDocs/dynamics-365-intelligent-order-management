---
author: josaw1
description: This topic provides information about how Dynamics 365 Intelligent Order Management can be extended.
ms.date: 03/21/2025
ms.custom: 
  - bap-template
ms.topic: article
ms.author: josaw

title: Extensibility

---


# Extensibility

[!include [banner](includes/banner.md)]


Dynamics 365 Intelligent Order Management is built as a Microsoft Dataverse application that enables customers and partners to extend the application. This topic lists where you can find more information about how the application that can be extended to provide the functionality that your business requires 

## Terminology
Understanding some of the terminology in Microsoft Dataverse will help you to get started. To learn more, see [Understand terminology in Microsoft Dataverse](/powerapps/developer/data-platform/understand-terminology).

## Data model
As part of the Intelligent Order Management solution, the application extends Common Data Model in Dataverse. As a customer, you can modify data entities to store additional data needed to implement your business processes. Modifying an entity allows you to add new fields to capture data or new tables to store related data that can help with the order and fulfillment process. For more information, see [Tables in Dataverse](/powerapps/maker/data-platform/entity-overview).

## User interface
The Intelligent Order Management user interface is built using model-driven app concepts. You can use the same technology to build additional forms that capture data for management orders, fulfillment, or other processes. For more information, see [What are model-driven apps](/powerapps/maker/model-driven-apps/model-driven-app-overview). 

## Business logic
Business logic can be extended in Intelligent Order Management in multiple ways, depending on the complexity of what you need to implement. Business logic can be as simple as updating a field or as complicated as creating a complex optimization function. To help get you started, see 
[Apply custom logic with business rules and flows in model-driven apps](/powerapps/maker/model-driven-apps/guide-staff-through-common-tasks-processes). 

## Providers
Building your own provider enables you to incorporate an external service that you can call through the orchestration flow. For more information about building a new provider, see [Customize an out-of-box provider](customize-provider.md). 

## Orchestration
Intelligent Order Management orchestration is business process logic that represents the flow of an order document. You can build your own orchestration flows. For more information, see [Orchestration flows](orchestration-flows.md). 

## Business intelligence
Intelligent Order Management is built on and extends Common Data Model. Understanding the concepts of Common Data Model model will help you to determine what data can be stored with Intelligent Order Management, and to identify what you can use to enhance the reporting and business intelligence solutions you design for your business. For more information about Common Data Model, see [Common Data Model](/common-data-model). 
