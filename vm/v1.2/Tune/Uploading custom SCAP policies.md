---
title: "Uploading custom SCAP policies"
excerpt: ""
---
There is no one-size-fits-all solution for managing configuration security. The application provides policies that you can apply to scan your environments. However, you may create custom scripts to verify items specific to your company, such as health check scripts that prioritize security settings. You can create policies from scratch, upload your custom content to use in policy scans, and run it with your other policy and vulnerability checks.

You must log on as Global Administrator to upload policies.
[block:callout]
{
  "type": "warning",
  "body": "To upload policies you must have the Policy Editor capability enabled in your license. Contact your account representative if you want to update your license."
}
[/block]
##File specifications

SCAP 1.2 datastreams and datastream collections are in XML format.

SCAP 1.0 policy files must be compressed to an archive (ZIP or JAR file format) with no folder structure. The archive can contain only XML or TXT files. If the archive contains other file types, such as CSV, then the application does not upload the policy.

The archive file must contain the following XML files:

* **XCCDF file**—This file contains the structure of the policy. It must have a unique name (title) and ID (benchmark ID). This file is required.
The SCAP XCCDF benchmark file name must end with _-xccdf.xml_ (For example, XYZ-xccdf.xml).
* **OVAL file**—These files contain policy checks. The file names must end with _-oval.xml_ (For example, XYZ-oval.xml).

If unsupported OVAL check types are in the policy, the policy fails to upload. The policy files must contain supported OVAL check types, such as:

* accesstoken_test
* auditeventpolicysubcategories_test
* auditeventpolicy_test
* family_test
* fileeffectiverights53_test
* lockoutpolicy_test
* passwordpolicy_test
* registry_test
* sid_test
* unknown_test
* user_test
* variable_test

The following XML files can be included in the archive file to define specific policy information. These files are not required for a successful upload.

* **CPE files**—These files contain the Uniform Resource Identifiers (URI) that correspond to fingerprinted platforms and applications.
The file must begin with _cpe:_ and includes segments for the hardware facet, the operating system facet, and the application environment facet of the fingerprinted item (For example, cpe:/o:microsoft:windows_xp:-:sp3:professional).
* **CCE files**—These files contain CCE identifiers for known system configurations to facilitate fast and accurate correlation of configuration data across multiple information sources and tools.
* **CVE files**—These files contain CVE (Common Vulnerabilities and Exposures) identifiers to known vulnerabilities and exposures.

##Version and file name conventions

You can name your custom policies to meet your company’s needs. The application identifies policies by the benchmark ID and title. You must create unique names and IDs in your benchmark file to upload them successfully. The application verifies that the benchmark version to identifies a benchmark (v1.2.1.0) that is supported.
[block:callout]
{
  "type": "info",
  "body": "The application does not upload custom policies with the same name and benchmark ID as an existing policy."
}
[/block]
##Uploading SCAP policies
[block:callout]
{
  "type": "info",
  "body": "Custom policies uploaded to the application can be edited with the Policy Manager. See [Creating a custom policy](doc:creating-a-custom-policy)."
}
[/block]
To upload a policy, complete the following steps:

1. Click the **Policies** icon.
2. Click the **Upload Policy** button.
If you cannot see this button then you must log on as a Global Administrator.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/ae56f5a-s_upload_policy_button.jpg",
        "s_upload_policy_button.jpg",
        1265,
        545,
        "#eff5f6"
      ],
      "caption": "Clicking the **Upload Policy** button"
    }
  ]
}
[/block]
The system displays the _Upload a policy_ panel.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1d90063-s_upload_policy.jpg",
        "s_upload_policy.jpg",
        831,
        421,
        "#e8eeef"
      ],
      "caption": "Entering SCAP policy file information"
    }
  ]
}
[/block]
3. Enter a name to identify the policy. This is a required field.
To identify which policies are customized for your organization you can devise a file naming convention. For example, add your organization name or abbreviation, such as _XYZ Org -USGCB 1.2.1.0 - Windows 7 Firewall_.
4. Enter a description that explains what settings are applied in the custom policy.
5. Click the Browse button to locate the archive file.
6. Click the Upload button to upload the policy.
   * If the policy uploads successfully, go to step 7.
   * If you receive an error message the policy is not loaded. You must resolve the issue noted in the error message then repeat these steps until the policy loads successfully. For more information about errors, see [Troubleshooting upload errors](doc:uploading-custom-scap-policies#section-troubleshooting-upload-errors).
During the upload, a "spinning" image appears: ![Alt](https://files.readme.io/0135703-s_nx_progress_spinner.jpg). The time to complete the upload depends on the policy's complexity and size, which typically reflects the number of rules that it includes.
When the upload completes, your custom policies appear in the _Policy Listing_ panel on the **Policies** page. You can edit these policies using the Policy Manager. See [Creating a custom policy](doc:creating-a-custom-policy).
7. Add your custom policies to the scan templates to apply to future scans. See [Selecting Policy Manager checks](doc:selecting-policy-manager-checks).

##Uploading specific benchmarks or datastreams

You can select any combination of datastream or the underlying benchmark in the following manner: Upload an SCAP 1.2 XML policy file using the steps described in [Uploading custom SCAP policies](doc:uploading-custom-scap-policies). After you specify the XML file for upload, the Security Console displays a page for selecting individual components from the datastream collection. All components are selected by default. To prevent any component from being included, clear the check box for that component. Then, click **Upload**.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/8c1a40c-s_nx_scap_v500.jpg",
        "s_nx_scap_v500.jpg",
        1013,
        489,
        "#e9efee"
      ],
      "caption": "Selecting SCAP 1.2 XML components for upload"
    }
  ]
}
[/block]
##Troubleshooting upload errors

