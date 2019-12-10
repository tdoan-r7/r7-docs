---
title: "Configuring File Searches on Target Systems"
excerpt: ""
---
If InsightVM gains access to an asset’s file system by performing an exploit or a credentialed scan, it can search for the names of files in that system.

File name searching is useful for finding software programs that are not detected by fingerprinting. It also is a good way to verify compliance with policies in corporate environments that don't permit storage of certain types of files on workstation drives:
* Copyrighted content
* Confidential information, such as patient file data in the case of HIPAA compliance
* Unauthorized software

The Security Console can read the metadata of these files, but it does not read nor retrieve file contents. You can view the names of scanned file names in the "File and Directory Listing" pane of a scan results page.
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "File searching operations can take a considerable amount of time to complete. For this reason, we do not recommend file searching during routine network scanning. Instead, file searching is best implemented with ad hoc or manual scans."
}
[/block]
# How to Configure File Searching

You can configure file searching capabilities on new or existing custom scan templates.

**To configure file searching on your scan template:**

1. In your Security Console, open the left menu and click the **Administration** tab.
2. In the “Global and Console Settings” section, click **manage** next to the “Templates” label.
3. Browse to the template that you want to configure.
 * If the custom scan template that you want to configure already exists, browse to it and click the edit icon.
 * If you want to create a new custom template from a built-in version, click the copy icon next to the desired template.
4. On the “Scan Template Configuration” screen, click the **File Searching** tab.
5. Click **Add File Search**. The “File Search Editor” window displays.
6. Name your file search configuration. This name will identify the configuration in the “File Search Listing” table going forward.
7. Select a pattern type. The following options are available:
 * **DOS wildcard pattern**
 * **GNU regular expression**
[block:callout]
{
  "type": "info",
  "title": "How are these patterns different?",
  "body": "The most important distinction between these two pattern types is how they evaluate character wildcards.\n\nThe DOS pattern supports two wildcards that function as stand-ins for allowable characters. These wildcards are as follows:\n\n* `*` - matches any combination of allowable characters\n* `?` - matches any single allowable character\n\nUnlike the DOS variant, the GNU regular expression pattern only supports a single character wildcard, but it also includes several operators that change how that wildcard is matched. This character wildcard is as follows:\n\n* `.` - matches any single character\n\nYou can modify how this character behaves by appending one of the following operators to the wildcard (or to any other literals that you want to match):\n\n* `*` - matches zero or more of the preceding character. For example, `.*` would match zero or more of any allowable character.\n* `+` - matches one or more of the preceding character. While this is similar to the `.*` example, `.+` would only match if at least one character was present.\n* `?` - matches the preceding character a single time, if it exists. This functionally makes the preceding character optional. For example, `.?` would match any character a single time, but would not break the expression if it didn’t appear."
}
[/block]
8. Enter your search string in the provided field. Make sure that you observe the syntax requirements of your selected pattern type.
9. Click **Save** when finished.

Your file search configuration should now display in the “File Search Listing” table. Click **Save** in the upper right corner of the “Scan Template Configuration” screen to apply your configuration for use with your next scan.