---
title: "Authenticated Discovery Scans"
excerpt: ""
---
Scan template configurations now support an authentication feature for asset discovery.  Enable this authentication feature on your discovery scan templates to improve operating system, software, and service fingerprinting on target assets.
[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "Assets discovered by authenticated discovery scans **do not** count against your license."
}
[/block]
# Overview

The Security Console implements this authenticated discovery feature through a **Use Credentials** checkbox located in your scan template configuration.  When enabled, this checkbox directs the Scan Engine to attempt to authenticate to target assets using any shared or local credentials that you have included and enabled in your site configuration.

# Feature Behavior

The **Use Credentials** checkbox has the following characteristics.

## Default State

The **Use Credentials** checkbox is disabled by default.  To enable it, you must create a copy of a built-in scan template.  In most cases, you will make a copy of the **Discovery Scan** template.

## Check Type Restrictions

Although the **Use Credentials** checkbox is technically available in all scan template configurations, you can only enable it on templates that you designate with the **Asset Discovery** check type alone.  The presence of any other enabled check type (**Vulnerabilities**, **Web Spidering**, or **Policies**) makes the **Use Credentials** checkbox unclickable.  Similarly, checking any of these check types on a scan template configuration with **Use Credentials** already turned on will consequently disable the **Use Credentials** checkbox.

# How to Enable Authentication for Discovery Scans
[block:callout]
{
  "type": "warning",
  "title": "REMINDER",
  "body": "You must have credentials configured and enabled in your site configuration for this authenticated discovery feature to have any effect."
}
[/block]
**To enable authentication in a discovery scan template:**

1. In your Security Console, click the **Administration** tab in your left navigation menu.
2. In the “Scan Options” section, click **manage** next to the “Templates” label.
3. In the “Scan Templates” table, Browse to the **Discovery Scan** template entry and click the icon in the “Copy” column.
4. On the **General** tab of the “Scan Template Configuration” page, name and describe your new copy of the scan template for easy identification later.
5. Check the **Use Credentials** box.  A confirmation window appears explaining the feature’s characteristics.  Click **Yes** to confirm.
6. Click **Save** in the upper right corner of the screen when finished.
[block:callout]
{
  "type": "success",
  "title": "Authenticated discovery scanning enabled!",
  "body": "You should now have a properly configured discovery scan template that you can use for authenticated discovery scans.  Make sure to modify your site configuration and select this new template before you start your next discovery scan."
}
[/block]