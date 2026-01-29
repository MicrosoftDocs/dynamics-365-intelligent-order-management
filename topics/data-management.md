---
author: josaw1
description: Learn about the data management systems in Dynamics 365 Intelligent Order Management.
ms.date: 03/21/2025
ms.custom: 
  - bap-template
ms.topic: article
ms.author: anvenkat

title: Data management

---


# Data management

[!include [banner](includes/banner.md)]

Managing data is an important part of setup and administration in Dynamics 365 Intelligent Order Management. You can classify data in Intelligent Order Management into the following categories.

- System data: Set up data needed to support the administration of the app. Additionally, reference data is base data needed to support setup of master data or transactional data.

- Master data: Entities for orienting a business process. You might need master data to validate or drive different processes in the orchestration of order transactions.

- Transaction data: The main transactional document recorded by the app in the processing of order flows.

Intelligent Order Management is designed for complex environments where many internal and external systems communicate data. You design systems that share master data with other systems.

Intelligent Order Management is built on Microsoft Dataverse and the common data model, which you can use to store data you consider to be master data. You can configure Intelligent Order Management as the central app with a single view of orders in your organization, so you might consider it the master system. However, other business apps, such as your existing ERP app, might originate master data such as products or accounts. Therefore, you might consider that ERP app the master data system for some types of data.

## System data

You can configure and use parameters throughout Intelligent Order Management. The app provides pages where you can administer system parameters that are needed to control functionality. Use these pages when you're initially setting up Intelligent Order Management and throughout day-to-day administration.

Some data is important for the operation of the systems, such as currency and units of measure. You can access this type of reference data through the pages provided for master data entities like product. You can also import and export this data by using the tools listed in the following sections.

## Master data

Business apps often use master data entities that represent key business entities such as accounts and products. Intelligent Order Management uses these types of entities to validate data as it moves through the orchestration flow. For example, you might have customer account numbers, so when an order comes into Intelligent Order Management, you might want to look up the account number.

Intelligent Order Management works with or without master data. Master data is an important concept if you use the orchestration capabilities, but you can use different source and destination systems to control master data at those endpoints.

An example is account data from e-commerce systems in D2C and D2C flows. If you receive an order from an online marketplace, you likely don't have an account number from that system. The order arrives with minimal customer information. You might receive thousands of these orders a day in high volume scenarios, but there's enough information on the orders to send to fulfillment, and you don't validate these orders against an account master list. Similarly, products on the order lines can use the write-in product concepts, so you might choose to not catalog a product list in Intelligent Order Management for validation of product information as it moves through the orchestration flow.

If you need to set up master data such as accounts or products, use the appropriate page in the app and use the import and export tools listed in the following sections.

## Transactional data

Order transactions are the main transactional entity in Intelligent Order Management. The focus in the current release is on sales orders. The common data model in Dataverse includes entities for a sales order header named **Order** and a sales order line named **Order Product**.

Intelligent Order Management introduces a new transactional entity called a **Fulfillment Order**. This entity includes information about the fulfillment of a sales order line and includes a header named **Fulfillment Order** and lines named **Fulfillment Order Product**.

In Intelligent Order Management, orchestration is designed around the order concept of a sales order.

## Import and export data

Intelligent Order Management enables admins and business users to use several different tools to import and export data.

- Using the app: Business users can use pages in the app to export to Excel and import from Excel to update data like transactions and master data.

- Maker Portal: Admins can use the Maker Portal to import and export data from Dataverse. To learn more, see [Import or export data from Microsoft Dataverse](/powerapps/maker/data-platform/data-platform-import-export).

- Dataflows: Admins can use the capabilities of dataflows to move data between Dataverse and other apps. To learn more, see [Self-service data prep with dataflows](/powerapps/maker/data-platform/self-service-data-prep-with-dataflows).
