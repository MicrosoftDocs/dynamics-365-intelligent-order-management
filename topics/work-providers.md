---

author: sumanic
description: This topic provides an overview of working with providers and how to set up a provider in Microsoft Dynamics 365 Intelligent Order Management.
ms.date: 10/05/2022
ms.topic: conceptual
ms.author: sumanic

title: Work with providers

---

# Work with providers

[!include [banner](includes/banner.md)]

This topic provides an overview of working with providers and how to set up a provider in Microsoft Dynamics 365 Intelligent Order Management.

A key value proposition of Dynamics 365 Intelligent Order Management is the ability to seamlessly integrate with other systems. To do so, Intelligent Order Management uses *providers*. Providers are constructs that allow you to connect Intelligent Order Management to external systems.

Intelligent Order Management includes a library of out-of-the-box providers that you can set up and customize to meet your needs. You can also create your own provider if the library does not have the one you need. 

The following image shows an example of providers in the Intelligent Order Management provider library.

![Intelligent Order Management provider library](media/Providers.png)

## Provider architecture

Intelligent Order Management providers were designed with the following properties:

-   Extensibility: Providers can be extended and customized using the Microsoft Power Platform.
-   Low code customization: Because providers are built on the Power Platform, customizations require little to no code.
-   Scale: Providers use Microsoft Power Automate so they can scale up with the volume of incoming messages.

## Provider components

A provider in Intelligent Order Management has the following components.

| **Component name** | **Description** | **For more information** |
|-------------------------|-------------------------|-------------------------|
| Connection | The connection component in Intelligent Order Management allows a provider to establish a connection with an external service. Each provider instance may require one or more connections that it uses to gain access and communicate with the external service. There could be some provider instances that may not require any connections. For more information, see [Learn to connect to your data using connections and on-premises data gateways.](/power-automate/add-manage-connections#delete-a-connection) | <ol type="1"></br><li>Go to **Provider \> Library** or **Provider \> Installed** and select the provider you want to find the connection information for.</li></br><li>On the **Overview** tab in the **Connections** section, the dependent connections are listed.</li></br></ol> |
| Business Event | The events defined for a provider are events that the associate provider actions can raise in the orchestration designer.<br/></br><br/></br>All of the out-of-box business events in Intelligent Order Management can be applied for all providers | <ol type="1"></br><li>Go to **Provider \> Library** or **Provider \> Installed** and select the provider you want to find the business event information for.</li></br><li>On the **Event** tab, there are two sections: **Global Events** and **Provider Events**. **Global Events** are provider agnostic. The **Provider Events** section lists the provider-specific events.</li></br></ol> |
| Action | The actions associated with a provider determine what actions are available to you when you create an orchestration flow.<br/></br><br/></br>If your provider doesn't have any actions, the provider can't be invoked from the orchestration. | <ol type="1"></br><li>Go to **Provider > Library** or **Provider > Installed** and select the provider you want to find the action information for.</li></br><li>On the **Actions** tab, the list of all the provider-specific actions is available. The list of provider actions is also available on the **Providers \> Provider Actions** page.</li></br></ol> |
| Parameter | Some providers require additional configuration information to retrieve and send information.<br/></br><br/></br>This additional information is called a provider parameter. | <ol type="1"></br><li>Go to **Provider \> Library** or **Provider \> Installed** and select the provider you want to find the parameter information for.</li></br><li>On the **Parameters** tab, the provider parameters are listed.</li></br></ol> |
| Transformation | Provider transformations are essential to any provider that retrieves or sends data from Intelligent Order Management to an external service.<br/></br><br/></br>A transformation maps data from an external service to an entity in Intelligent Order Management and from Intelligent Order Management to an external source. For more information, see [What is Power Query?](/power-query/power-query-what-is-power-query) | <ol type="1"></br><li>Go to **Provider \> Library** or **Provider \> Installed** and select the provider you want to find the transformations for.</li></br><li>On the **Transformations** tab, the list of the provider-specific actions is available. The list of transformations is also available on the **Providers \> Transformations** page.</li></br></ol> |

## Activate one or more providers 

Use the following steps to set up one or more providers.

1. Go to **Providers \> Library**.
1. Select **Select** or select the symbol next to the provider you want to set up.
1. Select **Activate Provider** on the top right. If you want to add multiple providers, repeat step 2 for each additional provider.
1. In the wizard to add the connections, read through the **Terms and Conditions** and select the checkbox for each provider you have selected. 
1. Select **Accept** to accept the terms and conditions.
1. For the first provider, select **See details** to open the provider details page. Optionally, here you can edit the provider name or leave it as it is on the **Connection** page.
1. Scroll down to the **Connections** section to see the connections associated with that provider.
1. Next to the provider connection, select **Create**. This will open up a screen to enter the **Connection** details.

    ![image](https://user-images.githubusercontent.com/30285449/191603617-03fd413e-b65f-478d-8ab1-a70f6fa52f22.png)

1. Enter the connection details, and then select **Create**.
1. Once the connection is added, a green checkmark will appear next to it.
1. Add the **Microsoft Dataverse** connection. This should auto reference from your system connections and a **green tick** should reflect on the side.
1. Once you've successfully added the connections, select **Next**.
1. On the **Parameters** screen, add any parameters needed for this provider.
1. Select **Mapping Group**.
1. Select **Next**.
1. On the **Transformations** page that appears, review the details and make any changes that are needed.
1. Select **Next**.
1. On the **Summary** page, review the added connections and their details.
1. Select **Activate**. The message **Provider activated successfully** will appear.
1. Select **Back** to make any updates.
1. Select **Next** for any additional providers selected.
1. Repeat steps 6 through 21 for each additional provider.
1. When done configuring the providers, go to the **Review and Finish** page. 
1. Review the details and exit. The providers will show as **Installed** in gray if not activated yet, or **Activated** in green if successfully activated. 

## Delete a provider instance

When you delete a provider instance, the system removes any configuration you completed for that provider. None of the information you set up is saved, including the connection details, transformations, and any customizations.

Before you delete a provider instance, ensure that you're not using the provider in any of your orchestration flows.

To delete a provider instance, follow these steps.

1. Remove any related provider actions from your orchestration flows. Dependent flows will break if you delete a provider without removing the related steps.
1. Go to **Provider \> Installed**.
1. Select the provider you want to delete, and then on the top ribbon select **Delete**.
1. Optionally, if you want to remove connections to your external service in this environment, delete the connections you set up as a part of this provider in Power Automate. To remove a connection, follow the steps in [Learn to connect to your data using connections and on-premises data gateways.](/power-automate/add-manage-connections#delete-a-connection).

## Additional resources

[Set up an environment](setup.md)

[Provider catalog](provider-catalog.md)

[Customize an out-of-box provider](customize-provider.md)

[Create a new provider](create-new-provider.md)

[Intelligent Order Management architecture](architecture.md)