Policies are not uploaded to the application unless certain criteria are met. Error messages identify the criteria that have not been met. You must resolve the issues and upload the policy successfully to apply your custom SCAP policy to scans.

Each of the following errors (in italics) is listed with the resolution indented after it. In the error messages, value is a placeholder for a specific reference in the error message.

_The SCAP XCCDF Benchmark file [value] cannot be parsed.
Content is not allowed in prolog._

There are characters positioned before the first bracket (<). For example:    

* **abc**<?xml version="1.0" encoding="UTF-8">
* There are hidden characters at the beginning of the SCAP XCCDF benchmark file. The following items are hidden characters:
   * White space
   * Byte Order Mark character in UTF8 encoded XML file, that is caused by text editors like Microsoft® Notepad.
   * Any other type of invisible characters.
* Use a hex editor to remove the hidden characters.
* There is a mismatch in the encoding declaration and the SCAP XCCDF benchmark file. For example, there is a UTF8 declaration for a UTF16 XML file.
* The SCAP XCCDF benchmark file contains unsupported character encoding.
* If the XML encoding declaration is missing then it will default to the server’s default encoding. If the XML content contains characters that are not supported by the default character encoding then the SCAP XCCDF benchmark file cannot be parsed. 
Add a UTF8 declaration to the SCAP XCCDF benchmark file.

_The SCAP XCCDF Benchmark file cannot be found. Verify that the SCAP XCCDF benchmark file name ends in “-xccdf.xml” and is not under a folder in the archive._

> The application cannot find the SCAP XCCDF benchmark file in the archive.

The SCAP XCCDF benchmark file name must end with -xccdf.xml (For example, XYZ-xccdf.xml). The archive (ZIP or JAR) cannot have a folder structure.

Verify that the SCAP XCCDF benchmark file exists in the archive using the required naming convention.

_The SCAP XCCDF Benchmark version could not be found in [value]._

> The SCAP XCCDF benchmark file must contain a valid schema version.

Add the schema version (SCAP policy) to the SCAP XCCDF benchmark file.

_The SCAP XCCDF Benchmark version [value] is unsupported._

> The SCAP XCCDF benchmark file must contain a version in supported format (for example, 1.1.4). The application currently supports version 1.1.4 or earlier.

Replace the version number using a valid format. Verify that there are no blank spaces.

_The SCAP XCCDF Benchmark file must contain an ID for the Benchmark to be uploaded._

> The SCAP XCCDF benchmark file must contain a benchmark ID.

Add a benchmark ID to the SCAP XCCDF benchmark file.

_The SCAP XCCDF Benchmark file [value] contains a Benchmark ID that contains an invalid character: [value]. The Benchmark cannot be uploaded._

> The benchmark ID has an invalid character, such as a blank space.

Replace the benchmark ID using a valid format.

_The SCAP XCCDF Benchmark file [value] contains a reference to an OVAL definition file [value] that is not included in the archive._

> Verify that the archive file contains all policy definition files referenced in the SCAP XCCDF benchmark file. Or remove the reference to the missing definition file.

_The SCAP XCCDF Benchmark file [value] contains a test [value] that is not supported within the product. The test must be removed for the policy to be uploaded._

> The SCAP XCCDF benchmark file includes a test that the application does not support.

Remove the test from the SCAP XCCDF benchmark file .

_The uploaded archive is not a valid zip or jar archive._

> The format of the archive is invalid.

The archive (ZIP or JAR) cannot have a folder structure.

Compress your policy files to an archive (ZIP or JAR) with no folder structure.

