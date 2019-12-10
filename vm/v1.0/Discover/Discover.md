---
title: "Discover"
excerpt: ""
---
To know what your security priorities are, you need to discover what devices are running in your environment and how these assets are vulnerable to attack. You discover this information by running scans.

First, if you don't know what a site is, go to [What is a site?](doc:what-is-a-site). And learn about different [Site creation scenarios](doc:site-creation-scenarios) for use cases such as discovering all the assets in your environment, running PCI scans, and dealing with Zero-day vulnerabilities.

The *Discover* section provides guidance on operations that enable you to prepare and run scans.

[Creating and editing sites](doc:creating-and-editing-sites): Before you can run a scan, you need to create a site. A site is a collection of assets targeted for scanning. A basic site includes target assets (if necessary), a scan template, a Scan Engine, and users who have access to site data and operations. This section provides steps and best practices for creating a basic static site.

[Adding assets to sites](doc:adding-assets-to-sites): This section explains different ways to specify which assets should be scanned, and it provides best practices for planning sites.

[Selecting a Scan Engine for a site](doc:selecting-a-scan-engine-for-a-site): A Scan Engine is a requirement for a site. It is the component that will do the actual scanning of your target assets. By default, a site configuration includes the local Scan Engine that is installed with the Security Console. If you want to use a distributed or hosted Scan Engine, or a for a site, this section guides you through the steps of selecting it.

[Configuring distributed Scan Engines](doc:configuring-distributed-scan-engines): Before you can select a distributed Scan Engine for your site, you need to configure it and pair with the Security Console, so that the two components can communicate. This section shows you how.

[Working with Scan Engine pools](doc:working-with-scan-engine-pools): You can improve the speed of your scans for large numbers of assets in a single site by pooling your Scan Engines. This section shows you how to use them.

[Configuring scan credentials](doc:configuring-scan-credentials): To increase the information that scans can collect, you can authenticate them on target assets. Authenticated scans inspect assets for a wider range of vulnerabilities, as well as policy violations and adware or spyware exposures. They also can collect information on files and applications installed on the target systems. This section provides guidance for adding credentials to your site configuration. It also links to sections on elevating permissions, working with PowerShell, and best practices.

[Configuring scan authentication on target Web applications](doc:configuring-scan-authentication-on-target-web-applications): Scanning Web applications at a granular level of detail is especially important, since publicly accessible Internet hosts are attractive targets for attack. Authenticated scans of Web assets can flag critical vulnerabilities such as SQL injection and cross-site scripting. This section provides guidance on authenticating Web scans.

[Managing dynamic discovery of assets](doc:managing-dynamic-discovery-of-assets): If your environment includes virtual machines, you may find it a challenge to keep track of these assets and their activity. A feature called vAsset discovery allows you find all the virtual assets in your environment and collect up-to-date information about their dynamically changing states. This section guides you through the steps of initiating and maintaining vAsset discovery.

[Configuring a site using a Dynamic Discovery connection](doc:configuring-a-site-using-a-dynamic-discovery-connection): After you initiate vAsset discovery, you can create a dynamic site and scan these virtual assets for vulnerabilities. A dynamic site’s asset membership changes depending on continuous vAsset discovery results. This section provides guidance for creating and updating dynamic sites.

[Integrating NSX network visualizations with scans](doc:integrating-nsx-network-visualizations-with-scans): Integrating InsightVM with the VMware NSX network virtualization platform gives a Scan Engine direct access to an NSX network of virtual assets. This section provides guidance on setting up the integration.

[Running a manual scan](doc:running-a-manual-scan): After you create a site, you’re ready to run a scan. This section guides you through starting, pausing, resuming, and stopping a scan, as well as viewing the scan log and monitoring scan status.