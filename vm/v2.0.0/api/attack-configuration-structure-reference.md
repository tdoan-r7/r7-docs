---
title: "attack-configuration-structure-reference"
excerpt: ""
---
# Attack Configuration Structure Reference

This section describes the meaning of the Attack Configuration structure elements (applies to the AttackConfig elements in the attacks.cfg file, as well as the DefaultAttackConfig element in the module.cfg file).

| Element | Description |

| --- | --- |

| Id | A unique identifier of the attack. |

| Description | A description of the attack. The description is used in the AppSpider GUI to show the description of the attack module. |

| Enabled | 1 - if the attack configuration is enabled, 0 - if disabled |

| AttackClass | 
 

The attack class. Valid values are:

- Application Developer

- Server Administrator

- Database Administrator 
 
- Best Practice

- Privacy

- Reflection

- External Active Content

  |

| AttackType | The type of the attacks. It should be one of those declared in the ScanEngine/Config/SystemConfig.xml file. |

| Version | Version of the attack. |

| Copyright | Copyright information of the attack. |

| DescriptionDocId | The ID of the description of a vulnerability discovered by this attack. The ID is used to find the corresponding description in the Module Configuration File. |

| RecommendationDocId | The ID of the recommendation for this vulnerability. The ID is used to find the corresponding recommendation in the Module Configuration File. |

| ComplianceDescriptionDocId | The ID of the compliance description for this vulnerability. The ID is used to find the corresponding compliance description in the Module Configuration File. |

| ComplianceRecommendationDocId | The ID of the compliance recommendation for this vulnerability. The ID is used to find the corresponding compliance recommendation in the Module Configuration File. |

| Severity | 
 

Default severity of the vulnerabilities found by this attack. The valid values are:

- Safe

- Informational 
 
- Low

- Medium

- High

  |

| Advanced | This flag is used by the scheduler to determine on what attack points the attack should be performed. If the value of this parameter is set to 1, then the scheduler will try to reduce number of times this attack will be executed on duplicated parameter attack points. |

| PassiveAnalysisOnAttacks | Obsolete; not functional. |

| DoNotUseSession | Unused for custom attack modules. |

| AttackSequences | If set to 0, attack will not be run in the context of sequences (default value is 1). |

| AttackInjectedParameter | This flag tells whether AppSpider should run this attack on the injected parameter (see interface IAttackerParameter for details). |

| AttackControllingParameterOnly | If set to 1, AppSpider will run the attack only on parameters which cause changes in the response (controlling parameters). |

| AttackPersistentReflection | If set to 1, the attack will run on parameters showing persistent reflection (default value is 0).  |

| AttackBinary | Tells AppSpider whether it should run this attack to attack requests that received binary responses during crawling. |

| AttackExtension | Tells AppSpider to attack only links with the specified file extensions (comma delimited list). |

| DoNotAttackExtension | Tells AppSpider to not attack links with the specified file extensions (comma delimited list). |

| AttackContentType | Tells AppSpider to attack only links that had responses with the specified Content-Type header (comma delimited list). |

| DoNotAttackContentType | Tells AppSpider to not attack links that had responses with the specified Content-Type header (comma delimited list). |

| ParameterValueTypes | 
 

Tells that AppSpider should use this attack to only attack parameters with the specified parameter value types. Valid values are:

-  UnknownInputType

- Base64

- Base64MS

- DateYMD

- DateMDY

- DateDMY

- Digit

- EpochTime

- PathFile

- HashMD5

- Url

- UserPassWord

- Alpha

- AlphaNumeric

- AllTypes

Note that multiple values can be set. To set multiple values, the values should be separated by ‘|’ character, as follows:

Base64 | UserPassWord | AlphaNumeric

  |

| AnalysisRequirements | 
 

Tells AppSpider whether or not to perform parameter analysis. Valid values are:

- No Analysis Requirements 
 
- Injected Reflecting Parameter 
 
- Controlling Parameter

Note that multiple values can be set. To set multiple values, the values should be separated by ‘|’ character, as follows:

Injected Reflecting Parameter | Controlling Parameter

Notes:

1. The default value is the combination of “Injected Reflecting Parameter” and “Controlling Parameter.” Currently, there is no functional difference between these two values. Specifying either or both will result in full parameter analysis being performed. At present, then, this is a boolean flag.

2. For custom modules, this value should be set to “No Analysis Requirements” unless either:

