---
author: josaw1
description: 
ms.service: dynamics-365-intelligent-order-management
ms.date: 09/01/2021
ms.topic: how-to
ms.author: josaw

title: Onboard provider instance

---

# Onboard provider instance

[!include [banner](includes/banner.md)]

If you followed the previous provider creation steps you can skip this section, since you have already created these application connections.

## Create application connections

### Create Outlook connection

1. Select **New connection**.
1. In the search box on the upper right corner, enter "Outlook.com."
1. Select the plus symbol ("**+**") to create the connection.
1. Sign in with your Outlook credentials (user name and password), which are not related to your IOM credentials.

### Create RequestBin connection

1. Select **New connection**.
1. In the search box on the upper right corner, enter "requestbin."
1. Select the plus symbol ("**+**") to create the connection.

## Add provider – order intake

1. Go to **Providers \> Catalog** and select **Add Provider** on the **IOMLabOrderIntakeProvider** tile.
1. Under the **Connections** section, select **Microsoft Dataverse** to navigate to the **IOM Provider Connection Reference** form.
1. Very similar to how platform connection references are set up, we need to set up connection reference to corresponding Power Automate connections created in previous steps. 
1. Copy the connection URL from the Dataverse Power Automate connection and paste it into the **Connection URL** field. 
1. On the **IOM Provider Connection Reference** form: 
    1. Select **Save**. 
    1. Select **Activate**.
    1. Select **Save and close**.
1. Under the **Connections** section on the IOM provider form, select **Outlook.com**.
1. Copy the Outlook.com connection URL from the corresponding Power Automate connection details page and paste it into the **Connection URL** field.
1. On the **IOM Provider Connection Reference** form: 
    1. Select **Save**. 
    1. Select **Activate**.
    1. Select **Save and close**.
1. On the IOM provider form, select **Activate**. This action deploys the Power Automate flow that processes the incoming email with order attachment.

## Add provider – fulfillment 

1. Go to **Providers \> Catalog** and select **Add Provider** on the **IOMLabFulfillmentProvider** tile.
1. Under the **Connections** section, set up all the connections listed. 
1. On the **Parameters** tab, enter the email account where you want the fulfillment order payload to be sent to. This can be any valid email address. 
1. On the **IOMLabFulfillmentProvider** form: 
    1. Select **Save**. 
    1. Select **Activate**.
    1. Select **Save and close**.

## View the deployed Power Automate component

1. Go to the maker portal at https://make.powerapps.com/ and make sure you are in the right IOM trial environment. To check which environment you are in, select **Environment** icon on the top right corner of the maker portal.
1. Go to **Solutions \> Default Solution**. 
1. Filter the solution component to display only cloud flows. You should now see the following Power Automate flows.

![Power Automate cloud flows in Intelligent Order Management](./media/power-automate-cloud-flows-3.PNG)

