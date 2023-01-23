---
author: raybennett-msft
description: This article describes how to create an environment and install Intelligent Order Management as a standalone application.
ms.author: bennettray
ms.date: 01/23/2023
ms.topic: conceptual

title: Dynamics 365 Intelligent Order Management Installation

---

# Installation

## Creating an Environment
You'll need to create an environment to install Dynamics 365 Intelligent Order Management into. If you're integrating with Dynamics 365 for Finance and Operations and have set up dual-write, it will have created an environment already for you to install Intelligent Order Management into. Once the environment is created, the instructions remain the same.

1.	Navigate to <https://admin.powerplatform.microsoft.com>
1.	On the left side menu, select Environments, and then select New
1.	Give the environment a name, ensure that the Sandbox option is selected (unless you're deploying a Production instance). Select the option to Create a Database and then hit Next.
1.	On the next screen, set your preferred options, and then turn on **Enable Dynamics 365 apps**. If you fail to select this option, you'll need to recreate the environment as the key data model for Intelligent Order Management will be missing. Intelligent Order Management isn't a default app that can be deployed, so leave that option at None unless you're an advanced user and know what other applications you'll need in this environment. Select Save when done.
1.	You'll get a message that your environment is Preparing, and the State will be PreparingInstance. 
1.	Your environment will change to the Ready state when it's complete (less than an hour)

## Installing Intelligent Order Management
You'll install Dynamics 365 Intelligent Order Management into the environment that you created.

1.	Select on the environment that you created
1.	Open Dynamics 365 Apps under Resources
1.	At the top select on Install app
1.	Find Dynamics 365 Intelligent Order Management in the list. Select it, hit Next. Agree to the Terms of Service, and select Install. Installation may take a few hours.
 
While it's installing, you can use the Refresh button to see when it has completed.

## Next Steps
Proceed with [Configuring Intelligent Order Management](setup.md)