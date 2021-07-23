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

Intelligent fulfillment optimization optimizes order fulfillment in a supply chain network, to help ensure that products are delivered to customers in the correct quantities, from the correct sources, and at the correct time. Intelligent fulfillment optimization can help minimize costs, maximize profits, and satisfy service-level requirements.

In a modern supply network, where product fulfillment can come from multiple channels, organizations must quickly adapt to order changes, supplier availability issues, or spikes in demand. Intelligent fulfillment optimization helps optimize order fulfillment and find the best sources for product delivery, based on business objectives. These business objectives might include minimizing costs by determining the closest product fulfillment source that is possible under imposed constraints.

Intelligent fulfillment optimization is built as an Azure microservice that is deployed to multiple geographies. In each geography, intelligent fulfillment optimization is deployed to two active regions, and order processing requests are balanced between those regions. If one region becomes unavailable, it's automatically taken out of rotation. Order processing then resumes in the other available region.

Intelligent fulfillment optimization follows Azure regional pairing, where each Azure region is paired with another region in the same geography. Regional pairing has the following benefits:

- If there is a broad outage, recovery of at least one region in every pair is prioritized.
- Planned Azure system updates are rolled out to paired regions sequentially to minimize possible downtime.
- In most cases (except Brazil), regional pairs reside in the same geography to meet data residency requirements.

For more information about regional pairs, see [Business continuity and disaster recovery (BCDR): Azure Paired Regions](/azure/best-practices-availability-paired-regions).

Intelligent fulfillment optimization can be enabled as part of the order orchestration journey in Dynamics 365 Intelligent Order Management. Intelligent fulfillment optimization optimizes orders only from geographies where it's available. It doesn't process orders from other geographies, even if they are configured in the order orchestration journey. Intelligent fulfillment optimization processes orders in the same geography where the Intelligent Order Management and Microsoft Power Platform environment is set up.

Intelligent fulfillment optimization is currently available in the United States, Europe, Australia, and Asia Pacific geographies. For support in other geographies, contact the Intelligent Order Management product team.

| Intelligent Order Management/Dataverse geography | Intelligent fulfillment optimization geography |
|---|---|
| United States | United States |
| Europe | Europe |
| Australia | Australia |
| Asia Pacific | Asia Pacific |
| Brazil | No order processing is done. |
| Canada | No order processing is done. |
| China | No order optimization is done. |
| France | No order optimization is done. |
| Germany | No order optimization is done. |
| India | No order optimization is done. |
| Japan | No order optimization is done. |
| Switzerland | No order optimization is done. |
| United Arab Emirates | No order optimization is done. |
| United Kingdom | No order optimization is done. |

To enable intelligent fulfillment optimization as part of the order orchestration journey, configure the intelligent fulfillment optimization provider as part of the order journey. Then, during the optimization process, intelligent fulfillment optimization reads fulfillment strategy, business constraint, and order information from Dataverse. It then immediately writes fulfillment plans back to the Dataverse environment. Intelligent fulfillment optimization ensures that data doesn't persist beyond the microservice order optimization stage.

Intelligent fulfillment optimization uses Bing Maps to calculate the fulfillment source that is closest to the address that an order is being shipped to. To do this calculation, it determines geocodes, or latitude and longitude, for the fulfillment source address and the order shipping address. Intelligent fulfillment optimization uses Bing Maps to calculate the road distance between two addresses (geocodes). If road distance calculation isn't enabled, aerial distance between the two locations is used.

Bing Maps is a highly available, non-regional service. For more information, see [Bing Maps terms of use](https://www.microsoft.com/en-us/maps/product).

Intelligent fulfillment optimization also uses an inventory visibility service provider to determine on-hand inventory for different products at different fulfillment sources. You can enable this feature by configuring **use real inventory** on the fulfillment strategy and on each specific fulfillment source where inventory must be looked up.
