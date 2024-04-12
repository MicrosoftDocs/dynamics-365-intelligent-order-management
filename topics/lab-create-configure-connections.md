---
author: josaw1
description: This topic describes the steps required to create and configure connections in Microsoft Dynamics 365 Intelligent Order Management.
ms.date: 04/12/2024
ms.custom: 
  - bap-template
ms.topic: how-to
ms.author: josaw

title: Create and configure connections

---

# Create and configure connections

[!include [banner](includes/banner.md)]

This topic describes the steps required to create and configure connections in Microsoft Dynamics 365 Intelligent Order Management.

## Create platform Power Automate connections

Navigate to https://us.flow.microsoft.com/ and ensure you are in the right Intelligent Order Management trial environment. To confirm which environment you are in, select the **Environment** icon on the top right corner of the Power Automate portal.

### Create Dataverse connection

To create the Dataverse connection, follow these steps.

1. Go to **Data \> Connections**.
1. Select **New connection**.
1. In the search box on the upper right corner, enter "Dataverse".
1. Select the plus symbol "**+**" to create the Dataverse connection. When prompted to sign in, make sure to use the same credentials you used to sign in to Intelligent Order Management.

### Create Power Automate connection

To create the Power Automate connection, follow these steps.

1. Go to **Data \> Connections**.
1. Select **New connection**.
1. In the search box on the upper right corner, enter "Power Automate Management".
1. Select the plus symbol "**+**" to create the Power Automate connection. When prompted to sign in, make sure to use the same credentials you used to sign in to Intelligent Order Management.

## Configure platform connection references

> [!NOTE]
> You will need to configure three platform Dataverse connection references, but you can use the same Dataverse connection created previously for all three.

To configure platform connection references, follow these steps.

1.	On the Intelligent Order Management **Welcome and get started** screen, select **Configure settings \> Manage**.
1.	For each connection reference, do the following:
    1. Select the connection reference.
    1. Go to the [Power Automate portal](https://powerautomate.microsoft.com/). 
    1. To retrieve the connection URL, select the corresponding connection to navigate to that specific connection page, and then copy the URL. For example, if you are setting up the Intelligent Order Management Data Transformer, you need to select the **IOM Data Transformer** connection on the Power Automate connection page and then copy the Intelligent Order Management Data Transformer connection page URL from your browser's address bar.
    1. Return to the corresponding Intelligent Order Management platform connection reference page and paste the copied URL into the **Connection URL** field.
1. Select **Activate System**. 

Next quick start lab step: [Create provider solution](lab-create-provider-solution.md)
