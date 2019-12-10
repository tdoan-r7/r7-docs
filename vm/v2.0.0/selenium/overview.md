---
title: "overview"
excerpt: ""
---
# Setting Up Selenium Scripts

Selenium is a tool that record's browser actions and responses used predominantly by testing and automation teams. AppSpider can execute Selenium scripts at runtime. This means that new session cookies are generated. If proxy file recordings of Selenium script executions are used, the cookies can be old and the web scanner will not be logged in unless the Selenium scripts are rerun and rerecorded.

It allows them to:

- Build a comprehensive testing suite that ensures every aspect of application functionality. If AppSpider uses Selenium, the entire site will be tested.

- Get testing done earlier and faster. 
 

## System Requirements

- AppSpider (6.9 or higher) 
 
- Java Development Kit (1.8 or higher) 
 
- Apache Maven 
 

## Browser Requirements

- Mozilla Firefox (39 or higher)

## Building your source code

This document provides an example of a using the Selenium Firefox WebDriver written in Java, and proxying it through AppSpider.

Create a project in Maven to build your Selenium script. Use the Java code from the following link as a guideline: [https://github.com/sdavis-r7/selenium-java-firefox-appspider-example/blob/master/src/main/java/com/rapid7/TestFirefoxSelenium.java](https://github.com/sdavis-r7/selenium-java-firefox-appspider-example/blob/master/src/main/java/com/rapid7/TestFirefoxSelenium.java).

1. Assign baseUrl: 
 

`private String baseUrl = baseScheme + "://www.mozilla.org/";`

1. Assign proxyPort: 
 

`private String proxyPort = "32768";`

1. Assign FF\_PROFILE (Firefox Profile Name): 
 

`private String FF_PROFILE = "RAPID7APPSPIDERSELENIUM";`

1. Configure Selenium WebDriver to use Firefox:

ProfilesIni listProfiles = new ProfilesIni();

FirefoxProfile profile = listProfiles.getProfile( FF\_PROFILE );

objDesiredCapabilities.setCapability(FirefoxDriver.PROFILE,profile);

driver = new FirefoxDriver(objDesiredCapabilities);

1. Configure Selenium to run through AppSpider proxy: 
 

Proxy objProxy = new Proxy();

objProxy.setHttpProxy(proxyUrl+":"+proxyPort);

objProxy.setSslProxy(proxyUrl+":"+proxyPort);

objDesiredCapabilities.setCapability(CapabilityType.PROXY, objProxy);

 

1. Run the Maven package and build the Selenium .jar file:

mvn package

## Exporting the AppSpider proxy certificate

This task must be performed on the AppSpider machine intended to run the script.

1. In Windows, click the **Start** button.

2. Type **certmgr.msc** into the search box and press **ENTER**.

![](https://help.rapid7.com/appspider/content/resources/images/selenium/ExportCertificate-Search.png)

1. Navigate to **Trusted Root Certification Authorities -\> Certificates.**

2. Locate and right-click the **Rapid7 ProxyServer** certificate.

3. Navigate to **All Tasks -\> Export** to open the certificate Export Wizard.

![](https://help.rapid7.com/appspider/content/resources/images/selenium/ExportCertificate-Export.png)

1. Click the **Next** button to begin.

![](https://help.rapid7.com/appspider/content/resources/images/selenium/CertificateExportWizard-Next.png)

1. Select **No, do not export the private key** and click the **Next** button.

![](https://help.rapid7.com/appspider/content/resources/images/selenium/CertificateExportWizard-DoNotExportPrivatekey.png)

1. Select **DER encoded binary X.509 (.CER)** and click the **Next** button.

![](https://help.rapid7.com/appspider/content/resources/images/selenium/CertificateExportWizard-SelectDER.png)

1. Name the file **Rapid7 ProxyServer** and click the **Next** button.

![](https://help.rapid7.com/appspider/content/resources/images/selenium/CertificateExportWizard-NameFile.png)

1. Click the **Finish** button to complete the Certificate Export Wizard.

![](https://help.rapid7.com/appspider/content/resources/images/selenium/CertificateExportWizard-Finish.png)

## Creating a Firefox profile

1. Hold the **Windows Key + R** to open the Run dialog box.

2. Type **firefox.exe -p** into the Run dialog box and click the **OK** button.

![](https://help.rapid7.com/appspider/content/resources/images/selenium/CreateFirefoxProfile-OpenRunDialogBox.png)

1. Click the **Create Profile** button.

![](https://help.rapid7.com/appspider/content/resources/images/selenium/CreateFirefoxProfile-CreateProfile.png)

1. Click the **Next** button to create a Firefox profile.

![](https://help.rapid7.com/appspider/content/resources/images/selenium/CreateFirefoxProfile-Next.png)

1. Enter **RAPID7APPSPIDERSELENIUM** as the profile name and click the **Finish** button.

![](https://help.rapid7.com/appspider/content/resources/images/selenium/CreateFirefoxProfile-ProfileName.png)

1. Select **RAPID7APPSPIDERSELENIUM** and click the **Start Firefox** button.

![](https://help.rapid7.com/appspider/content/resources/images/selenium/FirefoxProfile-StartFirefox.png)

## Importing the Trusted Root Certificate

1. Navigate to **Firefox Options -\> Advanced -\> Certificates -\> View Certificates.**

![](https://help.rapid7.com/appspider/content/resources/images/selenium/ImportCertificate-ViewCertificates.png)

1. Select the **Authorities** tab and click the **Import** button.

![](https://help.rapid7.com/appspider/content/resources/images/selenium/ImportCertificate-Import.png)

1. Select the certificate file named **Rapid7 ProxyServer** and click the **Open** button.

![](https://help.rapid7.com/appspider/content/resources/images/selenium/ImportCertificate-Open.png)

1. Click the **OK** button to exit the Certificate Manager.

![](https://help.rapid7.com/appspider/content/resources/images/selenium/ImportCertificate-OK.png)

## Editing the scan configuration in AppSpider

1. Open AppSpider.

2. Locate the scan configuration and select **Edit Configuration**.

3. Select **Proxy** from the _Pages_ menu. 

4. Select **Use Firefox settings**.

![](https://help.rapid7.com/appspider/content/resources/images/selenium/ProxySettings-SelectUseFirefoxSettings.png)

1. Select **Selenium Recordings** from the _Pages_ menu. 

2. Click the **Add File (+)** icon, highlight the bundled Selenium .jar file, and click the **Open** button.

![](https://help.rapid7.com/appspider/content/resources/images/selenium/AddFile-ClickOpen.png)

The .jar file is now visible in AppSpider.

1. Select the **Restrict scan to Selenium recording** check box to limit the scan to the Selenium script.

2. Click the **Save & Run** button to start the scan in AppSpider.

![](https://help.rapid7.com/appspider/content/resources/images/selenium/SeleniumRecordings-RestrictScan.png)