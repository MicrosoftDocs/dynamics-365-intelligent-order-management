---
author: josaw1
description: 
ms.service: dynamics-365-intelligent-order-management
ms.date: 09/01/2021
ms.topic: how-to
ms.author: josaw

title: Create intake provider

---

# Create intake provider

[!include [banner](includes/banner.md)]

## Create new provider definition

1. Go to **Providers \> Catalog**.
1. Select **New Provider Definition**.
1. For **Display Name**, enter "IOMLabOrderIntakeProvider."
1. For **Logical Name**, enter "msdyn_IOMLabOrderIntakeProvider."
1. For **Logo**, select "IOMLab.png."
1. For **Service Type**, enter "Order intake."
1. For **Description**, enter "IOM lab order intake provider."
1. Select **Save and close**.

## Add provider definition to solution

1. On the Power App Maker portal, navigate to the newly-created solution **IOMLabProviders**.
1. Select **Add existing\IOM Provider Definition**.
1. Select **IOMLabOrderIntakeProvider**, and then select **Add** to add it to the solution. 

## Add transformation to the provider definition

1. Go to **Providers \> Catalog**.
1. Select the newly-created **IOMLabOrderIntakeProvider**.
1. Select **Edit** on the menu bar. 
1. Select the **Transformations** tab.
1. Select **+ New IOM Provider Definition Transformation**.
1. For **Display Name**, enter "IOMLab Order to Dataverse Order." 
1. For **Logical Name**, enter "msdyn_IOMLabOrderIntake_Order."
1. For **Provider Definition**, enter or select **IOMLabOrderIntakeProvider**.
1. For **Source Object Name**, enter "IOMLabOrderIntakeProvider."
1. For **Destination Object Name**, enter "Dataverse Order."
1. For **Transformation**, paste in the following M query code:
```M
shared ImportMappingKey = [
    account = {
			[
				ExternalRecordKey = [ProviderName = "IOMLabOrderIntakeProvider"],
				SelectedFields = {"accountid"}
			]
    },
		pricelevel = {
			[
				ExternalRecordKey = [ProviderName = "IOMLabOrderIntakeProvider"],
				SelectedFields = {"pricelevelid"}
			]
    },
		product = List.Distinct(List.Transform(Source[orderdetails], each
			[
				ExternalRecordKey = [sku = _[sku]],
				SelectedFields = {"productid"}
			])),
		uom = List.Distinct(List.Transform(Source[orderdetails], each
			[
				ExternalRecordKey = [unit = _[unit]],
				SelectedFields = {"uomid"}
			]))
];
shared TransformSourceData =
let
	orderProducts = Source[orderdetails],
	account = IOM.MapRecord(IOM.MappingTables[account], [ProviderName = "IOMLabOrderIntakeProvider"]),
	pricelevel = IOM.MapRecord(IOM.MappingTables[pricelevel], [ProviderName = "IOMLabOrderIntakeProvider"]),
			
	orderheader = Record.FromTable
					(
						Table.SelectRows
						(
							Record.ToTable
							(
								[
									ordernumber = Text.From(Source[ordernumber]),
									name = ordernumber,
									#"customerid_account@odata.bind" = "/accounts(" & Text.From(account[accountid]) & ")",
									#"pricelevelid@odata.bind" = "/pricelevels(" & Text.From(pricelevel[pricelevelid]) & ")",
									billto_city = Record.FieldOrDefault(Source, "billtocity"),
									billto_stateorprovince = Record.FieldOrDefault(Source, "billtostateorprovince"),
									billto_country = Record.FieldOrDefault(Source, "billtocountry"),
									billto_postalcode = Record.FieldOrDefault(Source, "billtozip"),
									shipto_city = Record.FieldOrDefault(Source, "shiptocity"),
									shipto_stateorprovince = Record.FieldOrDefault(Source, "shiptostateorprovince"),
									shipto_country = Record.FieldOrDefault(Source, "shiptocountry"),
									shipto_postalcode = Record.FieldOrDefault(Source, "shiptozip")
								]
							), each [Value] <> null
						)
					),

	orderlines = List.Transform(orderProducts, each
						Record.FromTable
						(
							Table.SelectRows
							(
								Record.ToTable
								(
									[
										ispriceoverridden = true,
										#"productid@odata.bind" = "/products(" & IOM.MapRecord(IOM.MappingTables[product], [sku = Record.FieldOrDefault(_, "sku")])[productid] & ")",
										#"uomid@odata.bind" = "/uoms(" & IOM.MapRecord(IOM.MappingTables[uom], [unit = Record.FieldOrDefault(_, "unit")])[uomid] & ")",
										quantity = [quantity]
									]
								), each [Value] <> null
							)
						)
					),

	salesorder = Record.AddField(orderheader, "order_details", orderlines)

in Text.FromBinary(Json.FromValue(salesorder));

```
12. For **Transformation Source Type**, enter "JsonPayload."
13. Select **Save**.
14. Create a JSON file, paste in the following code, and save it.
```JSON
{
  "ordernumber": "IOMLabOrder001",
  "shiptocity": "BELLEVUE",
  "shiptostateorprovince": "WA",
  "shiptocountry": "US",
  "shiptozip": "98007",
  "billtocity": "BELLEVUE",
  "billtostateorprovince": "WA",
  "billtocountry": "US",
  "billtozip": "98007",
  "orderdetails": [
    {
      "sku": "883988211855",
      "unit": "each",
      "quantity": 11
    }
  ]
} 

```
15. Next to the **Sample Data** field, select **Choose File** and upload the JSON file you created.
16. Select **Save and close**.

