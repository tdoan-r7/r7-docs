---
title: "module-configuration-file-reference"
excerpt: ""
---
# Module Configuration File Reference

The following table describes the Module Configuration file elements:

| Element | Description |

| --- | --- |

| ModuleId | 
 

A GUID that identifies the module.

  |

| DisplayName | 
 

The name of the module as it is presented to the user.

  |

| ModuleDescription | 
 

The description of the module that will be shown to the user.

  |

| ModuleFormat | 
 

The format of the module.

Valid values are:

- C#

  |

| Location | 
 

The location of the module binary code.

Valid values are:

- \<name of the module DLL\>

- Internal

  |

| ModuleTypes | 
 

The type of module.

Valid values are:

- Active (has attacks that send requests)

- Passive (has attacks that do not send requests)

Multiple values can be set. To set multiple values, the values should be separated by ‘|’ character, as follows:

Active | Passive

  |

| ModulePriority | 
 

The priority of the module. This value is used to schedule attacks with higher priority before attacks with lower priority.

Valid values are:

- High

- Medium

- Low

  |

| AttackModulePolicy | 
 

This is the default attack module policy that is placed in every scan configuration file for this module. It can be modified in the scan configuration, and it is the policy in the scan configuration that is used at run time.

  |

| AttackModulePolicy.Enabled | 
 

Specifies if the module should be enabled by default.

  |

| AttackModulePolicy.ModuleId | 
 

The GUID of the module. This is the same GUID as in ModuleId at the beginning of the page.

  |

| AttackModulePolicy.ModulePriority | 
 

Default module priority.

Valid values are:

- High

- Medium

- Low

  |

| AttackModulePolicy.Severity | 
 

Default severity of module findings.

Valid values are:

- Safe 
 
- Informational

- Low

- Medium

- High

  |

| AttackModulePolicy.MaxVulnLimit | 
 

Maximum number of vulnerabilities found by module after which AppSpider will stop running the module attacks for the scan.

  |

| AttackModulePolicy.MaxVarianceLimit | 
 

Maximum number of attack variances per root cause that AppSpider will try to create.

  |

| AttackModulePolicy. PassiveAnalysisOnAttacks | 
 

This element is obsolete and is not functional.

  |

| AttackModulePolicy. EnforceEncoding | 
 

Flags that tells AppSpider if it should encode attack payload.

  |

| AttackModulePolicy.AttackPoints | 
 

Described default attack point that should be attacked by this module.

Valid values are:

- Web Site

- Directory

- File

- Web Resource

- Parameter

- Response Analysis

Note that multiple values can be set. To set multiple values, the values should be separated by ‘|’ character, as follows:

Web Site | Directory| Parameter

N.B. The “Web Resource” string here correlates to the CrawlResult attack point in the API.

  |

| AttackModulePolicy. ParameterLocations | 
 

The default parameter locations that should be attacked by this module.

Valid values are:

- Directory

- File

- Path

- Query

- Fragment

- Post

- Http Header

- Cookie

- Referer

Multiple values can be set. To set multiple values, the values should be separated by ‘|’ character, as follows:

Query | Post | Cookie

  |

| AttackModulePolicy. RequestOriginations | 
 

The default request originations for which this module should be used.

Valid values are:

- HTML

- Form

- AJAX

- Flash

- Silverlight

- WSDL

Multiple values can be set. To set multiple values, the values should be separated by ‘|’ character, as follows:

Flash | Silverlight

  |

| DefaultAttackConfig | 
 

Describes default attack configuration. This structure contains default values of the parameters declared in AttackConfig structure in `attacks.cfg` file.

  |

| DescriptionList | 
 

List of vulnerability descriptions that are referenced from attack configurations.

  |

| RecommendationList | 
 

List of vulnerability recommendations that are referenced from attack configurations.

  |

| CustomParameterList | 
 

List of module-wide parameters that can be used to parameterize the module. The names and format of the parameters are defined by module writers.

  |

## What's Next?

<menuproxy data-mc-skin="/Project/Skins/SideMenu.flskn" mc-linked-toc="/Project/TOCs/as-custom-attack-module-api.fltoc" style="mc-toc-depth: 1;mc-context-sensitive: True;mc-include-parent: True;mc-include-siblings: True;mc-include-children: True;" madcap:conditions="General.Online_Only"></menuproxy>