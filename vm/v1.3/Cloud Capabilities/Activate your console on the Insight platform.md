---
title: "Activate your console on the Insight platform"
excerpt: ""
---
This article will guide you through the console activation process that enables InsightVM’s cloud capabilities.

# Insight platform overview

The Rapid7 Insight platform provides data collection, visibility, analytics, and automation to establish a shared point of view between security, IT operations, and DevOps teams. Our cloud platform delivers one-click access to Rapid7’s vulnerability management, application testing, orchestration and automation, incident detection and response, phishing analysis and simulation, and log management solutions.

You can learn more about the Insight platform in the following pages:

* https://www.rapid7.com/products/insight-platform/
* https://www.rapid7.com/trust

# InsightVM cloud capabilities

InsightVM license holders can take advantage of the following capabilities and tools that are only available through the Rapid7 Insight platform:

* [Dashboards](doc:dashboards) and [Cards](doc:cards)
* [Containers](doc:working-with-containers)
* [Insight Agents](doc:using-the-agent-with-insightvm)
* [Remediation projects](doc:remediation-workflow)
* [Automation](doc:automation)
* [Goals](doc:goals-and-slas)

# Understand different user identifications

The credentials used to access to InsightVM’s cloud capabilities are different from those used for the on-premises Security Console.  This section will help you distinguish between the two sets.

## Security Console login

The Security Console login is the username and password you use to access your console using the IP address or FQDN of the host machine.  These logins only exist within the console itself.  The following login page accepts Security Console login credentials:
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/7377b49-security_console_login.png",
        "security_console_login.png",
        458,
        532,
        "#eef0f2"
      ]
    }
  ]
}
[/block]
## insight.rapid7.com account

Unlike Security Console logins, insight.rapid7.com accounts use email addresses as the user identifier.  The following sign-in page at [insight.rapid7.com](https://insight.rapid7.com/login) accepts Insight account credentials:
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/cae033c-insight_platform_login.png",
        "insight_platform_login.png",
        830,
        824,
        "#5c6e7b"
      ]
    }
  ]
}
[/block]
At the conclusion of this activation process, your Insight account will be used to authenticate your access to InsightVM’s cloud capabilities.

# Requirements

You must meet the following general and networking requirements before you start the activation process:

* Your Security Console must be on version 6.5.29 or later.
* Your Security Console must not be already activated on the Insight platform.
* You must have [whitelisting configured](doc:configure-communications-with-the-insight-platform) for the hostname of your corresponding data region.

# Activation process

The following numbered sections guide you through the activation process.
[block:callout]
{
  "type": "danger",
  "title": "IMPORTANT",
  "body": "Before starting this procedure, ensure the Security Console’s host machine has the correct time. If the time setting on the host machine is incorrect, it may interfere with your ability to access InsightVM’s cloud capabilities.\n\nTo ensure that the system time is correct, Rapid7 recommends syncing your Security Console’s host machine with an NTP server."
}
[/block]
Choose one of the following methods to initiate the console activation wizard.

## 1a. Launch the wizard automatically

In your Security Console, click any of the following tabs on your left navigation menu to automatically start the wizard:

* **Dashboard**
* **Projects**
* **Goals and SLAs**
* **Containers**
* **Automation**
* **Management**

When the activation window appears, click **Activate Now**.
[block:callout]
{
  "type": "warning",
  "title": "I clicked one of those tabs and the wizard didn’t start.  What does that mean?",
  "body": "Your console is already activated on the Insight platform.  No further action is required."
}
[/block]
## 1b. Launch the wizard manually

Alternatively, start the wizard manually by navigating to the **Insight platform** tab of the “Security Console Configuration” screen:

1. From your left navigation menu, click the **Administration** tab.
2. In the “Global and Console settings” section, click **Administer**.
3. On the “Security Console Configuration” screen, click the **Insight platform** tab.
4. Click **Activate Console**.
5. When the activation window appears, click **Activate Now**.
[block:callout]
{
  "type": "warning",
  "title": "My Insight platform tab only shows a Deactivate Console link.  What does this mean?",
  "body": "Your console is already activated on the Insight platform.  No further action is required."
}
[/block]

[block:callout]
{
  "type": "warning",
  "title": "My Insight platform tab already shows a pairing key field.  What does this mean?",
  "body": "Someone else in your organization has already started the activation wizard.  If you need to restart the wizard, click the **Cancel console activation** link located above the pairing key field and start the process again."
}
[/block]
## 2. Determine if you already have an Insight account

The wizard prompts you to select whether or not you already have an insight.rapid7.com account.

