---
author: josaw1
description: This topic provides information about how to deploy the preview version of Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 05/17/2021
ms.topic: conceptual
ms.author: josaw

title: Extensibility

---


# Extensibility

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

Dynamics 365 Intelligent Order Management is built as a Microsoft Dataverse application that enables customers and partners to extend the application. The following topics outline the areas of the application that can be extended to provide the functionality that your business requires. 

## Terminology
Understanding some of the terminology in Microsoft Dataverse will help you to get started. To learn more, see [Understand terminology in Microsoft Dataverse](/powerapps/developer/data-platform/understand-terminology).

## Data model
As part of the Dynamics 365 Intelligent Order Management solution, the application extends the common data model in Dataverse. As a customer, you can modify data entities to store additional data needed to implement your business processes. Modifying an entity allows you to add new fields to capture data or new tables to store related data that can help with the order and fulfillment process. For more information, see [Tables in Dataverse](/powerapps/maker/data-platform/entity-overview).

## User interface
The Dynamics 365 Intelligent Order Management user interface is built using model-driven app concepts. You can use the same technology to build additional forms that capture data for management orders, fulfillment, or other processes. For more information, see [What are model driven apps](/powerapps/maker/model-driven-apps/model-driven-app-overview). 

## Business logic
Business logic can be extended in Dynamics 365 Intelligent Order Management in multiple ways, depending on the complexity of what you need to implement. Business logic can be as simple as updating a field or as complicated as creating a complex optimization function. The following topic can help get you started. 
[Apply custom logic with business rules and flows in model-driven apps](/powerapps/maker/model-driven-apps/guide-staff-through-common-tasks-processes). 

## Providers
Building your own provider enables you to incorporate an external service that you can call through the orchestration flow. For more information about building a new provider, see [Customize an out-of-box provider](customize-provider.md). 

## Orchestration
Dynamics 365 Intelligent Order Management orchestration is business process logic that represents the flow of an order document. You can build your own orchestration flows. For more information, see [Orchestration designer](). 

## Business Intelligence
Dynamics 365 Intelligent Order Management is built on and extends the common data model. Understanding the concepts of the common data model will help you to determine what data can be stored with Dynamics 365 Intelligent Order Management, and to identify what you can use to enhance the reporting and business intelligence solutions you design for your business. For more information about the common data model, see [Common Data Model](/common-data-model). 
