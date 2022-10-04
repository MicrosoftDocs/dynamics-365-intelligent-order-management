---
author: raybennett-msft
description: This article describes application lifecycle management (ALM) in Microsoft Dynamics 365 Intelligent Order Management, including how to move solutions from one environment to another, or package solutions for storage in source control.
ms.author: bennettray
ms.date: 10/04/2022
ms.topic: conceptual

title: Application lifecycle management for Dynamics 365 Intelligent Order Management
---

# Application lifecycle management for Dynamics 365 Intelligent Order Management

This article describes application lifecycle management (ALM) in Microsoft Dynamics 365 Intelligent Order Management, including how to move solutions from one environment to another, or package solutions for storage in source control.

The following information specifies the required setup tables to migrate data for Dynamics 365 Intelligent Order Management configurations. These setup tables require a manual step to add each entity to an unmanaged solution. After the desired entities are added, the solution can be exported via a package file that is created with the data of the entities added to the unmanaged solution. The package file can then be imported into another Intelligent Order Management environment where the data then can be activated for use. 

## Setup tables

The following table lists the required setup tables needed to migrate data for Dynamics 365 Intelligent Order Management configurations.

|**Table Name**|**Solution Location**|
|:-|:-|
|**Policy**<br>(msdyn\_iompolicy)|Intelligent Order Management Provider Integration Outbound|
|**Rule**<br>(msdyn\_iomrule)|Intelligent Order Management Provider Integration Outbound|
|**Provider Definition**<br>(msdyn\_iomproviderdefinition)|Intelligent Order Management Provider Configuration|
|**Provider**<br>(msdyn\_iomprovider)|Intelligent Order Management Provider Configuration|
|**Provider Connection Reference**<br>(msdyn\_iomproviderconnectionreference)|Intelligent Order Management Provider Configuration|
|**Provider Definition Connection Reference**<br>(msdyn\_iomproviderdefinitionconnectionref)|Intelligent Order Management Provider Configuration|
|**Provider Transformation**<br>(msdyn\_iomprovidertransformation)|Intelligent Order Management Provider Integration Base|
|**Provider Transformation Definition**<br>(msdyn\_iomproviderdefinitiontransformation)|Intelligent Order Management Provider Configuration|
|**Provider Parameter**<br>(msdyn\_iomproviderparameter)|Intelligent Order Management Provider Configuration|
|**Provider Definition Parameter**<br>(msdyn\_iomproviderdefinitionparameter)|Intelligent Order Management Provider Configuration|
|**Provider Definition Logic Definition**<br>(msdyn\_iomproviderdefinitionlogicdefinition)|Intelligent Order Management Provider Configuration |
|**Designer**<br>(msdyn\_iomdesigner)|Intelligent Order Management Designer|

### Tables required for policy rule migration

The following tables required are for policy rule migration:

- Policy
- Rule

> [!NOTE]
> When you manually add rules, the parent policies are automatically added.

### Tables required for provider migration

The following tables are required for provider migration:

- Provider Definition
- Provider
- Provider Connection
- Provider Connection Reference
- Provider Transformation
- Provider Definition Transformation 
- Provider Parameter
- Provider Definition  Parameter 

### Tables required for orchestration migration

The following tables are required for orchestration migration:

- Designer
- Policy and Rule tables
- Provider tables if orchestration has Provider Actions. 

## Add tables as solution components and export your solution from the source environment

To add tables as solution components and export your solution from the source environment, follow these steps.

1. Go to https://make.preprod.powerapps.com for your test environment, or https://make.powerapps.com for your production environment.
1. Select the appropriate environment in the upper right-hand corner.
1. In the left-side navigation pane, select **Solutions**.
1. On the **Solutions** form, set the solution preview option to **Solution preview off**. 
1. At the top left, select **+ New Solution**.
1. In the **New solution** flyout menu, do the following:Enter desired Display Name and Name.
    1. Enter values for **Display Name** and **Name**.
    1. Select any publisher.
    1. Keep the version as 1.0.0.0. This version can be increased as you export solutions, and is required to upgrade a managed solution.
    1. Select **Create**.
1. Open the new solution. 
1. On the menu bar at the top of the page, select **+Add existing**.
1. On the **Add existing tables** flyout menu, navigate to or search for a table that is required for the data migration, and then select it. The search box is located on the top right side.
1. Find and select the rest of the required setup tables, and then select **Next**.
1. Under **Selected tables**, for each table, select the **Include table metadata** checkbox.
1. Select **Add**.
1. Once existing data has been added to the solution, on the menu bar, select **Export**.
1. On the **Before you export** flyout menu, under **Publish All Changes**, select **Publish**, and then select **Next**.
1. On the **Export this solution** flyout menu, under **Export as**, select **Managed (recommended)**, and then select **Export**. This export option creates the package zip file that contains the data that was added as a solution component.
1. Wait for the export to complete, and then download your solution. The solution may download automatically, so check your local **Downloads** folder when you see the export success message with a green background.

## Import your solution into your target environment

To import your solution into your target environment, follow these steps.

1. In your target environment, within Intelligent Order Management, ensure that your orchestrations, providers, and policies are deactivated/unpublished. You must do this step for each provider, policy, and orchestration that you're importing.
1. In your maker portal (https://make.preprod.powerapps.com for your test environment, or https://make.powerapps.com for your production environment), select the target environment you want to import the solution to.
1. On the menu bar at the top of the page, select **Import**
1. Import your solution into the target environment and then (in this order) activate policies, providers, and then orchestration.
1. Once the components are activated, the flows for policy will be updated, and orchestration flows will have to be republished with the data that was imported.

## Policy and rule versioning

To provide the functionality of being able to roll back changes to a specific version for policy and rules, versioning records are created for the policy components. 

In the policy table, there are two different states of records.

- **Current** - There is only one current record for the policy.
- **Archived** - There can be many archived records depending on how many changes have occurred to the linked policy and rules.

An archived version of the policy will have appropriate rules linked based on the policy ID. The versioning record is created every time a policy is unpublished. 

The following tables highlight how the two tables are linked and how the **PolicyVersionId** column is used to group the versions that are created for a policy. The **PolicyVersionId** is populated with the policy ID of the first policy record created. The policy ID value will persist for each subsequent version created, while the **PolicyId** column will be populated a new GUID, along with a new rule created to link to that new GUID. 

|**Policy**|**Type**|
|:-|:-|
|Primary Key (PK) PolicyId|GUID|
|PolicyVersionId|GUID|
|PolicyVersionState|enum|
|PolicyVersionNumber|int|

|**Rule**|**Type**|
|:-|:-|
|Primary Key (PK) RuleId|GUID|
|Foreign Key (FK) Policy|GUID|
|RuleDefinition|string|
|AssociatedEntity|enum|
