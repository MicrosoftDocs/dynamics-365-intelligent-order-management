---
author: josaw1
description: This topic provides an overview of Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 05/17/2021
ms.topic: conceptual
ms.author: josaw

title: Intelligent Order Management overview
---


# Intelligent Order Management overview

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]



With Dynamics 365 Intelligent Order Management, customers can manage the orchestration of orders through to fulfillment. These capabilities enable organizations to orchestrate order flows across different platforms and apps.

Intelligent Order Management is designed to operate in complex environments where there are many internal and external systems and partners that enable the supply chain processes. The platform is designed to scale up and down with a business, regardless of the organization size.

Intelligent Order Management is designed for customers that are implementing business to consumer, direct to consumer, and business to business order process flows.

Customers who want to implement new fulfillment strategies like buy-online ship, buy-online and collect, have complex implementation requirements. Those customers choose different e-commerce systems and fulfillment partners to help implement business strategies. Intelligent Order Management enables customers to choose the best systems and partners, and integrate them into a single system.

Intelligent Order Management is designed as a Microsoft Dataverse application and shares the common data model with other apps in the Dynamics 365  family. Intelligent Order Management has no dependency on other Dynamics 365 apps. However, it works with both Dynamics 365 and non-Dynamics 365 business apps through the provider framework.

In the preview release of Intelligent Order Management, partners and customers can benefit from the following.

-   Partners can understand the core architecture and integration capabilities and start developing solutions to integrate with external service or build application functionality.

-   Customers can learn the core components including the orchestration, fulfillment optimization, provider services concepts, data platform, and insights capabilities.

## Components

Intelligent Order Management is delivered as a cloud-based solution. The following list contains the core components of the solution: 

-   App: The Intelligent Order Management app provides an interface to view orders and the fulfillment state. It provides a single place to view orders, regardless of the order source or how they were fulfilled.

-   Providers: Providers enable the transfer of orders and fulfillment information between different platforms and apps.

-   Orchestration: Flows are configured to manage the journey of an order. Communication with providers creates events that drive an order through the flow. Customers implement business processes for their products and business requirements.

-   Inventory Visibility Service: This service provides real-time visibility of inventory in the supply network so that decisions can be made through the order flow. Inventory can be communicated from source and target systems through the orchestration flows and providers.

-   Fulfillment optimization: This is a service that can be leveraged through the orchestration flow. The service enables optimization decisions about where an order can be fulfilled, using concepts such as cost and closest in distance.

-   Insights: Understanding order and fulfillment metrics is critical in decision-making. Dashboards provide visibility to key order data and fulfillment key performance indicators (KPIs).

### Intelligent Order Management app

Intelligent Order Management provides a single view of an order that helps organizations understand the state of fulfillment. Orders can originate in different e-commerce systems, point of sales systems, electronic data interchange (EDI), and customer relationship management (CRM) apps.

### Providers

Providers allow customers to integrate Intelligent Order management with other systems. Providers wrap the API calls between systems and present them to the organization as actions. The actions can raise events which drive the orchestration.

Providers use Power Automate connectors. This technology allows Intelligent Order Management to connect to an ecosystem of platforms and apps that customers choose.

Intelligent Order Management will ship connectors to populate marketplace, e-commerce systems, fulfillment and logistics systems, and partners. Both customers and partners can use the platform capabilities of Power Automate and Microsoft Dataverse development tools to build new providers.

A customer may want to build a provider to an existing warehouse or manufacturing system in their organization. A partner can build providers to integrate their platforms or apps with the Intelligent Order Management provider ecosystem.

There are two types of providers: first-party and third-party. First-party providers are for connecting with Microsoft apps, such as Dynamics 365 Supply Chain Management, Dynamics 365 Commerce, or Dynamics 365 Finance. Services that ship with Intelligent Order Management are also implemented as a provider and are used to communicate between the fulfillment optimization service and the Inventory Visibility service.

Third-party providers are for services that Microsoft doesn't ship. Customers can use them to integrate Intelligent Order Management with different capabilities in e-commerce platforms and fulfillment and logistics systems.

For more information, see [Work with providers](work-providers.md).

### Orchestration

Intelligent Order Management enables the business user to directly change order flows, so they don't need to have much reliance on their IT administrator. The supply chain team can leverage the embedded policy designer to design the rules to optimize their business processes.

The supply chain team can use the journey orchestration designer tools to model and automate the response to fulfillment constraints and leverage machine learning to influence and optimize the flow of the order. If an organization predicts or detects constraints in their fulfillment network, the journey orchestration designer tools can help them proactively overcome the bottlenecks and drive efficiencies across the supply chain.

Organizations can scale during peak order volumes by supporting various order intake, fulfillment, and delivery partners using pre-built connectors. The order orchestration engine is built on Microsoft Power Platform, which has more than 200 pre-built connectors, allowing business users to easily connect into this ecosystem. Microsoft will continue to grow the ecosystem of connectors by working with external design partners.

### Inventory visibility service

Intelligent Order Management ships with an integrated real-time inventory visibility service that is highly scalable and extensible, providing a single, global view of the inventory positions across all legal entities.

The fulfillment orchestration engine uses real-time inventory data to optimize fulfillment and ensure optimal stock levels across the channel.

### Fulfillment optimization

Intelligent Order Management ships with a fulfillment optimization service that allows users to define different fulfillment strategies. They act as an engine through the orchestration process to determine the best location to fulfill an order from.

### Insights

Intelligent Order Management ships with Power BI dashboards to provide visibility to order and fulfillment metrics, helping to manage the order processes. The pre-built dashboards can be extended using the Power BI tools and data stored in Dataverse.

## Additional resources

[Work with providers](work-providers.md)

[Overview video](https://www.youtube.com/watch?v=X73HzFPrBb0&feature=youtu.be)

[Adapt quickly and fulfill efficiently with Dynamics 365 Intelligent Order Management - Microsoft Dynamics 365 blog](https://cloudblogs.microsoft.com/dynamics365/bdm/2021/03/02/adapt-quickly-and-fulfill-efficiently-with-dynamics-365-intelligent-order-management/)