1. AttackControllingParameterOnly is set to 1 (true), or 
 
2. ParameterValueTypes has a value other than either UnknownInputType or AllTypes.

In the cases where parameter analysis is necessary as noted, the attack execution will depend on the results of the parameter analysis. For example, if the attack is only for controlling parameters, the attack will only be run for parameters that have been found by parameter analysis to be controlling parameters. In this situation, the AnalysisRequirements value must be set accordingly to ensure that the analysis is actually performed.

If the attack requires analysis, but analysis is never performed, then no parameters will meet the criteria, and the attack will never be run. Conversely, if the attack does not require parameter analysis, then AnalysisRequirements should be set to “No Analysis Requirements” to avoid unnecessary time-consuming analysis.

  |

| CWEID, CAPEC, DISSA\_ASC, OWASP2007, OWASP2010, OWASP2013, OVAL, WASC | 
 

Ids of the vulnerability type according the various standards.

  |

| Encoding | 
 

Determines how parameter values should be encoded.

Valid values are:

- No Encoding

- Percent Encoding

Note that multiple values can be set. To set multiple values, the values should be separated by ‘|’ character, as follows:

No Encoding | Percent Encoding

  |

| AttackPoints | 
 

Describes the attack point for which this attack should be invoked. Valid values are:

- Web Site

- Directory

- File

- Web Resource

- Parameter

- Response Analysis

Note that multiple values can be set. To set multiple values, the values should be separated by ‘|’ character, as follows:

Web Site | Directory | Parameter

N.B. The “Web Resource” string here correlates to the CrawlResult attack point in the API.

  |

| ParameterLocations | 
 

Describes parameter locations that should be attacked with this attack. Valid values are:

- Directory

- File

- Path

- Query

- Fragment

- Post

- Http Header

- Cookie

- Referer

Note that multiple values can be set. To set multiple values, the values should be separated by ‘|’ character, as follows:

Query | Post | Cookie

  |

| Schedule | 
 

For passive attacks only. If set to 1, the attack will be scheduled to run later in the scan (as though it is an active attack) instead of running immediately during crawl (default value is 0).

  |

| RequestOriginations | 
 

Depending on where link was found, it can be attackable by this attack or not. This element specified what links should be attacked based on where they were found.

Valid values are:

- HTML

- Form

-  AJAX

- Flash

-  Silverlight

-  WSDL

Note that multiple values can be set. To set multiple values, the values should be separated by ‘|’ character, as follows:

Flash | Silverlight

  |

| COMPLIANCE\_HEADERS | Lists headers that should be used to create the compliance report entry for this vulnerability. |

| LanguageList | List all languages for which that attack config should be used. |

| RegionList | List all geographical regions for which this attack config should be used. |

| CustomParameterList | 
 

List of parameters that can be used to parameterize attack behavior. Attack module has access to those parameter during attack execution. The names and format of the parameters are defined by module writers.

See “Access to configuration and custom parameters” for an example parameter.

  |

| Discard404 | Checked by PreProcessResponse (multiple interfaces). Set to 1 to discard 404 responses. Uses same logic as IResponse.Is404 (see reference for that interface for details). |

| ResponseCode | Checked by PreProcessResponse (multiple interfaces). Allows responses only with the code(s) listed (comma delimited list). |

| ForbiddenResponseCode | Checked by PreProcessResponse (multiple interfaces). Disallows responses with the code(s) listed (comma delimited list). |

| ResponseContentType | Checked by PreProcessResponse (multiple interfaces). Allows responses only with the content type(s) listed (comma delimited list). |

| ResponseContentCharset | Checked by PreProcessResponse (multiple interfaces). Disallows responses with the content type(s) listed (comma delimited list). |

| ResultsFeedback | If set to 1, traffic from a successful attack will be fed back into the crawler for additional discovery and possible attacking by all modules (default is 1).  |

| TechnologyTargets | This element is for possible future use; it is currently not functional. |

| BypassWinInet | This element is not used for custom attack modules. |

## What's Next?

<menuproxy data-mc-skin="/Project/Skins/SideMenu.flskn" mc-linked-toc="/Project/TOCs/as-custom-attack-module-api.fltoc" style="mc-toc-depth: 1;mc-context-sensitive: True;mc-include-parent: True;mc-include-siblings: True;mc-include-children: True;" madcap:conditions="General.Online_Only"></menuproxy>