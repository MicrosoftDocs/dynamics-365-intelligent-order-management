---
author: v-chgri
description: This article can help troubleshoot issues that occur during sign-up for the Microsoft Dynamics 365 Intelligent Order Management trial.
ms.date: 01/28/2026
ms.custom: 
  - bap-template
ms.topic: troubleshooting-general
ms.author: anvenkat
title: Troubleshoot trial sign-up issues

---

# Troubleshoot trial sign-up issues

[!include [banner](includes/banner.md)]


This article can help troubleshoot issues that occur during sign-up for the Microsoft Dynamics 365 Intelligent Order Management trial. It provides some workarounds that you can try if you receive error messages that resemble the following examples when you sign up for the trial:

- "You're already signed up for this subscription with..."
- "You are not a member of this organization"

The purpose of a preview trial is to test in public and then incorporate improvements into later updates, based on feedback. The Intelligent Order Management team will continue to monitor trial feedback and will provide updated instructions as required.

## Sign-in issues

During sign-in, you might experience an authentication issue and receive the following message: "Sign in required - Please select sign in to continue." In this case, try the following workarounds:

- Start your browser session in a private window.
- Clear cookies for your browser session.
- Start your browser session in a different browser. A browser-specific cache issue is currently being investigated.

## Account and tenant license issues

Depending on your account setup, you might experience account and tenant license issues. The trial experience is supported only for trial subscriptions that are created during the sign-up process when a new account is created.

If the account that you use to sign up is related to an existing tenant, but you aren't the administrator of that tenant, you will experience issues and won't be able to deploy the trial environment. For more information about what a tenant is, see [What is a tenant](https://powerbi.microsoft.com/blog/what-is-a-tenant/).

If a Dynamics 365 Customer Engagement license is already associated with your tenant, you might experience issues when you deploy your trial. In this case, we recommend that you create a new tenant.

To create a new tenant, follow these steps:

1. Open a new private window in your browser.
1. Go to <https://dynamics.microsoft.com/intelligent-order-management>.
1. Select **Start free trial**.
1. In the **Email** field, enter your email address.
1. Select **Create a new account instead**, and enter the requested information. For more information, see [Dynamics 365 Intelligent Order Management (Preview) release](https://community.dynamics.com/365/dynamics-365-intelligent-order-management/b/dynamics-365-intelligent-order-management-blog/posts/dynamics-365-intelligent-order-management-preview-release).

After you create your new account, you will have a new free tenant. You're automatically made the administrator of the tenant.

For more information, see [Deployment](deploy.md).

If the sign-up issue persists after you create a new tenant, try to deploy the environment directly from the Power Platform admin center by following these steps.

1. Open the [Power Platform admin center](https://admin.powerplatform.microsoft.com/environments).
1. Select **New**.
1. In the **New environment** dialog box, in the **Name** field, enter your name.
1. In the **Type** field, select **Trial**.
1. Select **Next**.
1. In the **Add database** dialog box, follow these steps:

    1. In the **Language** field, select **English**. English is the only language that is supported in the trial.
    1. In the **URL** field, enter a domain name URL. If you leave this field blank, a domain name URL will be created for you.
    1. Set the **Enable Dynamics 365 Apps** option to **Yes**.
    1. In the **Automatically deploy these apps** field, select **Intelligent Order Management**.
    1. Select **Save** to start the process of deploying your environment. Deployment will take a few minutes.

1. After deployment is completed, and the **Environments** page shows the state of your environment as **Ready**, select the environment name.
1. Under **Details**, select the URL to open the environment.
1. Select the **Intelligent Order Management** application.

## Mismatched regions

Mismatched regions are another common cause of errors.

The region that you selected when you created your tenant must match the region that you select when you sign up for the trial. For example, if you selected Europe as your region during tenant creation, you can't select United States as your region when you deploy your trial.

> [!NOTE]
> Some issues with deployment of environments in Canada have been reported. Therefore, we recommend that you deploy your environment in another region.
