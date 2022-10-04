---
author: raybennett-msft
description: This article describes application lifecycle management (ALM) in Microsoft Dynamics 365 Intelligent Order Management, including how to move solutions from one environment to another, or package them for storage in source control.
ms.author: bennettray
ms.date: 10/04/2022
ms.topic: conceptual

title: Application lifecycle management for Dynamics 365 Intelligent Order Management
---

# Application lifecycle management for Dynamics 365 Intelligent Order Management

This article describes application lifecycle management (ALM) in Microsoft Dynamics 365 Intelligent Order Management, including how to move solutions from one environment to another, or package them for storage in source control.

The following information specifies the required tables to migrate data for Dynamics 365 Intelligent Order Management configuration. This implementation is phase one of the ALM features where these tables require a manual step to add each entity to an unmanaged solution. After the desired entities are added, the solution can be exported where a package file is created with the data of the entities added to the unmanaged solution. There the package file can be imported into another Intelligent Order Management environment where data then can be activated for use. 

## Setup Tables


|**Table Name**|**Solution Location**|
|:-|:-|
|**Policy**<br>(msdyn\_iompolicy)|Intelligent Order Management Provider Integration Outbound|
|**Rule** <br>(msdyn\_iomrule)|Intelligent Order Management Provider Integration Outbound|
|**Provider Definition** (msdyn\_iomproviderdefinition)|Intelligent Order Management Provider Configuration|
|<p>**Provider** </p><p>(msdyn\_iomprovider)</p>|Intelligent Order Management Provider Configuration|
|**Provider Connection Reference** (msdyn\_iomproviderconnectionreference)|Intelligent Order Management Provider Configuration|
|**Provider Definition Connection Reference** (msdyn\_iomproviderdefinitionconnectionref)|Intelligent Order Management Provider Configuration|
|**Provider Transformation** (msdyn\_iomprovidertransformation)|Intelligent Order Management Provider Integration Base|
|<p>**Provider Transformation Definition**</p><p>(msdyn\_iomproviderdefinitiontransformation)</p>|Intelligent Order Management Provider Configuration|
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

1. Go to <https://make.preprod.powerapps.com> for your test environment, or <https://make.powerapps.com> for your production environment.
1. Select the appropriate environment in the upper right-hand corner.

    ![Screenshot of environment selection](media/developer-alm-1.png)

1. Go to Solutions form accessible from Solutions menu on left-hand side.

    ![Screenshot of Solutions selection](media/developer-alm-2.png)

1. Turn Solution Preview off. 

    ![Screenshot showing solution preview](media/developer-alm-3.png)

1. Select **+ New Solution**.

    ![Screenshot showing new selection button](media/developer-alm-4.png)

1. Enter desired Display Name and Name.
1. Select any publisher.
1. Keep version as 1.0.0.0. This version can be increased as you export solution, and it's needed to upgrade a managed solution.

    ![Screenshot showing version and solution creation](media/developer-alm-5.png)

1. Open the Solution. 
1. On Menu bar, select “+Add existing”.

    ![Screenshot showing add existing button](media/developer-alm-6.png)

1. In the drop-down, navigate to the table that is required for the data migration. For example, needing to add the policies and rules go to the Rule table. 

    ![Screenshot showing table navigation](media/developer-alm-7.png)

1. Here you can individually select the records or check mark all records by checking the circle next to the Display Name column. 
   1. There's also a search option on the right-hand side. 
1. Select “Include table metadata” and select Add

    ![Screenshot showing table metadata](media/developer-alm-8.png)

1. Once existing data has been added to the solution, there now will be a link to the data that was added. 
1. Select Export.

    ![Screenshot showing export button](media/developer-alm-9.png)

1. Select Publish All Changes, and then select Next

    ![Screenshot showing publish changes](media/developer-alm-10.png)

1. Export as **managed.**
   1. **This export creates the package zip file which contains the data that was added as a solution component.**

    ![Screenshot showing export managed](media/developer-alm-11.png)

1. Wait for the export to complete and then download your solution. Note: it may automatically download, check your Downloads folder when you see the green bar.

    ![Screenshot showing completion of solution creation](media/developer-alm-12.png)

    ![Screenshot showing download of solution creation](media/developer-alm-13.png)

## Import your solution into your target environment

To import your solution into your target environment, follow these steps.

1. In your target environment, within Intelligent Order Management, make sure your orchestrations, providers, and policies are deactivated/unpublished. You'll need to do this step for each provider, policy and orchestration that you're importing.
1. Back in your maker portal, select your target environment like you did in the previous section, but selecting the environment you want to import the solution to.

![Screenshot showing target environment](media/developer-alm-14.png)

1. Select Import

![Screenshot showing Import](media/developer-alm-14.png)

- Import solution into environment and activate policies, providers, and then orchestration.
  1. ` `**IN that order.** 
1. Once the components are activated there the flows for policy will be updated, and orchestration flows will have republished with the data that was imported.

## Policy and rule versioning

To provide the functionality of being able to roll back changes to a specific version for policy and rules, versioning records are created for the policy components. 

In the policy table, there are two different states of records.

- **Current** - There is only one of these records for the policy.
- **Archived** - There can be many of these records depending on how many changes have occurred to the linked policy and rules.

An archived version of the policy will have appropriate rules linked based on the Policy ID. The versioning record will be created every time a policy is unpublished. The below tables highlight how the two tables are linked and how the **PolicyVersionId** column will be used to group the versions that are created for a policy. The PolicyVersionId will be populated with PolicyId of the first Policy record created. That value will stay for each subsequent version created while the PolicyId column will have a new Guid populated along with a new rule created linked to that new Guid. 


|**Policy**|**Type**|
|:-|:-|
|**PK** PolicyId|Guid|
|PolicyVersionId|Guid|
|PolicyVersionState|enum|
|PolicyVersionNumber|int|

|**Rule**|**Type**|
|:-|:-|
|**PK** RuleId|Guid|
|**FK** Policy|Guid|
|RuleDefinition|string|
|AssociatedEntity|enum|
