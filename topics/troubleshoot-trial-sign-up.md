---
author: v-chgri
description: This topic helps troubleshoot issues that may occur during sign up for the Microsoft Dynamics 365 Intelligent Order Management (Preview) trial.
ms.service: dynamics-365-intelligent-order-management
ms.date: 06/29/2021
ms.topic: conceptual
ms.author: josaw

title: Troubleshoot your trials sign up experience

---

# Troubleshoot your trials sign up experience

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

If you are signing up for the Dynamics 365 Intelligent Order Management (Preview) trial but are getting errors messages like the ones below, this post is for you.

Here are some steps we suggest investigating to work around these issues:

## Sign-in issues

If you’re running into an authentication issue like this one:

1. Start your browser session in a private window.
1. Clear your browser session cookies.
1. We are investigating an issue that might be a browser specific cache issue. We suggest trying the sign up using an alternate browser.


## Account and Tenant license issues

The trial experience is only supported in a trial subscription which the sign-up process will create when you select to a new account during the sign up and we recommend creating a new account.

You may experience issues depending on your account setup.

If you sign-up with an account that is related to an existing tenant, you will experience issues if you are not the administrator of the tenant and won’t be able to deploy the trial. For more information on what a tenant is this blog post does a great job explaining it: [What is a Tenant](https://powerbi.microsoft.com/blog/what-is-a-tenant/)

Does your tenant have a Dynamics 365 Customer Engagement (CE) license already associated with it? If it does, you might run into issues deploying your trial. The best way to move forward is to just create a new tenant:

1. Open a new private window in your browser.
1. Navigate to https://dynamics.microsoft.com/intelligent-order-management
1. Click start free trial.
1. Provide your email.
1. Select the option to create a new account. For more information, see [Dynamics 365 Intelligent Order Management (Preview) release](https://community.dynamics.com/365/dynamics-365-intelligent-order-management/b/dynamics-365-intelligent-order-management-blog/posts/dynamics-365-intelligent-order-management-preview-release).
1. Now you’ll have a new free tenant and will automatically be the admin.

For more information, see [Deployment](deploy.md).

If the issue persists after creating a new tenant, try to deploy the environment directly from the power platform admin center:

1. Navigate to https://admin.powerplatform.microsoft.com/environments
1. From the environments list, click New.
1. In the dialog that is presented.Enter a Name.
1. For the Type, select “Trial (subscription-based)”.
1. Click Next.
1. In the next dialog: Only English is supported in trial. Enter a URL or one will be created for you. Select the option to Enable Dynamics 365 Apps. From the drop down list select “Intelligent Order Management”. Click Save to start the deployment. That will start the process of deploying your environment and this will take a few minutes.
1. Once completed you will see the State in the list is Ready.
1. Click on the environment name you created.
1. Click on the URL provided in the settings to launch the environment.
1. Select the Intelligent Order Management application.


## Check your GEOs and regions

Another common issue is that you may run into errors if you have mismatched regions:

The region you selected when you created your tenant needs to be the same as the region you select when you sign up for the trial.

For example, if you selected Europe as your region during tenant creation, you cannot select United States as your region when you’re deploying your trial.

Note: We are currently experiencing issues deploying in Canada, and suggest you deploy in another region when deploying.

The purpose of a preview trial is to test in public and take the feedback into the next updates. We’ll continue to monitor the feedback and provide updated instructions.
