---
author: v-chgri
description: This article describes how to orchestrate orders by using the Intelligent Fulfillment Optimization provider in Microsoft Dynamics 365 Intelligent Order Management.
ms.date: 08/02/2021
ms.topic: conceptual
ms.author: josaw

title: Set up the Intelligent Fulfillment Optimization provider

---

# Set up the Intelligent Fulfillment Optimization provider

[!include [banner](includes/banner.md)]

This topic describes how to set up the Intelligent Fulfillment Optimization provider in Microsoft Dynamics 365 Intelligent Order Management. For information about Intelligent Fulfillment Optimization, see [Intelligent Fulfillment Optimization](ifo.md).

> [!NOTE]
> To orchestrate orders by using the Intelligent Fulfillment Optimization provider, you must use external fulfillment optimization providers to bring orders into the system.

## Add the Intelligent Fulfillment Optimization provider

1. In Intelligent Order Management, go to **Providers \> Catalog**.
2. On the **Intelligent Fulfillment Optimization** tile, select **Add Provider**.
3. On the **Terms and Conditions** page, select **Create**.
4. On the **Connections** page, select **Intelligent Fulfillment Optimization Dataverse (current environment) Connection**.
5. You should have previously created a Dataverse connection in Power Automate by following the instructions in [Create connections](setup.md#create-connections). Go to the [Power Automate portal](https://flow.microsoft.com/), and copy the URL as described in [Set up platform connection references](setup.md#set-up-platform-connection-references).
6. On the **Intelligent Fulfillment Optimization Dataverse Connection** reference page, in the **Connection URL** field, paste the copied URL.
7. Select **Save**.
8. Select **Activate**.
9. Select **Save and close**.
10. On the **Intelligent Fulfillment Optimization** provider page, select **Activate**.
11. Select **Save and close**.

## Configure a provider action

Customers typically add the **Send to Intelligent Fulfillment Optimization** provider action after an order is validated. When it has been added to an orchestration flow, the **Send to Intelligent Fulfillment Optimization** tile should have the following properties.

- **Name:** Send to intelligent order fulfillment
- **Input Events:** Validation of Order Lines has Succeeded
- **Provider Action:** Send to fulfillment determination

## Additional resources

[Intelligent Fulfillment Optimization](ifo.md)

[Intelligent Fulfillment Optimization architecture](ifo-arch.md)

[Orchestration flows](orchestration-flows.md)
