---
title: "Web interface frequently asked questions"
excerpt: ""
---
This page concerns using the InsightVM Security Console Web interface.

## How do I increase the session timeout value for the InsightVM Security Console Web interface?

Only a InsightVM global administrator can perform this task.

Click the **Manage** link next to InsightVM Security Console on the _Administration_ page to launch the _InsightVM Security Console Configuration_ wizard.

Go to the _Web Server_ page.

Change the session timeout to the desired value.

## If I accidentally close a pane on a page in the interface, how do I retrieve it?

You can you make closed panes visible by clicking the **Customize dashboard** link on the left side of the tab bar. A list of closed panes appears. Click the plus icon for any panes that you wish to make visible, and then click **Close**. Keep this feature in mind when you go to a page of the interface that is not displaying data that you are looking for.

## What should I do if I can't log on to the InsightVM Security Console Web interface?

InsightVM passwords are case sensitive, so make sure that you are using the proper capitalization and that the Caps Lock keyboard feature is not enabled. If you are still unable to log on with your correct password, you may have exceeded the lockout threshold, which is three invalid attempts. A InsightVM global administrator can unlock accounts by entering the ```unlock account <user name>``` command on the admin/global/diag_console.html page of theInsightVM Security Console Web interface. A global administrator also can reset passwords and provide temporary passwords.

## How do I run command prompts in the Web interface?

Go the page /admin/global/diag_console.html, and enter command prompts in the displayed box.

####Can I use a browser with a character set for a Chinese language?

Please refer to browser documentation for intstructions on using different languages.