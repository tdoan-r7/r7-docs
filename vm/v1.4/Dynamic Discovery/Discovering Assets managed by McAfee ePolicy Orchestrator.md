---
title: "Discovering Assets managed by McAfee ePolicy Orchestrator"
excerpt: ""
---
The McAfee ePolicy Orchestrator connection allows InsightVM to collect information from McAfee ePolicy Orchestrator (ePO) about the assets it manages. InsightVM can scan the assets managed by ePO and provide additional vulnerability assessment. If configured with an McAfee Data Exchange Layer (DXL) discovery connection, it can monitor these assets for malicious file detection events and perform automated actions such as adding tags that can give you context you need to understand your risk and your next steps.You can also configure InsightVM to publish risk scores to an ePO dashboard and share its vulnerability information with McAfeeThreat Intelligence Exchange (TIE). To learn more about the DXL and TIE components, see [Discovering vulnerability data collected by McAfee Data Exchange Layer (DXL)](doc:discovering-vulnerability-data-collected-by-mcafee-data-exchange-layer-dxl).

Version(s) of ePO currently supported:

* 5.1
* 5.3
[block:callout]
{
  "type": "info",
  "body": "Assets are synchronized from ePO once per day."
}
[/block]
McAfee ePolicy Orchestrator connections must be created from the Administration page. To learn more, see  [Creating a connection](doc:creating-and-managing-dynamic-discovery-connections#section-creating-a-connection).

The recommended best practice is to connect all assets managed by ePO into a single static site, and then use dynamic asset groups to categorize and scan the assets. To learn more, see [Using dynamic asset groups].
[block:callout]
{
  "type": "warning",
  "body": "In order to create an McAfee ePolicy Orchestrator connection, you will need to have a static site already configured. You can use an existing site or create a new one.",
  "title": "NOTE"
}
[/block]
If the Rapid7 Nexpose extension is installed on the ePO server, a dashboard will be created in ePO. If an McAfee ePolicy Orchestrator connection is configured to push risk scores back to ePO as described in [Creating and managing Dynamic Discovery connections](doc:creating-and-managing-dynamic-discovery-connections), then once you scan the assets, this dashboard will show the top ten highest-risk assets managed by ePO, as determined by Nexpose's vulnerability assessment and risk scoring system.

To view the **Rapid7 Nexpose Insight: Top 10 Riskiest Systems** dashboard in McAfee ePolicy Orchestrator:

1. Log on to the ePO installation using an account with Dashboards permission and Nexpose Run Command permission.
2. Navigate to the **Dashboards** section as described in the _Dashboards and Monitors_ section of the McAfee ePolicy Orchestrator Help.
3. From the drop-down menu, select **Rapid7 Nexpose Insight Summary**.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/ed3e0ea-ePO_select_NX_dashboard.jpg",
        "ePO_select_NX_dashboard.jpg",
        640,
        305,
        "#ebebe9"
      ]
    }
  ]
}
[/block]
4. The **Rapid7 Nexpose Insight: Top 10 Riskiest Systems** dashboard appears in the ePO interface. For information on actions you can perform with this dashboard, refer to the McAfee ePolicy Orchestrator Help.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/7582842-ePO_Nexpose_dashboard.jpg",
        "ePO_Nexpose_dashboard.jpg",
        886,
        349,
        "#f2f0f3"
      ]
    }
  ]
}
[/block]
## Preparing the target environment for discovery through McAfee ePolicy Orchestrator

In order to discover assets managed by McAfee ePolicy Orchestrator with InsightVM, you must install the Rapid7 Nexpose extension in McAfee ePolicy Orchestrator. The extension can be downloaded from [http://download2.rapid7.com/download/NeXpose-v4/epo-extension/Rapid7Nexpose.zip](http://download2.rapid7.com/download/NeXpose-v4/epo-extension/Rapid7Nexpose.zip).

Once the extension is installed, a user called NexposeServiceUser will be automatically created. Enable this user and set a valid password to use in the connection from InsightVM.