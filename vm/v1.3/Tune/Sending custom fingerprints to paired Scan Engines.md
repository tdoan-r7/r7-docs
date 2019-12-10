---
title: "Sending custom fingerprints to paired Scan Engines"
excerpt: ""
---
If you develop custom fingerprints, you can have the Security Console distribute them automatically to any paired Scan Engine that is currently in use when a scan is run. To do so, simply copy the fingerprint files to the [installation_directory]/plugins/fp/custom/ directory on your Security Console host.

You do not have to restart the Security Console afterward. The NSC.log file, located in the [installation_directory]/nsc/logs/ directory, will display a message indicating the location and number of the newly added fingperprints.

##Ensuring correct formatting for the fingerprints

Custom fingerprint XML files must meet certain formatting criteria in order to work properly, as in the following example:
```
<?xml version="1.0"?>
<fingerprints matches="ssh.banner">
<fingerprint pattern="^RomSShell_([\d\.]+)$">
<description>Allegro RomSShell SSH</description>
<example service.version="4.62">RomSShell_4.62</example>
<param pos="0" name="service.vendor" value="Allegro"/>
<param pos="0" name="service.product" value="RomSShell"/>
<param pos="1" name="service.version"/>
</fingerprint>
</fingerprints>
```
The first line consists of the XML version declaration.

The first element is a _fingerprints_ block with a matches attribute indicating what data the fingerprint file is intended to match.

The _matches_ attribute is normally in the form of _protocol.field_.

The _fingerprints_ element contains one or more _fingerprint_ elements.

Every fingerprint contains a _pattern_ attribute with the regular expression to match against the data.

An optional flags attribute controls how the regular expression is to be interpreted. See the [Recog documentation for FLAG_MAP](http://www.rubydoc.info/gems/recog/Recog/Fingerprint/RegexpFactory#FLAG_MAP-constant) for more information.

Each fingerprint contains a _description_ element with a human-readable string describing the fingerprint.

At least one _example_ element is included, though multiple example elements are preferable. These elements are used in test coverage present in rspec, which validates that the provided data matches the specified regular expression. Additionally, if the fingerprint is using the _param_ elements to extract field values from the data, you can add these expected extractions as attributes for the example elements. In the preceding example the string
```
<example service.version="4.62">RomSShell_4.62</example>
```
tests that *RomSShell_4.62* matches the provided regular expression and that the value of service.version is 4.62.

Each _param_ elements contains a _pos_ attribute that indicates what capture field from the pattern should be extracted, or 0 for a static string.

The _name_ attribute is the key that will be reported in a successful match, and the value will either be a static string for _pos_ values of 0 or missing and taken from the captured field.

##Best practices for creating fingerprints

Create a single fingerprint for each product as long as the pattern remains clear and readable. If that is not possible, separate the pattern logically into additional fingerprints.

Create regular expressions that allow flexible version number matching. This ensures greater probability of matching a product. For example, all known public releases of a product report either major.minor or major.minor.build format version numbers. If the fingerprint strictly matches this version number format, it would fail to match a modified build of the product that reports only a major version number format.

##Testing custom fingerprints via command line

You can test fingerprints via command line by entering executing *bin/recog_verify* against the fingerprint file:
```
$ bin/recog_verify xml/ssh_banners.xml
```
You can test matches via command line similarly:
```
$ echo 'OpenSSH_6.6p1 Ubuntu-2ubuntu1' | bin/recog_match xml/ssh_banners.xml -
MATCH: {"service.version"=>"6.6p1", "openssh.comment"=>"Ubuntu-2ubuntu1", "service.vendor"=
```