---
author: anush6121 
description: This article describes the email capabilities available in Microsoft Dynamics 365 Intelligent Order Management.
ms.date: 06/09/2022
ms.topic: 
ms.author: anvenkat

title: Email capabilities within Dynamics 365 Intelligent order management
---

# Email capabilities within Dynamics 365 Intelligent order management

This article describes the email capabilities available in Microsoft Dynamics 365 Intelligent Order Management.

Dynamics 365 intelligent order management has released following out of the box email capabilities:

- Rich and enhanced email template editor.
- High performant and scalable email sending service.
- Out of the box generic email domain that can be used in the "from" portion of the email address.
- Three out of the box email templates that can be called within the orchestration flow.

## Rich and enhanced email template editor

Many of the email template editor features are shared with the Microsoft Dynamics 365 marketing application. As part of the email editor, a personalization editor with predefined tokens was created specifically for Intelligent Order Management use cases.

For more information, see [Email marketing overview](/dynamics365/marketing/prepare-marketing-emails). 

## Out-of-the-box email templates

There are three out-of-the-box email templates that are shipped with the product:

- **Order Confirmation**: The email communication sent to a customer after an order is received in the application.
- **Shipment confirmation**: The email communication containing tracking information sent to a customer after order items are shipped.
- **Return pick up confirmation**: The email communication sent to a customer after a returns process has started.

To access the email templates, go to **Intelligent Order Management \> Configurations \> Communications \> Email templates**.

The templates above can be edited for your own business needs. We strongly recommend creating a new template and then copy the contents from the above templates over, save and copy and work on top of it. This is to avoid any upgrade issues with the IOM solutions in the future.

## Copy and create a new order confirmation template

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

## Sections within email template

### Image placeholders

There are a few image placeholders in the out of the box email template and they are as follows:

- **P1**: Brand logo 
- **P2, P3, P4, P5**: Social media logos (that you can use as your choice)

> [!NOTE]
> The current version of Intelligent Order Management does not come with image support. Images must be stored in a content distribution network (CDN) of your choice and publicly accessed via the internet. Image support is in development for an upcoming release.

### Predefined tokens

There are a number of predefined tokens that are released out of the box to support the three standard templates and beyond within Dynamics 365 Intelligent Order Management. The entire token list can be found by selecting **Personalization** within the template. By hovering over each of the tokens, you can also find the **Source**, **Data type** and **Default value** for them. The future of emails within Intelligent Order Management entails customers to be able new tokens with no code to low code.

## Sending emails through orchestration flow

### Activate Dynamics 365 Communication provider

1. Go to **Intelligent Order Management \> Providers \> Catalog \> Dynamics 365 Communication** and select **Create**.
1. Go to **Connections** and select **Communications Dataverse (current enviroment) Connection**.
1. Select **Save**, select **Activate**, and then select **Save and close**.
1. Select **Parameters** and enter the "from" email address in **value** field. See guidelines below.
  
#### Guidelines for the "from" email address 

The "from" email address domain (the part that comes after the "@" symbol) should always be `d365iom.com`. The text that appears before "@" symbol can be any text. But recommendation is to have your company or brand name added to it, for example `support_<your brand name>@d65iom.com` or `admin_<your brand name>@d365iom.com` or `noreply_<your brand name>@d365iom.com`.

### Adding email tile as part of the orchestration flow

You can add the SendEmail tile in an new or existing flow. Here is an example of how you can add order confirmation template to an orchestration flow.

1. Add **Send email** in the orchestration flow and provide a **Name** for the tile
1. Select **Order Confirmation** email template under **Email Template**
1. Select **Send Email for Sales Order** in this example where the email is generated from sales order. For shipment confirmation template, this needs to be **Send Email for Fulfillment Order Line**  and for returns order process this needs to be  **Send Email for Return Order**
1. Select **Validation of Order lines has Succeeded** for **Input Events**. Input event indicates when the email should be invoked and could change based on how the orchestration is set up and also based on the email being sent out.

## Email delivery status

Email delivery status can be found in the sales order **Orchestration Step Results** within sales order view. There should be an orchestration step corresponding to email delivery which should show the the status in **Result** column. Further details of the result will be found in **Result Details** column.

## Email feature flag settings

The following steps ensure email capability with enhanced editor is turned on. 

1. Login into the power app admin portal for your enviroment. 
1. Goto **Solutions** and navigate to **Default Solution** . Ensure **Solution preview on** is turned on.
1. Under **Default Solution** navigate to **Show Email Preview** setting.
1. Ensure that the **Default value** is set to **Yes**. If you toggle back to **No**, please be aware that the platform email capabilities will be turned on instead which would be missing some of the key email editor enhancements. Also changing this default setting would also mean that the orchestration flow needs to be changed to use the older templates.
1. Goto **Setting environment value** , select **+ Add existing value** and choose **Yes** and **Save**




