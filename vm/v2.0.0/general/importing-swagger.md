---
title: "importing-swagger"
excerpt: ""
---
# Importing Swagger REST API

The Swagger Utility is available in AppSpider Pro 6.8 and later. It's a tool that allows you to upload Swagger REST API documents to enable the scanning of the API by AppSpider. The Swagger Utility currently supports the Swagger 2.0 version saved in JSON.

Swagger provides a way of publishing remote REST API function calls and what response to expect back from the calls.  AppSpider parses the Swagger document to generate function calls and create values for the expected parameters.  The file is then saved as a TREC traffic recording file which then can be used by AppSpider to scan and attack the REST API. 

To access the Swagger Utility, go to the Tools menu and choose **Swagger Utility**.

![](https://help.rapid7.com/appspider/content/resources/images/swagger/03000001.png)

When the Swagger Utility is opened, you'll see a new tab called "Swagger Utility”.

![](https://help.rapid7.com/appspider/content/resources/images/swagger/03000002.png)

 

From this tab, can click Open to browse to the location of the Swagger JSON files you want to upload to AppSpider.

![](https://help.rapid7.com/appspider/content/resources/images/swagger/03000003.png)

After you upload the Swagger JSON files, the API function calls from the document will listed in the traffic viewer window.

![](https://help.rapid7.com/appspider/content/resources/images/swagger/03000004.png)

If you need to edit any parameters, you can click the **Edit API Parameters** button to launch the editor. When you are done editing, close the editor and the updated parameter values will be propagated in the various request calls.

![](https://help.rapid7.com/appspider/content/resources/images/swagger/03000005.png)

After you edit the API parameters, you'll need to save the traffic recording file, which you can use to add to a scan configuration.

![](https://help.rapid7.com/appspider/content/resources/images/swagger/03000006.png)

Now you can create a new scan configuration and you can use the traffic recording created by the Swagger Utility.  Go to **Configuration \> New** to access the scan configuration form. When you create the scan configuration, it is recommended that you include the base URL of the REST API in the URL list so that the same domain restrictions that apply to that will apply to the REST calls.

![](https://help.rapid7.com/appspider/content/resources/images/swagger/03000007.png)

When you get to the "Recorded Traffic" section of the scan configuration press on the Green Plus icon (+) to add the Traffic recording file created by the Swagger Utility.

![](https://help.rapid7.com/appspider/content/resources/images/swagger/03000008.png)

If you want to limit the scan to only the recorded traffic file, select the **Restrict scan to recorded traffic** option.

![](https://help.rapid7.com/appspider/content/resources/images/swagger/03000009.png)

After you finish configuring the scan, you can save the configuration and run the scan.