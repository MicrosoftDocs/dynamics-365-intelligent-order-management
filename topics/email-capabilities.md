---
author: anush6121 
description: This article describes the email capabilities available in Microsoft Dynamics 365 Intelligent Order Management.
ms.date: 06/16/2022
ms.topic: 
ms.author: anvenkat

title: Email capabilities in Dynamics 365 Intelligent Order Management
---

# Email capabilities in Dynamics 365 Intelligent Order Management

This article describes the email capabilities available in Microsoft Dynamics 365 Intelligent Order Management.

Dynamics 365 Intelligent Order Management supports the following out-of-the-box email capabilities:

- An enhanced email template editor.
- Three email templates that can be called within the orchestration flow.
- A high performant and scalable email sending service.
- A generic email domain that can be used in the "from" segment of the email address.

## Enhanced email template editor

Many of the email template editor features are shared with the Microsoft Dynamics 365 Marketing application. The personalization editor component with predefined tokens was created specifically for Intelligent Order Management.

For more information, see [Email marketing overview](/dynamics365/marketing/prepare-marketing-emails). 

### Enable the enhanced email template editor feature

To enable the enhanced email template editor feature, follow these steps.

1. Sign in into the [Power Apps portals admin center](/power-apps/maker/portals/admin/admin-overview#open-power-apps-portals-admin-center) for your environment. 
1. Go to **Solutions \> Default Solution**. Ensure that **Solution preview on** is turned on.
1. Under **Default Solution**, navigate to the **Show Email Preview** setting.
1. Ensure that the **Default value** option set to **Yes**.  
    > [!NOTE]
    > If you set the **Default value** option back to **No**, the platform email capabilities will be missing some of the key email editor enhancements of the enhanced editor feature. Also, the orchestration flow will need to be changed to use the older templates.
1. Go to **Setting environment value**, select **+ Add existing value**, select **Yes**, and then select **Save**.

## Out-of-the-box email templates

There are three out-of-the-box email templates that are shipped with the product:

- **Order Confirmation**: The email communication sent to a customer after an order is received in the application.
- **Shipment confirmation**: The email communication containing tracking information sent to a customer after order items are shipped.
- **Return pick up confirmation**: The email communication sent to a customer after a returns process has started.

To access the email templates, go to **Intelligent Order Management \> Configurations \> Communications \> Email templates**.

The templates above can be edited for your own business needs. It is recommended that for each template you use, you create a new template copy the contents of the relevant out-of-the-box template into it, save it, and then customize it. This will avoid any issues with future Intelligent Order Management upgrades.

### Sections within an email template

#### Image placeholders

There are a few image placeholders in the out-of-the-box email templates:

- **P1**: For a brand logo.
- **P2, P3, P4, P5**: For social media logos, as needed.

> [!NOTE]
> The current version of Intelligent Order Management does not come with image support. Images must be stored in a content distribution network (CDN) of your choice and publicly accessed via the internet. Image support is in development for an upcoming release.

#### Predefined tokens

There are a number of predefined tokens that are released out-of-the-box to support the three standard templates within Dynamics 365 Intelligent Order Management. The entire token list can be found by selecting **Personalization** within the template. By hovering over each of the tokens, you can also find the **Source**, **Data type**, and **Default value** values for each token. 

### Copy and create a new order confirmation template

To copy and create a new order confirmation template, follow these steps.

1. Go to **Intelligent Order Management \> Configurations \> Communications \> Email templates** and open the order confirmation template.
1. Select **</> HTML** on the top right and copy the HTML content from the **HTML** window.
1. Select F12 on your keyboard to open developer tools in your browser.  
1. Open **Console** and run the following command to copy the tokens and placeholders from the template:

    ```JavaScript
    var placeholders = Xrm.Page.getAttribute('msdyn_placeholders').getValue()
    ```

1. Select **+New** to create a new email template, name the template, and then save it.
1. In the new template, select **</>HTML** on the top right and then paste the HTML content copied in step 2 into the **HTML** window. 
1. Close the **HTML** window and save the template.
1. In the **Console** section of the developer tools window, run the following command:

    ```JavaScript
    Xrm.Page.getAttribute('msdyn_placeholders').setValue(placeholdersStr)
    ```

1. Once you run the command, your new custom template will be similar to the out-of-the-box version and you will be able to edit it.

The Intelligent Order Management team is working towards an easier solution to copy and create a template in upcoming releases.

### Send emails through orchestration flow

To send emails through orchestration flow, you must first activate the Dynamics 365 Communication provider and then add the email template to the orchestration flow.

#### Activate Dynamics 365 Communication provider

To activate the Dynamics 365 Communication provider, follow these steps.

1. Go to **Intelligent Order Management \> Providers \> Catalog \> Dynamics 365 Communication** and select **Create**.
1. Go to **Connections** and select **Communications Dataverse (current environment) Connection**.
1. Select **Save**, select **Activate**, and then select **Save and close**.
1. Select **Parameters** and enter the "from" email address in **value** field. (See note below.)
  
> [!NOTE]
> The "from" email address domain (the part that comes after the "@" symbol) should always be `d365iom.com`. The text that appears before "@" symbol can be any text, but it is recommended that you add your company or brand name to it (for example `support_<your brand name>@d65iom.com`, `admin_<your brand name>@d365iom.com`, or `noreply_<your brand name>@d365iom.com`).

#### Add the email template to an orchestration flow

For this example, we will add the order confirmation template to an orchestration flow.

To add an order confirmation template to an orchestration flow, follow these steps.

1. Add the **Send email** tile to the orchestration flow and enter a **Name** for the tile.
1. Under **Email Template**, select the **Order Confirmation** email template.
1. Select **Send Email for Sales Order**, since the order confirmation email will be generated from sales order. Alternatively, for a shipment confirmation template you would select **Send Email for Fulfillment Order Line**, or for a returns order process you would select **Send Email for Return Order**.
1. For **Input Events**, select **Validation of Order lines has Succeeded**. An input event indicates when the email should be invoked and can change based on how the orchestration is set up and how the email will be sent.

## Check email delivery status

You can check email delivery status in the sales order **Orchestration Step Results** within the sales order view. There should be an orchestration step corresponding to email delivery that will show the delivery status in **Result** column. Further details can be found in **Result Details** column.






