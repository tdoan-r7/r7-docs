---
title: "installation-issues"
excerpt: ""
---
# Common Installation Questions

Questions about installing AppSpider? Check out the top questions we've received from customers below.

## Can I install AppSpider Pro on a different machine using the same license key?

The AppSpider licensing engine limits the use of one installation per product key. You cannot use one product key to install on multiple systems at the same time. However, you can move the installation to another PC but in some cases we may need to do a reset on the license key.

## How do I fix an invalid license error or reset my license?

1. Delete the license folder program files folder, which is located in C:\Program Files (x86)\Rapid 7\AppSpider 6\ScanEngine\License. 
 
2. Open regedit. 
 
3. Delete the following keys: 
 
4. HKEY\_LOCAL\_MACHINE\SOFTWARE\Wow6432Node\Acudata\Sheriff\ProductID\5376-8831-2529-7643-5729 
 
5. HKEY\_LOCAL\_MACHINE\SOFTWARE\Wow6432Node\Acudata\Sheriff\ProductID\5376-8851-2229-7643-5724. 
 

1. Restart the system and try to enter your key again. 
 

## Is there a major difference between using the different editions of SQL 2008 server?

Yes, there is a difference in the database size. SQL Express supports a database size up to 10 GB and 1 CPU, whereas Enterprise supports up to 2 TB and 8 CPU.

## How do I get the latest version of AppSpider Pro?

An notification message will alert you that an update is available when you log in to AppSpider Pro.

![](https://help.rapid7.com/appspider/content/resources/images/common-issues/updates/update-notification.jpg)

You can click on the notification message to access the download link for the latest installer. Or you can go directly to [https://www.rapid7.com/products/appspider/download.jsp](../getting-started/getting-started-pro.htm) to download the latest installer.

Running the installer will take you through the set up process again, except this time, it will update AppSpider Pro to the latest version.