---
author: josaw1
description: This topic provides an overview data management systems in Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 05/17/2021
ms.topic: conceptual
ms.author: josaw

title: Data management

---


# Data management
[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]



Managing data is an important part of setup and administration in Dynamics 365 Intelligent Order Management. Data in Intelligent Order Management can be classified into the following categories.

-   System data: Setup data needed to support the administration of the app. Additionally, reference data is base data needed to support setup of master data or transactional data.

-   Master data: Entities for orienting a business process. Master data may be needed to validate or drive different processes in the orchestration of order transactions.

-   Transaction data: The main transactional document recorded by the app in the processing of order flows.

Intelligent Order Management is designed to be used in complex environments where data is communicated between many internal and external systems. You'll design systems that will be used to share master data with other systems.

Intelligent Order Management is built on Microsoft Dataverse and the common data model which allow you to store data you consider to be master data. Intelligent Order Management can be configured to be the central app with a single view of orders in your organization, so you may want to consider it to be the master system. However, master data such as products or accounts may originate from other business apps, such as your existing ERP app, and therefore you may consider that ERP app the master data system for some types of data.

## System data 

You can configure and use parameters throughout Intelligent Order Management. The app provides pages where you can administer system parameters that are needed to control functionality. You can use those pages when you're initially setting up Intelligent Order Management and throughout day-to-day administration.

Some data may be important for the operation of the systems, such as currency and units of measure. This type of reference data can be accessed through the pages provided for master data entities like product and can also be imported and exported with the tools listed below.

## Master data

Business apps are often designed around master data entities that are key business entities such as accounts and products. Intelligent Order Management use these types of entities to validate data as it moves through the orchestration flow. For example, you may have customer account numbers, so when an order is brought into Intelligent Order Management, you may want to look up the account number.

Intelligent Order Management is designed to work with or without master data. Master data is an important concept if you choose to use the orchestration capabilities, but you can use different source and destination systems to control master data at those endpoints.

An example is account data from e-commerce systems in D2C and D2C flows. If you receive an order from an online marketplace, it's unlikely that you'll have an account number from that system. The order will arrive with minimal customer information. You may receive thousands of these orders a day in high volume scenarios, but there'll be enough information on the orders to send to fulfillment, and you won't validate these orders against an account master list. Similarly, products on the order lines can leverage the write-in product concepts, so you may choose to not catalog a product list in Intelligent Order Management for validation of product information as it moves through the orchestration flow.

If you need to set up master data such as accounts or products, you can use the appropriate page in the app and you can use the import and export tools listed below.

## Transactional data

Order transactions are the main transactional entity in Intelligent Order Management. The focus in the preview release is on sales orders. The common data model in Dataverse includes entities for a sales order header named **Order** and a sales order line named **Order Product**.

Intelligent Order Management introduces a new transactional entity called a **Fulfillment Order**. This entity includes information about the fulfillment of a sales order line and includes a header named **Fulfillment Order** and lines named **Fulfillment Order Product**.

In the preview release of Intelligent Order Management, orchestration is designed around the order concept of a sales order.

## Import and export data

Intelligent Order Management enables admins and business users to use several different tools to import and export data.

-   Using the app: Business users can use pages in the app to export to Excel and import from Excel to update data like transactions and master data.

-   Maker Portal: Admins can use the Maker Portal to import and export data from Dataverse. To learn more, see [Import or export data from Microsoft Dataverse](https://docs.microsoft.com/powerapps/maker/data-platform/data-platform-import-export).

-   Dataflows: Admins can leverage the capabilities of dataflows to move data between Dataverse and other apps. To learn more, see [Self-service data prep with dataflows](https://docs.microsoft.com/powerapps/maker/data-platform/self-service-data-prep-with-dataflows).
