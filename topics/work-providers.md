---
author: sumanic
description: This topic provides an overview of working with providers and how to set up a provider in Dynamics 365 Intelligent Order Management.
ms.date: 01/09/2022
ms.topic: conceptual
ms.author: sumanic

title: Work with providers

---


# Work with providers

[!include [banner](includes/banner.md)]



A key value proposition of Dynamics 365 Intelligent Order Management is the ability to seamlessly integrate with other systems. To do so, Intelligent Order Management uses "providers". Providers are constructs that allow you to connect Intelligent Order Management to external systems.

Intelligent Order Management includes a library of out-of-box providers that you can set up and customize as you need. You can also create your own provider if the library does not have the one you need. 

**Provider Library**

![Provider Catalog.](media/Providers.png)

## Provider architecture

Intelligent Order Management providers were designed with the following properties:

-   Extensibility: Providers can be extended and customized by leveraging the Microsoft Power Platform.

-   Low code customization: Because providers are built on the Power Platform, customizations require little to no code.

-   Scale: Providers leverage Power Automate, so providers can scale with the volume of incoming messages.

### Components

A provider in Intelligent Order Management has the following components.

| **Component name** | **Description** | **For more information** |
|-------------------------|-------------------------|-------------------------|
| Connection | The connection component in Intelligent Order Management allows a provider to establish a connection with an external service. Each provider instance may require one or more connections that it uses to gain access and communicate with the external service. For more information, see [Learn to connect to your data using connections and on-premises data gateways.](/power-automate/add-manage-connections#delete-a-connection) | <ol type="1"></br><li>Go to **Provider > Library** or **Provider > Installed** and select the provider you want to find the connection information for.</li></br><li>On the **Overview** tab in the **Connections** section, the dependent connections are listed.</li></br></ol> |
| Business Event | The events defined for a provider are events that the associate provider actions can raise in the orchestration designer.<br/></br><br/></br>All of the out-of-box business events in Intelligent Order Management can be applied for all providers | <ol type="1"></br><li>Go to **Provider > Library** or **Provider > Installed** and select the provider you want to find the business event information for.</li></br><li>On the **Event** tab, there are two sections: **Global Events** and **Provider Events**. **Global Events** are provider agnostic. The **Provider Events** section lists the provider-specific events.</li></br></ol> |
| Action | The actions associated with a provider determine what actions are available to you when you create an orchestration flow.<br/></br><br/></br>If your provider doesn't have any actions, the provider can't be invoked from the orchestration. | <ol type="1"></br><li>Go to **Provider > Library** or **Provider > Installed** and select the provider you want to find the action information for.</li></br><li>On the **Actions** tab, the list of all the provider-specific actions is available. The list of provider actions is also available on the **Providers > Provider Actions** page.</li></br></ol> |
| Parameter | Some providers require additional configuration information to retrieve and send information.<br/></br><br/></br>This additional information is called a provider parameter. | <ol type="1"></br><li>Go to **Provider > Library** or **Provider > Installed** and select the provider you want to find the parameter information for.</li></br><li>On the **Parameters** tab, the provider parameters are listed.</li></br></ol> |
| Transformation | Provider transformations are essential to any provider that retrieves or sends data from Intelligent Order Management to an external service.<br/></br><br/></br>A transformation maps data from an external service to an entity in Intelligent Order Management and from Intelligent Order Management to an external source. For more information, see [What is Power Query?](/power-query/power-query-what-is-power-query) | <ol type="1"></br><li>Go to **Provider > Library** or **Provider > Installed** and select the provider you want to find the transformations for.</li></br><li>On the **Transformations** tab, the list of the provider-specific actions is available. The list of transformations is also available on the **Providers > Transformations** page.</li></br></ol> |



## Set up a provider 

Use the following steps to set up a provider.

1.  Go to **Providers > Library**.

2.  Click on **Select** or click on the icon next to the provider you want to set up.

3.  If you wish to add multiple providers, then repeat step 2 for another provider and select **Activate Provider** from the top right.

4.  Once you do that, a wizard will appear to add the connections.

5.  In the **Display Name** field, enter a new name or leave the default name.
6.  Read through the **Terms and Conditions** Select the check box for each provider you have selected.
7.  Click on **Accept**.
8.  This will open up the first provider details.
9.  Scroll down into the **Connections** section.
10. You will see the Connections associated with that provider will appear.
11. Click on **Create** beside the provider connection. This will open up a screen to enter the **Connection** details.
12. Enter the details and click on **Create**.
13. Once the Connection is added, it will show a **green tick** on th side.
14. Add the **Microsoft Dataverse** connection. This should auto reference from your system connections and a **green tick** should reflect on the side.
15. Once successfully added the **Connections**, click on **Next**.
16. This will take you through the **Parameters** screen. Add any Parameters needed for this Connection.
17. Select the **Mapping Group**.
18. Click on **Next**.
19. This will open the **Transformations** page. Review for any changes needed.
20. Click on **Next**.
21. in the **Summary** page review the added **Connections** and **Details**.
22. Click on **Save**.
23. Click on **Activate**. This will show a message **Provider activated successfully**.
24. Click on **Back** button to make any updates.
25. Click on **Next** for any additional providers selected.
26. Repeat **Step 6** through **Step 24** for the next providers.
27. Finally Goto the **Review and Finish** page. 
28. Review the details and exit. The **Providers** will show **Installed** if not activate dyet and in grey or **Activated** if successful and in green. 


## Delete a provider instance

When you delete a provider instance, the system removes any configuration you completed for that provider. None of the information you set up is saved, including the connection details, transformations, and any customizations.

Before you delete the provider instance, make sure you're not using the provider in any of your orchestration flows.

1.  Remove any related provider actions from your orchestration flows. Dependent flows will break if you delete a provider without removing the related steps.

2.  Go to **Provider > Installed**.

3.  Select the provider you want to delete and select **Delete** on the top ribbon.

4.  (Optional) If you want to remove connections to your external service in this environment, delete the connections you set up as a part of this provider in Power Automate. To remove a connection, use the steps in [Learn to connect to your data using connections and on-premises data gateways.](/power-automate/add-manage-connections#delete-a-connection)



## Additional resources

[Set up an environment](setup.md)

[Provider catalog](provider-catalog.md)

[Customize an out-of-box provider](customize-provider.md)

[Create a new provider](create-new-provider.md)

[Intelligent Order Management architecture](architecture.md)
