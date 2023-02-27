---

title: Intelligent Fulfillment Optimization architecture
description: This topic provides an overview of the architecture for Intelligent Fulfillment Optimization in Microsoft Dynamics 365 Intelligent Order Management.
ms.date: 02/27/2023
ms.author: anvenkat
author: anush6121
ms.topic: conceptual
ms.custom: bap-template


---

# Intelligent Fulfillment Optimization architecture

[!include [banner](includes/banner.md)]


This topic provides an overview of the architecture for Intelligent Fulfillment Optimization in Microsoft Dynamics 365 Intelligent Order Management.

Intelligent Fulfillment Optimization optimizes order fulfillment in a supply chain network, to help ensure that products are delivered to customers in the correct quantities, from the correct sources, and at the correct time. Intelligent fulfillment optimization can help minimize costs, maximize profits, and satisfy service-level requirements.

In a modern supply network, where product fulfillment can come from multiple channels, organizations must quickly adapt to order changes, supplier availability issues, or spikes in demand. Intelligent Fulfillment Optimization helps optimize order fulfillment and find the best sources for product delivery, based on business objectives. These business objectives might include minimizing costs by determining the closest product fulfillment source that is possible under imposed constraints.

Intelligent Fulfillment Optimization is built as an Azure microservice that is deployed to multiple geographies. In each geography, Intelligent Fulfillment Optimization is deployed to two active regions, and order processing requests are balanced between those regions. If one region becomes unavailable, it's automatically taken out of rotation. Order processing then resumes in the other available region.

Intelligent Fulfillment Optimization follows Azure regional pairing, where each Azure region is paired with another region in the same geography. Regional pairing has the following benefits:

- If there is a broad outage, recovery of at least one region in every pair is prioritized.
- Planned Azure system updates are rolled out to paired regions sequentially to minimize possible downtime.
- In most cases (except Brazil), regional pairs reside in the same geography to meet data residency requirements.

For more information about regional pairs, see [Business continuity and disaster recovery (BCDR): Azure Paired Regions](/azure/best-practices-availability-paired-regions).

Intelligent Fulfillment Optimization can be enabled as part of the order orchestration journey in Dynamics 365 Intelligent Order Management. Intelligent Fulfillment Optimization optimizes orders only from geographies where it's available. It doesn't process orders from other geographies, even if they are configured in the order orchestration journey. Intelligent Fulfillment Optimization processes orders in the same geography where the Intelligent Order Management and Microsoft Power Platform environment is set up.

Intelligent Fulfillment Optimization is currently available in the United States, Europe, Australia, and Asia Pacific geographies. For support in other geographies, contact the Intelligent Order Management product team.

| Intelligent Order Management/Dataverse geography | Intelligent Fulfillment Optimization geography |
|---|---|
| United States | United States |
| Europe | Europe |
| Australia | Australia |
| Asia Pacific | Asia Pacific |
| Brazil | No order optimization is done. |
| Canada | No order optimization is done. |
| China | No order optimization is done. |
| France | No order optimization is done. |
| Germany | No order optimization is done. |
| India | No order optimization is done. |
| Japan | No order optimization is done. |
| Switzerland | No order optimization is done. |
| United Arab Emirates | No order optimization is done. |
| United Kingdom | No order optimization is done. |

To enable Intelligent Fulfillment Optimization as part of the order orchestration journey, configure the Intelligent Fulfillment Optimization provider as part of the order journey. Then, during the optimization process, Intelligent Fulfillment Optimization reads fulfillment strategy, business constraint, and order information from Dataverse. It then immediately writes fulfillment plans back to the Dataverse environment. Intelligent Fulfillment Optimization ensures that data doesn't persist beyond the microservice order optimization stage.

Intelligent Fulfillment Optimization uses Azure Maps to calculate the fulfillment source that is closest to the address that an order is being shipped to. To do this calculation, it determines geocodes, or latitude and longitude, for the fulfillment source address and the order shipping address. Intelligent Fulfillment Optimization uses Azure Maps to calculate the road distance between two addresses (geocodes). If road distance calculation isn't enabled, aerial distance between the two locations is used.

Azure Maps is a highly available global service and follows data residency practices for Azure.

Intelligent Fulfillment Optimization also uses an inventory visibility service provider to determine on-hand inventory for different products at different fulfillment sources. You should specify the inventory source as a prerequisite in each specific fulfillment source where inventory must be looked up.

## Additional resources

[Intelligent Fulfillment Optimization](ifo.md)

[Set up Intelligent Fulfillment Optimization provider](set-up-ifo-provider.md)

[Orchestration flows](orchestration-flows.md)