## Add provider definition transformation to solution

1. On the Power App Maker portal, navigate to the newly-created solution **IOMLabProviders**.
1. Select **Add existing\IOM Provider Definition Transformation**.
1. Select **IOMLab Order to Dataverse Order**, and then select **Add** to add it to the solution.

## Create provider message handler

-	On Power App Maker portal, go to **Solutions** and open the **Default Solution**. 
-	Select **New**.
-	Select **Cloud Flow**, and then name it "IOM Lab Order Intake Message Request Handler."
-	Select the trigger type as **Outlook.com – When a new email arrives (V2)**, and then sign in with your outlook.com account credentials.
-	For **Folder**, select **Inbox**.
-	For **To**, select **Recipient email addresses separated by semicolons**.
-	For **CC**, select **CC recipient email addresses separated by semicolons**.
-	For **To or CC*, select **To or CC recipient email addresses separated by semicolons**.
-	For **From**, select **Sender email addresses separated by semicolons**.
-	For **Include Attachments**, select **Yes**.
-	For **Subject Filter**, select **IOMLabOrderIntakeOrder**.
-	For **Importance**, select **Any**.
-	For **Only with Attachment**, select **Yes**.
-	Select **New step** and add "parse json."
-	For **Content**, paste in the following code:
```JSON
{
"ProviderId": "00000000-0000-0000-0000-000000000000"
}
```
-	Select **Generate from sample** and paste in the following sample schema code:
```JSON
{
  "type": "object",
  "properties": {
    "ProviderID": {
      "type": "string"
    }
  }
}
```
-	Select **Done**.
-	Select the ellipsis ("**...**") and then select **Rename**. 
-	Rename the action "IOM System Properties."
-	Select **Save**.
-	Select **New step**, add "parse json", and rename to "Initialize Provider Variables."
-	For **Content**, paste in the following code:
```JSON
{
  "SourceObjectName": "IOMLab Order",
  "DestinationObjectName": "Dataverse Order"
}
``` 
- Select **Save**.
-	Select **New step**, add "initialize variable", and rename to "Initialize Processing Execution Result."
-	For **Name**, enter "ExecutionResult."
-	For **Type**, select **Boolean**.
-	For **Value**, select **true**.
- Select **Save**.
-	Select **New step**, add "scope", and rename to "Try."
-	In the **Try** scope, select **Add an action**.
-	Add "perform an unbound action" from the **Dataverse** connector and rename it "Acknowledge the Provider Message in IOM."
-	For **Action Name**, enter "msdyn_CreateProviderMessageRequestExecution."
-	For **PowerAutomateWorkflowId**, enter ``workflow()['tags']['xrmWorkflowId']`` as an expression. 
-	For **PowerAutomateRunId**, enter ``workflow()['run']?['name']`` as an expression. 
-	For **ProviderExternalRequestId**, enter ``guid()`` as an expression. 
-	Select **Save**.
-	Select **Add an action**, and then add an "apply to each" control.
-	For **Select an output from previous steps**, enter "Attachments."
-	Select **Add an action** within the **Apply to each** loop, add "run a child flow" from the **Flow** connector, and rename it "Transform Message with Power Query Online."
-	For **Provider Id**, select the **ProviderId** variable.
- For **Source Object Name**, select the **SourceObjectName** variable.
- For **Destination Object Name**, select the **DestinationObjectName** variable.
- For **Payload**, enter ``decodeBase64(items('Apply_to_each')?['ContentBytes'])`` as an expression.
- Select **Save**.
-	After the transformation step, select **Add an action**, add "run a child flow" from the Flow connector, and rename it "Create Order."
-	For **Child Flow**, enter "IOM Sales Order Creation."
-	For **Payload**, enter ``	string(json(outputs('Transform_Message_with_Power_Query_Online')?['Body']?['result'])?[0][0])`` as an expression.
-	Select **Save**.
-	Collapse the **Try** scope by selecting its title bar.
-	Select **New step**, add "scope", and rename it "Catch."
-	Select … on Catch scope, select Configure run after,
 






## Add provider definition logic definition to the provider definition


## Add provider definition logic definition to IOMLabProviders solution


## Add provider definition connection reference to IOMLabProviders solution




