If you **already have an Insight account**, select the corresponding option and click **Next**.  Skip ahead to the [“Sign in”](doc:activating-your-console-on-the-insight-platform#section-3-sign-in) section of this article.

If you **do not have an Insight account**, select the corresponding option and fill out the necessary form fields.  After you submit the form, look out for an email to set your password and security questions.  After you’ve completed your account setup, proceed to the [“Sign in”](doc:activating-your-console-on-the-insight-platform#section-3-sign-in) section.
[block:callout]
{
  "type": "info",
  "title": "Not sure which option applies to you?",
  "body": "Contact our [Support team](https://www.rapid7.com/contact/) for assistance."
}
[/block]

[block:callout]
{
  "type": "warning",
  "title": "What if I chose the wrong option?",
  "body": "If you submit the wrong option during this step of the wizard, you can cancel the activation process by clicking the **Cancel console activation** link on the **Insight platform** tab of the “Security Console Configuration” screen.\n\nReturn to [step 1](doc:activating-your-console-on-the-insight-platform#section-1a-launch-the-wizard-automatically) to restart the wizard."
}
[/block]
## 3. Sign in

Go to insight.rapid7.com and sign in with your Insight account credentials.  This sign-in page is meant **exclusively** for email-based Insight accounts.
[block:callout]
{
  "type": "warning",
  "title": "REMINDER",
  "body": "Your existing Security Console login **does not** apply to this sign-in page."
}
[/block]
## 4. Open your cloud instance of InsightVM

The goal of this step is to navigate to your cloud instance of InsightVM in order to retrieve your console pairing key.  A successful sign-in takes you to one of three possible views depending on your current Insight platform structure.

### InsightVM “Welcome” screen

If you are taken directly to InsightVM after signing in and are presented with a “Welcome” screen, then you’re already in the right place.  Proceed to the [pairing key](doc:activating-your-console-on-the-insight-platform#section-5-copy-your-console-pairing-key) section.

### “Platform Home” page

If you are taken to the “Platform Home” page, browse to the InsightVM tile and click **Pair console** to open the “Welcome” screen described previously.  Proceed to the [pairing key](doc:activating-your-console-on-the-insight-platform#section-5-copy-your-console-pairing-key) section.

### Any other Insight product

If you already subscribe to other Insight products like InsightIDR or InsightOps, you may be taken directly to one of those screens instead.  To navigate back to your cloud instance of InsightVM, browse to the upper left corner of your screen and expand the dropdown next to the product name.  Click **My Account**.  From the “Platform Home” page, browse to the InsightVM tile and click **Pair console** to open the “Welcome” screen.  Proceed to the [pairing key](doc:activating-your-console-on-the-insight-platform#section-5-copy-your-console-pairing-key) section.

## 5. Copy your console pairing key

On the “Welcome” screen of InsightVM, copy the provided pairing key and proceed to the [activation](doc:activating-your-console-on-the-insight-platform#section-6-enter-your-pairing-key-in-your-security-console) section.  Console pairing keys use the following format:

```
XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX-XX
```
[block:callout]
{
  "type": "warning",
  "title": "Console pairing keys are different and separate from product activation keys.",
  "body": "The key shown on this screen is **not** a product activation key.  Console pairing keys are only meant to pair your on-premises Security Console to your cloud instance of InsightVM."
}
[/block]
## 6. Enter your pairing key in your Security Console

Return to your on-premises Security Console.  If necessary, log in using your [original console username and password](doc:activating-your-console-on-the-insight-platform#section-security-console-login) as usual.

A banner prompts you to enter the pairing key you copied from the previous step.  Click **Enter pairing key** on this banner to navigate directly to the **Insight platform** tab of the “Security Console Configuration” screen.

Enter your pairing key in the provided field and click **Activate Console**.  A notification indicates that the console pairing process was successful.
[block:callout]
{
  "type": "success",
  "title": "You’re on the platform!",
  "body": "You should now have successfully paired your on-premises Security Console with your cloud instance of InsightVM."
}
[/block]
# Troubleshooting

If you are having connection or sync issues, try the following procedures.

## Verify endpoint whitelisting

You must whitelist traffic to the corresponding hostname of your selected cloud region in order to communicate with the Insight platform.  Check the [Configure communications with the Insight platform](https://insightvm.help.rapid7.com/docs/configure-communications-with-the-insight-platform) page and verify that you have configured whitelisting properly.

## Restart the console collector

In cases where the collector is stuck in an error state, try restarting the collector:

1. From your left navigation menu, click the **Administration** tab.
2. In the “Maintenance, Storage and Troubleshooting” section, click **Run**.
3. Enter `collector stop` in the command box.  Click **Execute**.
4. Once stopped, enter `collector start` and click **Execute** again.

# Console deactivation
[block:callout]
{
  "type": "danger",
  "title": "WARNING - Data loss",
  "body": "Deactivating your console from the Insight platform will result in the **permanent loss** of all your saved dashboards, remediation projects, goals, filters, and any other cloud feature configurations you have saved during your opt-in period.\n\nWhile your console data will be unaffected, you will need to reactivate your console in order to sync your data to the Insight platform again."
}
[/block]
If you need to deactivate your Security Console from the Insight platform, return to the **Insight platform** tab of the “Security Console Configuration” screen and click **Deactivate Console**.