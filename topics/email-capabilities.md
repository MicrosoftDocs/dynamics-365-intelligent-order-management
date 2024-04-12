---
author: anush6121 
description: This article describes the email capabilities that are available in Microsoft Dynamics 365 Intelligent Order Management.
ms.date: 04/12/2024
ms.custom: 
  - bap-template
ms.topic: conceptual
ms.author: anvenkat

title: Email capabilities in Dynamics 365 Intelligent Order Management
---

# Email capabilities in Dynamics 365 Intelligent Order Management

This article describes the email capabilities that are available in Microsoft Dynamics 365 Intelligent Order Management.

Dynamics 365 Intelligent Order Management supports the following out-of-box email capabilities:

- An enhanced email template editor
- Three email templates that can be called in the orchestration flow
- A highly performant and scalable email sending service
- A generic email domain that can be used in the "from" email address

## Enhanced email template editor

Many features of the email template editor are shared with the Dynamics 365 Marketing app. However, the personalization editor component that includes predefined tokens was created specifically for Intelligent Order Management.

For more information, see [Email marketing overview](/dynamics365/marketing/prepare-marketing-emails).

### Enable the enhanced email template editor feature

To enable the enhanced email template editor feature, follow these steps.

1. Sign in to the [Power Apps portals admin center](/power-apps/maker/portals/admin/admin-overview#open-power-apps-portals-admin-center) for your environment. 
1. Go to **Solutions \> Default Solution**, and ensure that **Solution preview on** is turned on.
1. Under **Default Solution**, go to the **Show Email Preview** setting.
1. Ensure that the **Default value** option is set to **Yes**.

    > [!NOTE]
    > If you set the **Default value** option back to **No**, the platform email capabilities will be missing some of the key email editor enhancements of the enhanced editor feature. In addition, the orchestration flow will have to be changed so that it uses the older templates.

1. Go to **Setting environment value**, select **Add existing value**, select **Yes**, and then select **Save**.

## Out-of-box email templates

Three out-of-box email templates are included with the product:

- **Order Confirmation** – The email communication that is sent to a customer after an order is received in the app.
- **Shipment confirmation** – The email communication that contains tracking information and is sent to a customer after order items are shipped.
- **Return pick up confirmation** – The email communication that is sent to a customer after a returns process is started.

To access the email templates, go to **Intelligent Order Management \> Configurations \> Communications \> Email templates**.

The preceding templates can be edited to meet your business needs. For each template that you use, we recommend that you create a new template, copy the contents of the relevant out-of-box template into it, save it, and then customize it. By copying and modifying out-of-box templates, you help prevent issues with future Intelligent Order Management upgrades.

### Sections in an email template

#### Image placeholders

The out-of-box templates include a few image placeholders:

- **P1** – For a brand logo.
- **P2, P3, P4, P5** – For social media logos, as needed.

> [!NOTE]
> The current version of Intelligent Order Management doesn't include image support. Images must be stored in a content distribution network (CDN) of your choice and publicly accessed via the internet. Image support is in development for an upcoming release.

#### Predefined tokens

Predefined tokens are provided out of the box to support the three standard templates in Intelligent Order Management. You can find the whole token list by selecting **Personalization** in the template. By hovering over each token, you can view the **Source**, **Data type**, and **Default value** values for it.

### Copy and create a new order confirmation template

To copy and create a new order confirmation template, follow these steps.

1. Go to **Intelligent Order Management \> Configurations \> Communications \> Email templates**, and open the order confirmation template.
1. Select **\</\> HTML** in the upper right, and then copy the HTML content from the **HTML** window.
1. Select the **F12** key on your keyboard to open your browser's developer tools.
1. In the **Console** section of the developer tools, run the following command to copy the tokens and placeholders from the template.

    ```JavaScript
    var placeholders = Xrm.Page.getAttribute('msdyn_placeholders').getValue()
    ```

1. Select **New** to create a new email template, name the template, and then save it.
1. In the new template, select **\</\>HTML** in the upper right, and then paste the HTML content that you copied in step 2 into the **HTML** window.
1. Close the **HTML** window, and save the template.
1. In the **Console** section of the developer tools, run the following command.

    ```JavaScript
    Xrm.Page.getAttribute('msdyn_placeholders').setValue(placeholdersStr)
    ```

Your new custom template will resemble the out-of-box version, and you will be able to edit it.

The Intelligent Order Management team is working toward an easier solution for copying and creating a template in upcoming releases.

### Send emails through the orchestration flow

To send emails through the orchestration flow, you must first activate the Dynamics 365 Communication provider and then add the email template to the orchestration flow.

#### Activate the Dynamics 365 Communication provider

To activate the Dynamics 365 Communication provider, follow these steps.

1. Go to **Intelligent Order Management \> Providers \> Catalog \> Dynamics 365 Communication**, and select **Create**.
1. Go to **Connections**, and select **Communications Dataverse (current environment) Connection**.
1. Select **Save**, select **Activate**, and then select **Save and close**.
1. Select **Parameters**, and then, in the **value** field, enter the "from" email address. (See the note that follows.)

    > [!NOTE]
    > The domain of the "from" email address (the part after the \@ sign) should always be `d365iom.com`. The part before the \@ sign can be any text, but we recommended that you add your company or brand name to it (for example `support_<your brand name>@d65iom.com`, `admin_<your brand name>@d365iom.com`, or `noreply_<your brand name>@d365iom.com`).

#### Add the email template to an orchestration flow

For this example, you will add the order confirmation template to an orchestration flow.

To add an order confirmation template to an orchestration flow, follow these steps.

1. Add the **Send email** tile to the orchestration flow, and then, in the **Name** field, enter a name for the tile.
1. Under **Email Template**, select the **Order Confirmation** email template.
1. Select **Send Email for Sales Order**, because the order confirmation email will be generated from sales orders for this example. Alternatively, select **Send Email for Fulfillment Order Line** for a shipment confirmation template or **Send Email for Return Order** for a returns order process.
1. In the **Input Events** field, select **Validation of Order lines has Succeeded**. An input event indicates when the email should be invoked. It can change, based on how the orchestration is configured and how the email will be sent.

## Check email delivery status

You can check the status of email delivery in **Orchestration Step Results** in the sales order view. There should be an orchestration step that corresponds to email delivery and that shows the delivery status in the **Result** column. The **Result Details** column shows more details.
