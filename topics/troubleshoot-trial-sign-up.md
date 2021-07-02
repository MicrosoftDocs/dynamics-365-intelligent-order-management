---
author: v-chgri
description: This topic helps troubleshoot issues that may occur during sign up for the Microsoft Dynamics 365 Intelligent Order Management (Preview) trial.
ms.service: dynamics-365-intelligent-order-management
ms.date: 07/01/2021
ms.topic: conceptual
ms.author: josaw

title: Troubleshoot trial sign-up issues

---

# Troubleshoot trial sign-up issues

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic helps you troubleshoot issues that may occur during sign up for the Microsoft Dynamics 365 Intelligent Order Management (Preview) trial.

If you are signing up for the Dynamics 365 Intelligent Order Management (Preview) trial but are seeing error messages like those listed below, this topic provides some possible workarounds.

"You're already signed up for this subscription with \_______"

"You are not a member of this organization"

The purpose of a preview trial is to test in public and incorporate feedback improvements into later updates. The Commerce team will continue to monitor trial feedback and provide updated instructions as needed.

## Sign-in issues

If you're seeing an authentication issue during sign-in with the message "Sign in required - Please select sign in to continue," try the following workarounds.

- Start your browser session in a private window.
- Clear your browser session cookies.
- Start your browser session using an alternate browser. A browser-specific cache issue is currently being investigated.

## Account and tenant license issues

You may experience account and tenant license issues, depending on your account setup. The trial experience is only supported for trial subscriptions created during the sign-up process when a new account is created.

If you sign up with an account that is related to an existing tenant, you will experience issues if you are not the administrator of the tenant and you won't be able to deploy the trial environment. For more information on what a tenant is, see [What is a tenant](https://powerbi.microsoft.com/blog/what-is-a-tenant/).

If your tenant has a Dynamics 365 Customer Engagement (CE) license already associated with it, you may run into issues deploying your trial. The best way to move forward is to create a new tenant.

To create a new tenant, follow these steps.

1. Open a new private window in your browser.
1. Go to https://dynamics.microsoft.com/intelligent-order-management.
1. Select **Start free trial**.
1. In the **Email** field, enter your email address.
1. Select **Create a new account instead** and enter the requested information. For more information, see [Dynamics 365 Intelligent Order Management (Preview) release](https://community.dynamics.com/365/dynamics-365-intelligent-order-management/b/dynamics-365-intelligent-order-management-blog/posts/dynamics-365-intelligent-order-management-preview-release).
1. After creating your new account, you'll have a new free tenant and will automatically be the administrator of the tenant.

For more information, see [Deployment](deploy.md).

If the sign-up issue persists after creating a new tenant, try to deploy the environment directly from the Power Platform admin center by following these steps:

1. Go to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/environments).
1. Select **+ New**.
1. In the **New environment** dialog box, for **Name** enter your name.
1. For **Type**, select **Trial**.
1. Select **Next**.
1. In the **Add database** dialog box, do the following: 
    1. For **Language**, select **English**. English is the only language supported in the trial. 
    1. For **URL**, enter a domain name URL. If you don't enter a domain name URL, one will be created for you. 
    1. Select **Yes** for the **Enable Dynamics 365 Apps** option. 
    1. From the **Automatically deploy these apps** drop-down menu, select **Intelligent Order Management**. 
    1. Select **Save** to start the process of deploying your environment, which will take a few minutes.
1. Once deployment is completed, on the **Environments** page you will see the state of your environment as **Ready**. Once your environment is ready, select the environment name you created.
1. Under **Details**, select the URL to launch the environment.
1. Select the **Intelligent Order Management** application.

## Check your geographies and regions

Another common issue is that you may run into errors if you have mismatched regions.

The region you selected when you created your tenant must match the region you select when you sign up for the trial. For example, if you selected Europe as your region during tenant creation, you cannot select United States as your region when deploying your trial.

> [!NOTE] 
> There have been some reported issues deploying environments in Canada, so it is suggested that you deploy your environment in another region.
