---
title: "Enabling FIPS mode"
excerpt: ""
---
If you are operating the application in an environment where the use of FIPS-enabled products is mandatory, or if you want the security of using a FIPS-certified encryption module, you should enable FIPS mode. The application supports the use of Federal Information Processing Standard (FIPS) 140-2 encryption, which is required by government agencies and companies that have adopted FIPS guidelines.

###What is FIPS?

The FIPS publications are a set of standards for best practices in computer security products. FIPS certification is applicable to any part of a product that employs cryptography. A FIPS-certified product has been reviewed by a lab and shown to comply with FIPS 140-2 (Standard for Security Requirements for Cryptographic Modules), and to support at least one FIPS-certified algorithm.

Government agencies in several countries and some private companies are required to use FIPS-certified products.

###What is FIPS mode?

FIPS mode is a configuration that uses FIPS-approved algorithms only. When the application is configured to operate in FIPS mode, it implements a FIPS-certified cryptographic library to encrypt communication between the Security Console and Scan Engines, and between the Security Console and the user for both the browser and API interfaces.

###FIPS mode considerations

It is important to note that due to encryption key generation considerations, the decision to run in FIPS mode or non-FIPS mode is irrevocable. The application must be configured to run in FIPS mode immediately after installation and before it is started for the first time, or else left to run in the default non-FIPS mode. Once the application has started with the chosen configuration, you will need to reinstall it to change between modes.

###Activating FIPS mode

When InsightVM is installed, it is configured to run in non-FIPS mode by default. The application must be configured to run in FIPS mode before being started for the first time. See [Activating FIPS mode in Linux](doc:enabling-fips-mode#section-activating-fips-mode-linux).

When FIPS mode is enabled, communication between the application and non-FIPS enabled applications such as Web browsers or API clients cannot be guaranteed to function correctly.

####Activating FIPS mode in Linux

You must follow these steps after installation, and BEFORE starting the application for the first time.

To enable FIPS mode:
1. Install rng-utils.
The encryption algorithm requires that the system have a large entropy pool in order to generate random numbers. To ensure that the entropy pool remains full, the rngd daemon must be running while the application is running. The rngd daemon is part of the rng-utils Linux package.
2. Download and install the rng-utils package using the system’s package manager.
[block:callout]
{
  "type": "info",
  "body": "Add the rngd command to the system startup files so that it runs each time the server is restarted."
}
[/block]
3. Run the command ```rngd -b -r /dev/urandom```.
4. Create a properties file for activating FIPS mode.
5. Create a new file using a text editor.
6. Enter the following line in this file:
```fipsMode=1```
7. Save the file in the [install_directory]/nsc directory with the following name:
CustomEnvironment.properties
8. Start the Security Console.

####Activating FIPS mode in Windows

You must follow these steps after installation, and before starting the application for the first time.

To enable FIPS mode:
1. Create a properties file for activating FIPS mode.
2. Create a new file using a text editor.
3. Enter the following line in this file:
```fipsMode=1```
[block:callout]
{
  "type": "info",
  "body": "You can disable database consistency checks on startup using the CustomEnvironment.properties file. Do this only if instructed by Technical Support."
}
[/block]
4. Save the file in the [install_directory]\nsc directory with the following name:
CustomEnvironment.properties
5. Start the Security Console.

####Verifying that FIPS mode is enabled

To ensure that FIPS mode has been successfully enabled, check the Security Console log files for the following messages:
```
FIPS 140-2 mode is enabled. Initializing crypto provider
Executing FIPS self tests...
```