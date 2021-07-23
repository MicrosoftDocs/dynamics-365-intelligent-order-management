---
author: josaw1
description: This topic provides an overview of intelligent fulfillment optimization in Microsoft Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 07/23/2021
ms.topic: conceptual
ms.author: josaw

title: Intelligent fulfillment optimization

---

# Intelligent fulfillment optimization

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic provides an overview of intelligent fulfillment optimization in Microsoft Dynamics 365 Intelligent Order Management.

Intelligent fulfillment optimization optimizes order fulfillment within a supply chain network so that products are delivered to customers in the right quantities, from the right sources, at the right time. Intelligent fulfillment optimization can minimize costs, maximize profits, and satisfy service-level requirements.  
  
In a modern supply network where product fulfillment can come from multiple channels, organizations must quickly adapt to order changes, supplier availability issues, or spikes in demand. Intelligent fulfillment optimization helps optimize order fulfillment and find the best sources for product delivery based on business objectives such as minimizing costs by determining the closest product fulfillment source possible within imposed constraints.  

Intelligent fulfillment optimization is built as an Azure microservice deployed to multiple geographies. Within each geography, intelligent fulfillment optimization is deployed to two active regions with order processing requests balanced between them. If one region becomes unavailable, it is automatically taken out of rotation and order processing then resumes in the other available region. 

Intelligent fulfillment optimization follows Azure regional pairing, where each Azure region is paired with another region within the same geography. Such region pairing results in the following benefits:

- If there is a broad outage, recovery of at least one region out of every pair is prioritized.
- Planned Azure system updates are rolled out to paired regions sequentially to minimize possible downtime.
- In most cases (with the exception of Brazil), regional pairs reside within the same geography to meet data residency requirements. 

For more information on regional pairs, see [Business continuity and disaster recovery (BCDR): Azure Paired Regions](/azure/best-practices-availability-paired-regions). 

Intelligent fulfillment optimization can be enabled as part of the order orchestration journey within Dynamics 365 Intelligent Order Management. Intelligent fulfillment optimization only optimizes orders from geographies where it is available and does not process orders from other geographies even if they are configured in the order orchestration journey. Intelligent fulfillment optimization processes orders in the same geography where the Intelligent Order Management and Microsoft Power Platform environment is set up. 

Intelligent fulfillment optimization is currently available in the United States, Europe, Australia, and Asia Pacific geographies. For support within additional geographies, please contact the Intelligent Order Management product team. 

| Intelligent Order Management / Microsoft Dataverse geography | Intelligent fulfillment optimization geography |
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

Intelligent fulfillment optimization can be enabled as part of the order orchestration journey by configuring the intelligent fulfillment optimization provider as part of the order journey. Once enabled as part of the orchestration flow, during the optimization process intelligent fulfillment optimization reads fulfillment strategy, business constraints, order information from Dataverse and immediately writes back fulfillment plans to that Dataverse environment. Intelligent fulfillment optimization ensures that data does not persist beyond the microservice order optimization stage. 
 
Intelligent fulfillment optimization uses Bing Maps to calculate the closest fulfillment source to where an order is being shipped by determining geocodes or latitude and longitude for the fulfillment source address and order shipping address. Intelligent fulfillment optimization uses Bing Maps to calculate the road distance between two addresses (geocodes). If road distance calculation is not enabled, aerial distance between the two locations is used. 

Bing Maps is a highly available, non-regional service. For more information, see [Bing Maps terms of use](https://www.microsoft.com/en-us/maps/product). 

Intelligent fulfillment optimization also uses an inventory visibility service provider to determine on-hand inventory for different products at different fulfillment sources. This feature can be enabled by configuring **use real inventory** on the fulfillment strategy and on each specific fulfillment source where inventory needs to be looked up. 

