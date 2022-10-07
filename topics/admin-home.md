---
author: sumanic
description: This topic describes the Admin home workspace in Microsoft Dynamics 365 Intelligent Order Management.
ms.date: 10/07/2022
ms.topic: conceptual
ms.author: sumanic

title: Admin home workspace

---

# Admin home workspace

[!include [banner](includes/banner.md)]

This topic describes the **Admin home** workspace in Microsoft Dynamics 365 Intelligent Order Management.

The Intelligent Order Management **Admin home** administrator workspace makes all levels of Intelligent Order Management-related setups and settings easily accessible and available to administrators. Access to **Admin home** can be role-based according to customer needs.

To access the **Admin home** workspace, on the Intelligent Order Management **Home** page, select **Settings**, and then in the left navigation pane, select **Admin home**. 

![Access Admin home from the home page](media/adminhome.png)

Alternatively, at the bottom of the left navigation pane, select **Intelligent Order Management \> Settings** to change the workspace area, and then select **Admin home**.

![Admin home page with Settings highlighted](media/adminchangearea.png)

The **Admin home** workspace contains shortcuts to settings for key areas of Intelligent Order Management. All detailed settings and their subareas are available to access in the left navigation pane.

## Key settings areas of the Admin home navigation pane

The **Admin home** left navigation pane menu groups all of the different admin settings into one area. The following table lists the key settings areas and their descriptions.

| Area | Description |
|-------------------------|-------------------------|
| **App settings** | This area primarily focuses on enabling or disabling feature controls. |
| **Insight settings** | This area allows you to toggle Power BI Insights on or off. |
| **Communication settings** | This area allows you to configure settings associated with Teams or Email communications. |
| **Provider settings** | This area allows you to set up your provider connections and integrate with your partner systems.|
| **Orchestration settings** | This area allows you to define order journeys for your customer orders. |
| **Data settings** | This area allows you to configure any form of data mappings that enable smooth integration with your providers. |
| **Order settings** | This area allows you to configure settings related to orders, fulfillments, warehouses, and carriers. |
| **Inventory settings** | This area allows you to define your inventory measures and use them for inventory transaction updates. |

### Settings subareas

Each settings area in the left navigation pane is further broken down into settings subareas. The following table lists the setting subarea elements along with their related components and descriptions.

| Area  | Subarea | Components and descriptions |
| ----  |----------------|------------|
| **App settings**  | **General app settings**  | <ul><li>**Order Handling Preferences**: This setting allows you to turn on or off key order management capabilities like **Backorders**, **Subscriptions**, **Substitutions**, **Write-In products**, and **Replacements**.</li><li>**Feature version control** : This setting allows you to switch back to an older version of certain app pages based on your preferences. It includes **Enhanced Email**, **Enhanced pages**. </li><li>**Integration keys**: This setting allows you to maintain any keys associated with your app.</li></ul>
| **Insight settings**   | **Power BI settings** | This setting allows you to turn on or off your **Insights** dashboards. |
|  **Communication settings**  | **Teams settings** | This setting allows you to turn on or off collaboration, chat, and email functionality. </p> <ul><li>**Microsoft Teams collaboration and chat**: You can enable enhanced Microsoft Teams integrations, linking of records to Microsoft Teams channels, and confidential labels in this subarea.</li></ul> |
|   | **Email settings** | Using this space, you can manage different email templates that are provided out of the box as well as define your own.|
| **Provider settings**   | **Library** | This space contains a gallery of providers from which you can install them and add their connections.|
|   | **Installed** | This subarea displays the providers that you've successfully installed and activated. It also shows you the list of providers that are inactive and awaiting completion.|
|   | **Additional settings** | This subarea of admin space caters to additional setting required to make a provider work end-to-end. Below are its components: </p> <ul><li> **Transformations**: This section allows you to add power queries to enable communication between external system data in the app.</li><li>**Mapping groups**: This setting allows you to support data shared across multiple providers.</li><li>**Actions**: This setting allows you to manage the provider functions in the form of actions in the orchestration flows.</li><li>**Action types**: This setting allows you to manage your provider actions in the form of associated functions.</li></ul>
| **Orchestration settings**   | **Order journeys** | This subarea lets you set up your order orchestration flows. These could be **order**, **returns** and **inventory** orchestrations.|
|   | **Policies** | This section allows you to set up different business rules that can be used in the orchestration flows. |
|   | **Business events** | This setup enables different **input**, **output** business events that trigger subsequent actions in the orchestration flow.|
| **Data settings** | **Mapping** | In order to be able to map data across multiple providers, this section allows you to add value maps and value map types across **Accounts**, **Contacts**, **Products**, **Price lists**, **Warehouses**, **Currencies**, **Unit groups**, and **Units**.|
|  **Order settings** | **Fulfillment settings** | This section allows you to set up all configurations associated with an order fulfillment. </p><ul><li>**Strategies**: This setting allows you to define different order fulfillment strategies and use them differently across your order fulfillments.</li><li>**Constraints**: This setting allows you to define constraints or rules to optimize fulfillment to optimize inventory latency.</li><li>**Source lists**: This setting allows you to group multiple sources into groups and use that to run strategies and constraints across a source list.</li><li>**Sources**: This setting allows you to manage multiple sources to enable multi-modal fulfillment strategies.</li><li>**Fulfillment plan**: This setting allows you to visualize the record for the optimized plan across a specific strategy and set of constraints that was generated.</li><li>**Ship via**: This setting allows you to define mode of delivery for a product.</li><li>**Terms of delivery**: This setting allows you to define delivery terms as negotiated across carrier and vendor.</li></ul> |
|   | **Sales settings** | This subarea focuses on any setups that enhance order related orchestrations. This subarea includes the following: </p><ul><li>**Split groups**: This setting allows you to define split groups that can be used to split orders across any order entities.</li><li>**Shipping carriers**: This setting allows you to define the master list of supported carriers in your order orchestration for fulfillments.</li><li>**Customer groups**: This setting allows you to define the master list of your customer groups that can be used to allocate inventory.</li></ul>|
|   | **Warehouse settings** | This subarea focuses on any setups related to your stores or distribution centers that are required to carry out transactions effectively. This subarea includes the following: </p><ul><li>**Document types**: This setting allows you to set up your document type masters like **Shipping labels**, **return labels**.</li><li>**Document specifications** : This section allows you to set up detailed specifications like document print formats.</li><li>**Fulfillment source print specifications** : This setting allows you to set up fulfillment source print specifications like what kind of labels they support and what size formats.</li><li>**Disposition codes**: This setting allows you to manage the master list of disposition codes for your returned items.</li><li>**Inspection codes**: This setting allows you to set up the master list of your inspection codes for your returned items.</li><li>**Return warehouses**: This setting allows you to set up the master list of your return warehouses across a specific city, state, and country based on the customer delivery address.</li></ul>|
| **Inventory settings**  |**Index and Reservation** | This subarea focuses on any setups associated with inventory management in Dynamics 365 Intelligent order management. Here you can set up the inventory **physical measures**, **datasources**, **allocations**, **calculated measure**. For more information on this setup, see [Inventory setup](set-up-inventory-visibility-provider.md).
