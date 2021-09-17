---
author: josaw1
description: This topic describes the steps required to create and configure connections in Microsoft Dynamics 365 Intelligent Order Management.
ms.service: dynamics-365-intelligent-order-management
ms.date: 09/01/2021
ms.topic: how-to
ms.author: josaw

title: Create and configure connections

---

# Create and configure connections

[!include [banner](includes/banner.md)]

This topic describes the steps required to create and configure connections in Microsoft Dynamics 365 Intelligent Order Management.

## Create platform Power Automate connections

Navigate to https://us.flow.microsoft.com/ and ensure you are in the right IOM trial environment. To check which environment you are in, select the **Environment** icon on the top right corner of the Power Automate portal.

### Create Dataverse connection

1. Go to **Data \> Connections**.
1. Select **New connection**.
1. In the search box on the upper right corner, enter "Dataverse."
1. Select the plus symbol "**+**" to create the Dataverse connection. When prompted to sign in, make sure to use the same credentials you used to sign in to IOM.

### Create Power Automate connection

1. Go to **Data \> Connections**.
1. Select **New connection**.
1. In the search box on the upper right corner, enter "Power Automate Management."
1. Select the plus symbol "**+**" to create the Power Automate connection. When prompted to sign in, make sure to use the same credentials you used to sign in to IOM.

### Create IOM Data Transformer connection

1. Go to **Data \> Connections**.
1. Select **New connection**.
1. In the search box on the upper right corner, enter "IOM Data Transformer."
    > [!NOTE]
    > If you don’t see the connector, append ``?addConnectorHideKey=iomtransforme`` to the URL.
1. Select the plus symbol "**+**" to create the IOM Data Transformer connection. When prompted to sign in, make sure to use the same credentials you used to sign in to IOM.

## Configure platform connection references

1.	On the IOM **Welcome and get started** screen, select **Configure settings \> Manage**.
1.	For each connection reference, do the following:
    1. Select the connection reference.
    1. Go to the Power Automate portal to retrieve the connection URL. Select the corresponding connection to navigate to that specific connection page, and the copy the URL. For example, if you are setting up the IOM Data Transformer, you need to select the **IOM Data Transformer** connection on the Power Automate connection page and then copy the IOM Data Transformer connection page URL from your browser's address bar.
    1. Return to the corresponding IOM platform connection reference page and paste the copied URL into the **Connection URL** field.
    > [!NOTE]
    > There are three platform Dataverse connection references, but you can use the same Dataverse connection created previously for all three. 
1. Select **Activate System**. 

Next step: [Create provider solution](lab-create-provider-solution.md )
