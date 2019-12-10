---
title: "AppSec Chrome Extension"
excerpt: ""
---
The Rapid7 AppSec Plugin for the Chrome browser adds useful capabilities like recording your login activities or replaying attacks from your InsightAppSec console. In order to use this functionality you will need the latest version of the Chrome browser installed on your system. 

## Installation
1. To install the AppSec chrome plugin, click the following link: https://chrome.google.com/webstore/detail/appspider-chrome-plugin/mnmlipalillmakdiildpclhocfgcddnp?hl=en-GB
2. The 'Rapid7 AppSec Plugin' page below will open, click on the **ADD TO CHROME** button.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/472ace0-Screen_Shot_2018-01-29_at_3.39.29_PM.png",
        "Screen Shot 2018-01-29 at 3.39.29 PM.png",
        1920,
        1212,
        "#a0a4a7"
      ]
    }
  ]
}
[/block]
3. The following popup will appear, click the **Add extension** button.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e4a7f85-Screen_Shot_2018-01-29_at_3.41.45_PM.png",
        "Screen Shot 2018-01-29 at 3.41.45 PM.png",
        932,
        704,
        "#f3f2f2"
      ]
    }
  ]
}
[/block]
You will see a notification indicating that the chrome plugin has been successfully installed.

## Macro Recording

Once you have the AppSec chrome plugin installed you can use macro authentication for your scan configs. 

1. In the ‘Authentication’ tab of your scan config select the ‘Authentication Type’ menu option and choose ‘Macro Authentication’ from the drop down.
2. Click the **Record New Macro** button and enter the login URL for your application. Once you have done so click the **Start Recording** button.
3. A confirmation dialog will appear, notifying that the recording sequence has begun. The macro window will open at the URL you provided. Simply log in normally. Once you have logged in successfully, close the macro window and click the ‘Stop Recording’ button. 
4. A message will appear confirming that the recording was successful. Name your macro and click the ‘Save Macro’ button.
You should now see your recorded macro.
5. Save and run your config. It will now attempt authentication using your recorded macro. If successful the following will appear in the scan’s event log.


### Use Full Path

By default, the macro recording functionality records the login sequence using the page’s element IDs. In most cases this should suffice, however if your page is dynamically generated, then IDs may change. This could affect the success of the macro authentication.
To avoid issues you can specify the plugin to use the full path of elements when recording. XPath will then be used instead of element IDs.
To change these settings, click on the AppSec plugin’s browser icon and select ‘Macro’. Toggle the switch to select or deselect ‘Use Full Path’ based on your preference.

## Validate

1. To validate a vulnerability from InsightAppSec, simply navigate to the desired vulnerability and click on it. Click the **Replay Attack** button.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/62fa9ee-Screen_Shot_2018-02-01_at_10.46.54_AM.png",
        "Screen Shot 2018-02-01 at 10.46.54 AM.png",
        2240,
        1346,
        "#44515b"
      ]
    }
  ]
}
[/block]
2. Alternatively, if you have generated a ‘Vulnerabilities with Remediation Report’, you can validate attacks directly from the report. To do this, find the vulnerability you wish to validate and press the **Replay Attack** button.

Clicking the ‘Replay Attack’ button will result in the 'Vulnerability Validator' window opening.
Here you can see the attack request and response.

Along the top there are tabs (Attacks 1-5) that allow you to switch between each separate step in the attack traffic that occurred. 


### Settings

Clicking the ‘SETTINGS’ button in the bottom left corner of the validator window will open the following modal. 

#### Editor
The editor toggle allows you to switch how you edit your attack request. 
Selecting the ‘Raw’ option allows you to edit the request by entering text directly into the text areas.
The ‘Visual’ option gives users a user interface in which to add, edit or delete headers, cookies and parameters. These changes will then be reflected in the attack request.

#### Protocol
This toggle allows you to switch between HTTP and HTTPS protocols for your attack request URL.

#### Proxy
Enabling the ‘Use proxy’ switch will provide you with text boxes to enter details of the proxy you wish to send the attack through.


Once you are happy with your settings click the ‘SAVE SETTINGS’ button.

#### Get/Post Requests

To change the attack request between GET and POST messages, select the desired method from the dropdown beside the URL.


If you select POST, a text area will appear below the request in which you can add your POST body. To edit the POST body, change to the ‘Raw’ editor. (see settings section)


Once you have edited your attack request you can press the ‘SEND’ button to generate the updated attack response.
#### Editing Parameters

Parameters can also be added, modified or removed for the request URL by clicking the ‘EDIT HEADERS’ button while in the ‘Visual’ editor (see settings section) and selecting the ‘Parameters’ tab.


To add a new parameter, click the ‘ADD NEW’ button and enter the new key and value in the text boxes shown above. To delete a parameter, click the trash icon beside the parameter you wish to delete. 
Once satisfied with your changes, press the ‘SAVE CHANGES’ button. 

Any changes made will be reflected afterwards in the request URL input.


Alternatively, changes to parameters can be made directly from the request URL input when in the ‘Raw’ editor.


It is also possible to switch between HTTP and HTTPS protocols by clicking ‘SETTINGS’ and then selecting the desired protocol.

#### Request Headers & Cookies

Request headers can also be edited from the validate window. To make changes to these, click the ‘EDIT HEADERS’ button while in the ‘Visual’ editor (see settings section) and select the ‘Request Headers’ tab.


From here you can add new headers, modify existing headers and delete headers.
To add a header, click the ‘ADD NEW’ button. Enter the header label and content in the text boxes that appear. Headers can be modified by directly typing into the label and content text boxes.
To delete a header, click the trash icon beside the header you wish to delete. Once satisfied with your changes click the ‘SAVE CHANGES’ button.

To modify cookies for your attack request, select  the ‘COOKIES’ tab when in the ‘EDIT HEADERS’ section. From here you can add, edit and delete the cookies.

#### Comparing Attacks

While using the validate functionality it is possible to compare two different steps in the attack sequence and highlight the differences between them. To do this, click the *COMPARE ATTACKS* button in the top right of the validator window. The following modal will open.

To begin, select the two attacks you wish to compare from the checkboxes on the left. Once you have selected two attacks, the attack request and HTML response for each attack will be displayed in the boxes as shown below. A *HIGHLIGHT DIFFERENCE* button will also appear. Clicking the *HIGHLIGHT DIFFERENCE* button will highlight differences between the two steps as shown below.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/11d7c6e-Screen_Shot_2018-02-01_at_10.41.05_AM.png",
        "Screen Shot 2018-02-01 at 10.41.05 AM.png",
        1690,
        1488,
        "#465054"
      ]
    }
  ]
}
[/block]
Clicking the *HIDE HIGHLIGHTS* button will remove the highlighting and the *BACK* button will return you to the main validator window.