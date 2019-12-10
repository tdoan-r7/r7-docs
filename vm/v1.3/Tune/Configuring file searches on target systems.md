---
title: "Configuring file searches on target systems"
excerpt: ""
---
If InsightVM gains access to an asset’s file system by performing an exploit or a credentialed scan, it can search for the names of files in that system.

File name searching is useful for finding software programs that are not detected by fingerprinting. It also is a good way to verify compliance with policies in corporate environments that don't permit storage of certain types of files on workstation drives:
* copyrighted content
* confidential information, such as patient file data in the case of HIPAA compliance
* unauthorized software

The application reads the metadata of these files. The application does not read nor retrieve file contents. You can view the names of scanned file names in the _File and Directory Listing_ pane of a scan results page.