_The SCAP XCCDF Benchmark file contains a rule [value] that refers to a check system that is not supported. Please only use OVAL check systems._

> There are unsupported items (such as OVAL check types).

Remove the unsupported items from the SCAP XCCDF benchmark file.

_The item [value] is not a XCCDF Benchmark or Group. Only XCCDF Benchmarks or Groups can contain other items._

> Revise the SCAP XCCDF benchmark file. so only benchmarks or groups contain other benchmark items.

_The SCAP XCCDF item [value] requires a group or rule [value] to be enabled that is not present in the Benchmark and cannot be uploaded._

> A requirement in the SCAP XCCDF benchmark file is missing a reference to a group or rule.

Review the requirement specified in the error message to determine what group or rule to add.

_The SCAP XCCDF item [value] requires a group or rule [value] to not be enabled that is not present in the Benchmark and cannot be uploaded._

> A conflict in the SCAP XCCDF benchmark file is referencing an item that is not recognized or is the wrong item.

Review the conflict specified in the error message to determine which item to replace.

_The SCAP XCCDF item [value] requires a group or rule [value] to not be enabled, but the item reference is neither a group or rule. The Benchmark cannot be uploaded._

> A conflict in the SCAP XCCDF benchmark file is missing a reference to a group or rule.

Review the conflict specified in the error message to determine what group or rule to add.

_The SCAP XCCDF Benchmark contains two profiles with the same Profile ID [value]. This is illegal and the Benchmark cannot be uploaded._

> There are two profiles in the SCAP XCCDF benchmark file that have the same ID.

Revise the SCAP XCCDF benchmark file so that each <profile> has a unique ID.

_The SCAP XCCDF Benchmark contains a value [value] that does not have a default value set. The value [value] must have a default value defined if there is no selector tag. The Benchmark failed to upload._

> A default selection must be included for items with multiple options for an element, such as a rule.

If the item has multiple options that can be selected then you must specify the default option.

_The SCAP XCCDF Benchmark [value] contains reference to a CPE platform [value] that is not referenced in the CPE Dictionary. The SCAP XCCDF Benchmark cannot be uploaded._

> The application does not recognize CPE platform reference in the SCAP XCCDF benchmark file.

Remove the CPE platform reference from the SCAP XCCDF benchmark file.

_The SCAP XCCDF Benchmark file [value] contains an infinite loop and is illegal. The Benchmark cannot be uploaded._

> Review the SCAP XCCDF benchmark file to locate the infinite loop and revise the code to correct this error.

_The SCAP XCCDF Benchmark file [value] contains an item that attempts to extend another item that does not exist, or is an illegal extension. The Benchmark cannot be uploaded._

> There is an item referenced in the SCAP XCCDF benchmark file that is not included in the Benchmark.

Revise the SCAP XCCDF benchmark file to remove the reference to the missing item or add the item to the Benchmark.

_The referenced check [value] in [value] is invalid or missing._

> There is an check referenced in the SCAP XCCDF benchmark file that is not included in the Benchmark.

Revise the SCAP XCCDF benchmark file to remove the reference to the missing check or add the check to the Benchmark.

_[value] benchmark files were found within the archive, you can only upload one benchmark at a time._

The archive must contain only one benchmark or it cannot be uploaded.

Create a separate archive for each benchmark and upload each archive to the application.

_The SCAP XCCDF Benchmark Value [value] cannot be created within the policy [value]._

> The application cannot resolve the value within the policy.

Review the benchmark and revise the value.

_The SCAP XCCDF Benchmark file [value] cannot be parsed. 
[value]_

> The SCAP XCCDF benchmark file cannot be parsed due to the issue indicated at the end of the error message.

_The SCAP XCCDF item [value] does not reference a valid value [value] and the Benchmark cannot be parsed._

> A requirement in the SCAP XCCDF benchmark file is referencing an item that is not recognized or is the wrong item.

Review the requirement specified in the error message to determine which item to replace.

_The SCAP XCCDF Benchmark file contains a XCCDF Value [value] that has no value provided. The Benchmark cannot be parsed._

> Add a value to XCCDF value reference in the SCAP XCCDF benchmark file.

_The SCAP OVAL file [value] cannot be parsed. 
[value]_

> This parsing error identifies the issue preventing the SCAP OVAL file from loading.

Review the SCAP OVAL file and located the issue listed in the error message to determine the appropriate revision.

_The SCAP OVAL Source file [value] could not be found._

> The application cannot find the SCAP OVAL Source file in the archive. This file must end with -oval.xml or -patches.xml.

> Verify that the SCAP OVAL Source file exists in the archive and the file name ends in the correct format.