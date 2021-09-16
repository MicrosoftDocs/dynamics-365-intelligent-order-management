---
author: josaw1
de scription: Create fulfillment provider DESCRIPTION TBD
ms.service: dynamics-365-intelligent-order-management
ms.date: 09/01/2021
ms.topic: how-to
ms.author: josaw

title: Create fulfillment provider

---

# Create fulfillment provider

[!include [banner](includes/banner.md)]

## Create new provider definition

1. Go to **Providers \> Catalog**.
1. Select **New Provider Definition**.
1. For **Display Name**, enter "IOMLabFulfillmentProvider."
1. For **Logical Name**, enter "msdyn_IOMLabFulfillmentProvider."
1. For **Description**, enter "IOM lab fulfillment provider."
1. For **Logo**, select "IOMLab.png."
1. For **Service Type**, enter "Fulfillment."
1. Select **Save and close**.

## Add provider definition to solution

1. Go to the [Power App Maker portal](https://make.powerapps.com) and navigate to the newly-created solution **IOMLabProviders**.
1. Select **Add existing\IOM Provider Definition**.
1. Select **IOMLabFulfillmentProvider** and then select **Add** to add it to the solution. 

## Create provider action – send fulfillment payload to Outlook

1. Go to the [Power App Maker portal](https://make.powerapps.com) and navigate to **Solutions**.
1. Open the **Default Solution**.
1. Select **New**.
1. Select **Cloud Flow**, and then name it "IOM Lab Send To Fulfillment (Outlook)".
1. Select the trigger type as **Manually trigger a flow."
1. Create a variable initialization action:
    - For **Name**, enter "ExecutionResult".
    - For **Type**, select **Boolean**.
    - For **Value**, enter "true".  
1. Create a second variable initialization action:
    - For **Name**, enter "ProcessedSaleOrderLines".
    - For **Type**, select **Array**.
1. Create a third variable initialization action:
    - For **Name**, enter "ProcessedFulfillmentOrderLines".
    - For **Type**, select **Array**.
1. Add a **Try** scope.
1. Within the **Try** scope, add a **perform an unbound action** action as follows:
    - **ProviderActionExecutionEventId**: Under **Dynamic content**, select **ProviderActionExecutionEventId**.
    - **PowerAutomateRunId** – Specify the following as an expression: `workflow()['run']?['name']`.
1. Add a "Get a row by ID" action as follows:
    - **Row ID** – Under **Dynamic content**, select **EntityRecordId**.
1. Add a "Send an email" action from the Outlook.com connector, as follows. There are couple of email connectors, make sure to select Outlook.com since that's the connection set up earlier.
    - On the **To** line, "placeholder@placeholder.com” is used as placeholder text. This will be replaced by a provider parameter in later steps.
    - On the **Subject** line, "name" obtained is from the **Get fulfillment order** step from **Dynamic content**.
    - For **Body**, specify the following as an expression: `outputs('Get_fulfillment_order')['body']`




## Add provider definition logic definition to the provider definition (Outlook)

1. Go to **Providers \> Catalog**.
1. Select the newly-created **IOMLabFulfillmentProvider**.
1. Select **Edit** on the menu bar. 
1. Select the **Logic definitions** tab.
1. Select **+ New IOM Provider Definition Logic Definition**.
1. For **Display Name**, enter "IOM Lab Send to Fulfillment (Outlook)."
1. For **Logical Name**, enter "msdyn_LabSentToFulfillmentOutlook."
1. For **Provider Definition**, enter "IOMLabFulfillmentProvider."
1. For **Logic Type**, enter "Provider Action."
1. For **Workflow Name**, enter "IOM Lab Send to Fulfillment (Outlook)."
1. For **Timeout Minutes**, enter "2."
1. For **Max Retry Attempts**, enter "3."
1. For **Description**, enter "IOM Lab Send to Fulfillment (Outlook)."
1. For **Action Type**, enter "Send to Fulfillment."
1. Select **Save**. This will generate a JSON representation of the message handler cloud flow and populate the **Client Data** field.
1. Replace the placeholder email with provider parameter as follows:
    1. Copy the text block in the **Client Data** field and paste it into Notepad. 
    1. In the text block, find "placeholder@placeholder.com" and replace it with "{{IOMLabOutboundFulfillmentEmail}}".
    1. Copy the modified text block back into the **Client Data** field.
    1. Select **Save and close**.
1. Select **Connections**. You should see both the **Microsoft Dataverse** and **Outlook.com** connection reference definitions listed.

## Add provider definition logic definition to IOMLabProviders solution (Outlook)

1. Go to the [Power App Maker portal](https://make.powerapps.com) and navigate to the newly-created solution **IOMLabProviders**.
1. Select **Add existing\IOM Provider Definition Logic Definition**.
1. Select **IOM Lab Send To Fulfillment (Outlook)** and then select **Add** to add it to the solution. 

## Add provider definition connection references to IOMLabProviders solution

1. Go to the [Power App Maker portal](https://make.powerapps.com) and navigate to the newly-created solution **IOMLabProviders**.
1. Select **Add existing\IOM Provider Definition Connection Reference**.
1. Select both the **Microsoft Dataverse** and **Outlook.com** provider definition connection references, and then select **Add** to add them to the solution. 

## Create provider action – send fulfillment payload to RequestBin



## Add provider definition logic definition to the provider definition (RequestBin)

1. Go to **Providers \> Catalog**.
1. Select the newly-created **IOMLabFulfillmentProvider**.
1. Select **Edit** on the menu bar. 
1. Select the **Logic definitions** tab.
1. Select **+ New IOM Provider Definition Logic Definition**.
1. For **Display Name**, enter "IOM Lab Send to Fulfillment (RequestBin)."
1. For **Logical Name**, enter "msdyn_LabSentToFulfillmentRequestBin."
1. For **Provider Definition**, enter "IOMLabFulfillmentProvider."
1. For **Logic Type**, enter "Provider Action."
1. For **Workflow Name**, enter "IOM Lab Send to Fulfillment (RequestBin)."
1. For **Timeout Minutes**, enter "2."
1. For **Max Retry Attempts**, enter "3."
1. For **Description**, enter "IOM Lab Send to Fulfillment (RequestBin)."
1. For **Action Type**, enter "Send to Fulfillment."
1. Select **Save**. This will generate a JSON representation of the message handler cloud flow and populate the **Client Data** field.
1. Select **Save and close**.
1. Select **Connections**. You should see the **Microsoft Dataverse**, **Outlook.com**, and **RequestBin** connection reference definitions listed.

## Add provider definition parameter to the provider definition

1. Select **Parameters**. 
1. Select **+ New IOM Provider Definition Parameter**.
1. For **Display Name**, enter "IOMLAbOutboundFulfillmentEmail."
1. For **Data Type**, enter "Text."
1. For **Provider Definition**, enter "IOMLabFulfillmentProvider."
1. For **Key**, enter "IOMLabOutboundFulfillmentEmail."
1. For **Logical Name**, enter "msdyn_IOMLabOutboundFulfillmentEmail."
1. For **Is Required**, enter "Yes."
1. Select **Save and close**.

## Add provider definition logic definition to IOMLabProviders solution (RequestBin)

1. Go to the [Power App Maker portal](https://make.powerapps.com) and navigate to the newly-created solution **IOMLabProviders**.
1. Select **Add existing\IOM Provider Definition Logic Definition**.
1. Select **IOM Lab Send To Fulfillment (RequestBin)** and then select **Add** to add it to the solution. 

## Add provider definition connection reference to IOMLabProviders solution

1. Go to the [Power App Maker portal](https://make.powerapps.com) and navigate to the newly-created solution **IOMLabProviders**.
1. Select **Add existing\IOM Provider Definition Connection Reference**.
1. Select **RequestBin** and then select **Add** to add it to the solution.

## Add provider definition parameter to IOMLabProviders solution

1. Go to the [Power App Maker portal](https://make.powerapps.com) and navigate to the newly-created solution **IOMLabProviders**.
1. Select **Add existing\IOM Provider Definition Parameter**.
1. Select **IOMLabOutboundFulfillmentEmail** and then select **Add** to add it to the solution.

Next step: [Export provider solution](lab-export-provider-solution.md)
