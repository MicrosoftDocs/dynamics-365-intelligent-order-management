---
author: anush6121 
description: This article describes the email capabilities available in Microsoft Dynamics 365 Intelligent Order Management.
ms.date: 06/09/2022
ms.topic: 
ms.author: anvenkat

title: Email capabilities in Dynamics 365 Intelligent Order Management
---

# Email capabilities in Dynamics 365 Intelligent Order Management

This article describes the email capabilities available in Microsoft Dynamics 365 Intelligent Order Management.

Dynamics 365 intelligent order management supports the following out-of-the-box email capabilities:

- Rich and enhanced email template editor.
- Three email templates that can be called within the orchestration flow.
- High performant and scalable email sending service.
- Generic email domain that can be used in the "from" segment of the email address.

## Rich and enhanced email template editor

Many of the email template editor features are shared with the Microsoft Dynamics 365 Marketing application. A personalization editor with predefined tokens that is part of the email editor was created specifically for Intelligent Order Management use cases.

For more information, see [Email marketing overview](/dynamics365/marketing/prepare-marketing-emails). 

### Enable the email capability with enhanced editor feature

To enable the email capability with enhanced editor feature, follow these steps.

1. Sign in into the [Power Apps portals admin center](/power-apps/maker/portals/admin/admin-overview#open-power-apps-portals-admin-center) for your enviroment. 
1. Go to **Solutions \> Default Solution**. Ensure that **Solution preview on** is turned on.
1. Under **Default Solution**, navigate to the **Show Email Preview** setting.
1. Ensure that the **Default value** option set to **Yes**.  
    > [!NOTE]
    > If you set the **Default value** option back to **No**, the platform email capabilities missing some of the key email editor enhancements will be turned on instead of the enhanced editor feature. Also, the orchestration flow would need to be changed to use the older templates.
1. Go to **Setting environment value**, select **+ Add existing value**, select **Yes**, and then select **Save**.

## Out-of-the-box email templates

There are three out-of-the-box email templates that are shipped with the product:

- **Order Confirmation**: The email communication sent to a customer after an order is received in the application.
- **Shipment confirmation**: The email communication containing tracking information sent to a customer after order items are shipped.
- **Return pick up confirmation**: The email communication sent to a customer after a returns process has started.

To access the email templates, go to **Intelligent Order Management \> Configurations \> Communications \> Email templates**.

The templates above can be edited for your own business needs. It is recommended that for each template you use, you create a new template and then copy the contents from the relevant out-of-the-box template into it, save it, and then customize it. This will avoid any upgrade issues with future Intelligent Order Management solutions.

### Sections within an email template

#### Image placeholders

There are a few image placeholders in the out of the box email template and they are as follows:

- **P1**: Brand logo 
- **P2, P3, P4, P5**: Social media logos that you can use as needed

> [!NOTE]
> The current version of Intelligent Order Management does not come with image support. Images must be stored in a content distribution network (CDN) of your choice and publicly accessed via the internet. Image support is in development for an upcoming release.

#### Predefined tokens

There are a number of predefined tokens that are released out-of-the-box to support the three standard templates within Dynamics 365 Intelligent Order Management. The entire token list can be found by selecting **Personalization** within the template. By hovering over each of the tokens, you can also find the **Source**, **Data type**, and **Default value** for each token. 

### Copy and create a new order confirmation template

To copy and create a new order confirmation template, follow these steps.

1. Open the order confirmation template and copy the HTML content. Select **</> HTML** to get the content to copy.
1. After copying and while you are on this page, press F12 on your key board which opens the developer tools. Then open **Console** and execute the following command. 
var placeholders = Xrm.Page.getAttribute('msdyn_placeholders').getValue()
By doing this you are copying the tokens and placeholders from the template.
1. Go to **+New** and create a new email template and name it as you desire and save.
1. On the new template, go to **</>HTML** and paste the HTML content we copied in the step 2. Now close the HTML window and save the template.
1. In the developer tools window (we opened in step 2) run the following command in the console:
 Xrm.Page.getAttribute('msdyn_placeholders').setValue(placeholdersStr)
1. Once run, your new template is similar to the out of the box one and you are free to edit it.

We are working towards an easier solution for copy and create a template in the upcoming releases. Stay tuned to this page for more updates on this topic.

### Send emails through orchestration flow

#### Activate Dynamics 365 Communication provider

To activate the Dynamics 365 Communication provider, follow these steps.

1. Go to **Intelligent Order Management \> Providers \> Catalog \> Dynamics 365 Communication** and select **Create**.
1. Go to **Connections** and select **Communications Dataverse (current enviroment) Connection**.
1. Select **Save**, select **Activate**, and then select **Save and close**.
1. Select **Parameters** and enter the "from" email address in **value** field. (See note below.)
  
> [!NOTE]
> The "from" email address domain (the part that comes after the "@" symbol) should always be `d365iom.com`. The text that appears before "@" symbol can be any text. But recommendation is to have your company or brand name added to it, for example `support_<your brand name>@d65iom.com` or `admin_<your brand name>@d365iom.com` or `noreply_<your brand name>@d365iom.com`.

#### Add order confirmation template to an orchestration flow

To add an order confirmation template to an orchestration flow, follow these steps.

1. Add **Send email** in the orchestration flow and provide a **Name** for the tile.
1. Under **Email Template**, select the **Order Confirmation** email template.
1. Select **Send Email for Sales Order**, since the order confirmation email will be generated from sales order. For a shipment confirmation template, you would select **Send Email for Fulfillment Order Line**, and for a returns order process you would select **Send Email for Return Order**.
1. For **Input Events**, select **Validation of Order lines has Succeeded**. An input event indicates when the email should be invoked and can change based on how the orchestration is set up and how the email will be sent.

## Check email delivery status

You can check email delivery status in the sales order **Orchestration Step Results** within the sales order view. There should be an orchestration step corresponding to email delivery that will show the delivery status in **Result** column. Further details can be found in **Result Details** column.






