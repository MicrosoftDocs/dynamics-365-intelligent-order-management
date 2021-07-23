---
author: josaw1
description: This topic provides an overview of Microsoft Dynamics 365 Intelligent Fulfillment Optimization.
ms.service: dynamics-365-intelligent-order-management
ms.date: 07/23/2021
ms.topic: conceptual
ms.author: josaw

title: Intelligent Fulfillment Optimization

---

# Intelligent Fulfillment Optimization

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic provides an overview of Microsoft Dynamics 365 Intelligent Fulfillment Optimization.

Dynamics 365 Intelligent Fulfillment Optimization service that maximizes orders fulfillment within the supply chain network, so that products are delivered to the customers at the right quantities, from the right sources and at the right time, to maximize profits, minimizing costs and satisfying service-level requirements.  
  
In a modern supply network where product fulfillment can be from multiple channels, organizations must adapt to order changes, supplier availability issues, or a spike in demand quickly. Distributed Order Management helps with maximizing order fulfillment and finding right source for delivery of the products based on different business objectives like minimizing costs based on fulfilling from closest sources and within constraints imposed on it.  

Intelligent Fulfillment Optimization is built as a micro service on Azure and deployed to multiple geographies. Within each geography, Intelligent Fulfillment Optimization is deployed to two regions with both regions being active, and order processing requests are load balanced between them. If one region becomes unavailable, it is taken out of rotation automatically and order processing will resume on another region that is available. 

Intelligent Fulfillment Optimization follows Azure regional pairing with each Azure region paired with another region within the same geography. It leverages the benefits of this including:
•	If there is a broad outage, recovery of at least one region out of every pair is prioritized.
•	Planned Azure system updates are rolled out to paired regions sequentially to minimize possible downtime.
•	In most cases with exception of Brazil, regional pairs reside within the same geography to meet data residency requirements. 

For more information on regional pairs, see [Business continuity and disaster recovery (BCDR): Azure Paired Regions](https://docs.microsoft.com/azure/best-practices-availability-paired-regions). 

 
Intelligent Fulfillment Optimization can be enabled as part of the order orchestration journey within Intelligent Order Management.  Intelligent Fulfillment Optimization only optimizes orders from geographies where it is available and does not process orders from other geographies even if it is configured in the Order Orchestration journey. Intelligent Fulfillment Optimization will process orders in the same geography where Intelligent Order Management and Power Platform environment is setup. 

United States, Europe, Australia, and Asia Pacific are geographies where Intelligent Fulfillment Optimization is available. For support within additional geographies, please reach out to Intelligent Order Management product team. 


| Intelligent Order Management / Dataverse Geography | Intelligent Fulfillment Optimization Geography |
|---|---|
|  United States | United States |
| Europe  | Europe |
| Australia  | Australia |
| Asia Pacific   | Asia Pacific |
| Brazil  | No order processing. |
| Canada  | No order processing. |
| China  | No order optimization. |
| France  | No order optimization. |
| Germany  | No order optimization. |
| India  | No order optimization. |
| Japan  | No order optimization. |
| Switzerland  | No order optimization. |
| United Arab Emirates  | No order optimization. |
|  United Kingdom | No order optimization. |


Intelligent Fulfillment Optimization can be enabled as part of the order orchestration journey by configuring Intelligent Fulfillment Optimization provider as part of the Order Journey.  Once it is enabled as part of orchestration flow, Intelligent Fulfillment optimization will read Fulfillment strategy, business constraints, order information during optimization process from Dataverse and immediately write back fulfillment plans to that specific Dataverse environment. Intelligent Fulfillment Optimization ensures that data is not persisted beyond the order optimization step in the micro-service. 
 
Intelligent Fulfillment Optimization uses Bing Maps to calculate closest fulfillment source to where order is being shipped. It uses Bing Maps to determine geo codes or latitude and longitude for the Fulfillment source address and shipping address on the order.  It uses Bing Maps to calculate distance between two addresses (two geocodes). If road distance calculation is not enabled, it will use aerial distance between the two locations. Otherwise, it will use road distance calculation.  

Bing Maps is a non-regional service and highly available service. Please refer to [Bing Maps terms of use](https://www.microsoft.com/en-us/maps/product) for additional information on this service. 

Intelligent Fulfillment Optimization also uses Inventory Visibility Service provider to determine inventory on-hand for different products at different fulfillment sources. This can be turned on by configuring “use real inventory” on the Fulfillment strategy and on each specific fulfillment source where inventory needs to be looked up. 

