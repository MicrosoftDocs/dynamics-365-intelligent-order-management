---
author: josaw1
description: This topic provides an overview of working with providers and how to set up a provider in Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 05/17/2021
ms.topic: conceptual
ms.author: josaw

title: Work with providers

---


# Work with providers

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]


A key value proposition of Dynamics 365 Intelligent Order Management is the ability to seamlessly integrate with other systems. To do so, Intelligent Order Management uses "providers". Providers are constructs that allow you to connect Intelligent Order Management to external systems.

Intelligent Order Management includes a catalog of out-of-box providers that you can set up and customize as you need. You can also create your own provider if the catalog does not have the one you need.  


## Provider architecture

Intelligent Order Management providers were designed with the following properties:

-   Extensibility: Providers can be extended and customized by leveraging the Microsoft Power Platform.

-   Low code customization: Because providers are built on the Power Platform, customizations require little to no code.

-   Scale: Providers leverage Power Automate, so providers can scale with the volume of incoming messages.

### Components

A provider in Intelligent Order Management has the following components.

| **Component name** | **Description** | **For more information** |
|-------------------------|-------------------------|-------------------------|
| Connection | The connection component in Intelligent Order Management allows a provider to establish a connection with an external service. Each provider instance may require one or more connections that it uses to gain access and communicate with the external service. For more information, see [Learn to connect to your data using connections and on-premises data gateways.](https://docs.microsoft.com/power-automate/add-manage-connections#delete-a-connection) | <ol type="1"></br><li>Go to **Provider > Catalog** or **Provider > Installed** and select the provider you want to find the connection information for.</li></br><li>On the **Overview** tab in the **Connections** section, the dependent connections are listed.</li></br></ol> |
| Business Event | The events defined for a provider are events that the associate provider actions can raise in the orchestration designer.<br/></br><br/></br>All of the out-of-box business events in Intelligent Order Management can be applied for all providers | <ol type="1"></br><li>Go to **Provider > Catalog** or **Provider > Installed** and select the provider you want to find the business event information for.</li></br><li>On the **Event** tab, there are two sections: **Global Events** and **Provider Events**. **Global Events** are provider agnostic. The **Provider Events** section lists the provider-specific events.</li></br></ol> |
| Action | The actions associated with a provider determine what actions are available to you when you create an orchestration flow.<br/></br><br/></br>If your provider doesn't have any actions, the provider can't be invoked from the orchestration. | <ol type="1"></br><li>Go to **Provider > Catalog** or **Provider > Installed** and select the provider you want to find the action information for.</li></br><li>On the **Actions** tab, the list of all the provider-specific actions is available. The list of provider actions is also available on the **Providers > Provider Actions** page.</li></br></ol> |
| Parameter | Some providers require additional configuration information to retrieve and send information.<br/></br><br/></br>This additional information is called a provider parameter. | <ol type="1"></br><li>Go to **Provider > Catalog** or **Provider > Installed** and select the provider you want to find the parameter information for.</li></br><li>On the **Parameters** tab, the provider parameters are listed.</li></br></ol> |
| Transformation | Provider transformations are essential to any provider that retrieves or sends data from Intelligent Order Management to an external service.<br/></br><br/></br>A transformation maps data from an external service to an entity in Intelligent Order Management and from Intelligent Order Management to an external source. For more information, see [What is Power Query?](https://docs.microsoft.com/power-query/power-query-what-is-power-query) | <ol type="1"></br><li>Go to **Provider > Catalog** or **Provider > Installed** and select the provider you want to find the transformations for.</li></br><li>On the **Transformations** tab, the list of the provider-specific actions is available. The list of transformations is also available on the **Providers > Transformations** page.</li></br></ol> |



## Set up a provider 

Use the steps below to set up a provider.

1.  Go to **Providers > Catalog**.

2.  Select **Add Provider** next to the provider you want to set up.

3.  Select **Create** to accept the terms and conditions.

4.  In the **Display Name** field, enter a new name or leave the default name.

5.  For each of the connections in the **Connections** section do the following:

    1.  Select a connection.

    2.  In the **Connection URL** section, select **Retrieve Connection Link**. A connection URL is a unique URL that gets created when you [create a connection in Power Automate](https://docs.microsoft.com/power-automate/add-manage-connections).

    3.  Select **Create a connection**.

    4.  Search for your connector.

    5.  Select the connector and enter the required authentication information.

    6.  Select **Create**.

    7.  In the **Status** list, the connector will have a status of **Connected**.

    8.  Select the ellipses of the newly created connector and then select **Details.**

    9.  Copy the URL found at the top of the page.

    10. Go back to the **Connection URL** screen in Intelligent Order Management and paste the URL in the **Connection URL** field.

    11. Click **Activate** to activate the connection.

    12. Select **Save**.

    13. Repeat everything in step 5 for each the connections listed.

6.  Select **Activate** in the top ribbon.

7.  Go to **Providers > Installed** and validate that the provider you set up is listed with the status **Activated**.



## Delete a provider instance

When you delete a provider instance, the system removes any configuration you completed for that provider. None of the information you set up is saved, including the connection details, transformations, and any customizations.

Before you delete the provider instance, make sure you're not using the provider in any of your orchestration flows.

1.  Remove any related provider actions from your orchestration flows. Dependent flows will break if you delete a provider without removing the related steps.

2.  Go to **Provider > Installed**.

3.  Select the provider you want to delete and select **Delete** on the top ribbon.

4.  (Optional) If you want to remove connections to your external service in this environment, delete the connections you set up as a part of this provider in Power Automate. To remove a connection, use the steps in [Learn to connect to your data using connections and on-premises data gateways.](https://docs.microsoft.com/power-automate/add-manage-connections#delete-a-connection)



## Additional resources

[Provider catalog](provider-catalog.md)

[Customize an out-of-box provider](customize-provider.md)

[Create a new provider](create-new-provider.md)
