---
title: "api-overview"
excerpt: ""
---
# Attack Module API Overview

AppSpider is a web application security scanner. Its main purpose is to discover exploitable security flaws in web sites and web services.

AppSpider has over 50 built-in Attack Modules. In some cases, you may want to add additional attacks that are specific to your environment. You have the ability to add or change attack payloads that existing Attack Modules send by modifying Module Configuration and Attack Configuration Files, but in some cases you may need to add a custom module that finds a new type of vulnerability or finds vulnerabilities using a different approach than the one used by our Attack Modules. For those cases, you can create custom Attack Modules that contain custom attack code.

All information for the custom attack module API covers interfaces and data structures that are available in AppSpider 6.14.015.

## How the scanner works

The AppSpider scanner is divided into two components: the Crawler and the Attacker. The Crawler crawls the web site and discovers all the requests that can be sent to the server. Those requests can be static pages, dynamic pages, or web service requests. The Attacker then takes the discovery data from the Crawler and audits all the requests for vulnerabilities. The Attacker uses Attack Modules to perform actual attacks. Each attack module is designed to discover a specific type of vulnerability. However, there may be cases in which the Attack Modules that are provided do not cover the type of vulnerability that you need. This is when you would need to build a custom Attack Module.

## Concepts

Before you can create a custom Attack Module, you should familiarize yourself with a few key concepts.

### Module declaration

A module declaration consists of several files:

- **Module Declaration File** - This is a file named `module.cfg`, which is an XML file that contains information about the Attack Module. For additional information, please see the [Module Configuration File Reference](module-configuration-file-reference.htm)."

- **Attack Declaration File** - This is a file named `attacks.cfg`, which is an XML file that contains declaration of the attacks. For additional information, please see the [Attack Configuration File Reference](attack-configuration-structure-reference.htm) section. 
 
- **Attack Module Dynamic Linked Library (DLL)** - This DLL is optional. The AttackModule DLL is created using C#. There is no requirement for the file name other than it must be referenced correctly in the `module.cfg` file by name, like in the following example: `<Location>SampleSQLi.dll</Location>`.

Generally speaking, there is not a requirement to have the module DLL in the same directory with the configuration file; it is just a convention. In some cases (e.g., when debugging attack modules), it may be easier to point in the `module.cfg` file to the DLL in the Visual studio output directory.

Attack modules are loaded from two locations:

- **AppSpider internal modules location** - The internal modules directory is located in `C:\Program Files (x86)\Rapid7\AppSpider 6\ScanEngine\Modules`.

- **User-specific location** - The directory that is used to store custom modules that you've developed is the directory you've specified during installation to store user specific data for AppSpider. By default, the directory is set to `%USERPROFILE%\Documents\AppSpider`.

These two locations both contain subdirectories, each of which represents an Attack Module. To add a new module, a new subdirectory should be created with a Module Configuration File and an Attack Configuration File.

### Attack declaration and default attack configuration

Module Attacks are declared in the `attacks.cfg` configuration file. You can look at the example SampleSQLi for a typical attacks.cfg file. This file contains a list of AttackConfig structures. Each attack is represented by one AttackConfig entry.

It is common to have multiple attacks in the Attack Configuration file. It is also common for an attack to have an almost identical structure with just a small number of fields that are specific to a particular attack. To avoid having redundant data in the attacks.cfg file, AppSpider allows the user to move data that is the same across all the attacks into the DefaultAttackConfig structure that is declared in the Module Configuration file. If a field is not defined in the AttackConfig structure, AppSpider reads the value from the DefaultAttackConfig structure. This is the reason why AttackConfig structures in the SampleSQLi module are so small; most of the data is read from the DefaultAttackConfig.

### API structure

The AppSpider Attack Module API is structured such that the functions implemented by the Attack Module have either no parameters, or a single integral parameter (see C# Interface section). The rest of the information necessary for actually performing an attack (e.g. the AttackPoint) is retrieved using a ModuleRunner object (see API Reference section). The ModuleRunner object should be explicitly instantiated by the attack module in its Load function:

`public void` Load(`uint` moduleRunnerId)

{

\_moduleRunner = `new` AttackerCOMLib.`ModuleRunner`();

\_moduleRunner.SetModuleInstanceID(moduleRunnerId);

}

After the ModuleRunner is created, the rest of the required data can be accessed through its interface, either directly or indirectly: AttackPoint object, Attack object, Attack Configuration, etc.

### Attack points

After crawling the entire web site, the attack space is divided into Attack Points. This division allows AppSpider to optimize attack execution, to make sure that the site is being attacked efficiently and to remove many redundant attacks on the framework level. While attacking an Attack Point, the API allows the Attack Module to perform only operations that are allowed for that Attack Point.

There are several types of attack points that are provided to the Attack Module:

- **Host Attack Point** - Host is the address of the name of website. For instance, http://www.webscantest.com. If the Attack Module wants to perform host-specific attacks, it should use this attack point. Note that the protocol is considered the part of the host.

- **Directory Attack Point** - Directory is the directory on the site. For instance, http://www.webscantest.com/datastore/. This attack point can be used by modules that need to perform directory analysis (e.g., check for some well-known files that may exist in the directory).

- **File Attack Point** - An example of a file attack point is http://www.webscantest.com/datastore/get\_item\_by\_id.php.

-  CrawlResult Attack Point. CrawlResult Attack Point is a request to the web site with all the parameters. If the module wants to inject attack payloads into existing requests, this is the Attack Point the module should use.

- **Parameter Attack Point** - Parameter Attack Point allows the Attack Module to apply the attack payload to a particular parameter on a request. Using Parameter Attack Points isolates the Attack Module from the knowledge of the format of the requests; the framework makes sure that the attack payload will be properly inserted into the requests, whether the parameter is a part of JSON post data, google toolkit data or simple query parameter.

#### How does AppSpider create attack points?

To understand how AppSpider creates an attack point, let's consider the following web page discovered by the Crawler: http://www.webscantest.com/datastore/store1/get\_item\_by\_id.php?id=3&name=Rake.

After receiving that data from the crawler, the attacker creates the following Attack Points:

- **Host Attack Point** - Host http://www.webscantest.com:80

- **Directory Attack Point** - Directory http://www.webscantest.com/datastore/

- **Directory Attack Point** - Directory http://www.webscantest.com/datastore/store1/

- **File Attack Point** - File http://www.webscantest.com/datastore/store1/get\_item\_by\_id.php

- **CrawlResult Attack Point** - For the entire request http://www.webscantest.com/datastore/store1/get\_item\_by\_id.php?id=3&name=Rake

- **Parameter Attack Point** - Parameter 'id' with value '3'.

- **Parameter Attack Point** - Parameter 'name' with value 'Rake'

After that, the module can decide which Attack Point it is interested in. There are two mechanisms to control that: Configuration Files (see Attack Config File reference, ParameterLocations element) or function CalculateNumberOfAttacks (see C# Interface section)

Note that if there are many requests that were discovered for host http://www.webscantest.com/, only one Host Attack Point is created, so that the Attack Module won't have to keep track whether it attacked that host or not. The same approach applies to other attack points. It is possible to have multiple Parameter Attack Points that point to the same parameter name and value, but those parameters will always come from different requests with a unique set of other request parameters.

### Configuration and Custom Parameters

Attack modules can be configured using custom parameters in module configuration files and attack configuration files. An example of a declaration of such a parameter is shown below

\<CustomParameterList\>

\<CustomParameter\>

\<Name\>ParameterName\</Name\>

\<Value\>\<![CDATA[ParameterData]]\>\</Value\>

\</CustomParameter\>

\</CustomParameterList\>

There are two separate custom configuration parameter lists:

- One in the ModuleConfig data structure, declared in the `module.cfg` file, and optionally added to using the ScanModulesParametersList in the scan configuration file.

- One in the AttackConfig data structure, declared in the `module.cfg` (in the DefaultAttackConfig element) and `attacks.cfg` files.

During module execution, the module can read those parameters using the following code.

-  For those in the AttackConfig data structure:

AttackerCOMLib.`IAttackConfiguration` attackConfig=\_moduleRunner.GetAttackConfig();  
  
attackConfig.CustomParameters.GetParameter("ParameterName");

- For those in the ModuleConfig data structure:

\_moduleRunner.GetParameters().GetParameter("ParameterName");

The ScanModulesParametersList is not normally found in scan configuration files. If it is to be used, it must be added by the user. The ScanModulesParametersList element is a child of the ScanConfig element, and there is one ScanModuleParameters element per module. If there are parameters that need to be available to more than one module, however, the null Guid may be used for the ModuleId to make parameters available to all modules.

An example structure is as follows:

\<ScanModuleParametersList\>

\<ScanModuleParameters\>

\<ModuleId\>FA48FA7E33B6407B8793D1993C3FF582\</ModuleId\>

\<CustomParameterList\>

\<CustomParameter\>

\<Name\>Module Specific Parameter 1\</Name\>

\<Value\>Specific Value 1\</Value\>

\</CustomParameter\>

\<CustomParameter\>

\<Name\>Module Specific Parameter 2\</Name\>

\<Value\>Specific Value 2\</Value\>

\</CustomParameter\>

\</CustomParameterList\>

\</ScanModuleParameters\>

\<ScanModuleParameters\>

\<ModuleId\>00000000000000000000000000000000\</ModuleId\>

\<CustomParameterList\>

\<CustomParameter\>

\<Name\>Global Parameter 1\</Name\>

\<Value\>Global Value 1\</Value\>

\</CustomParameter\>

\<CustomParameter\>

\<Name\>Global Parameter 2\</Name\>

\<Value\>Global Value 2\</Value\>

\</CustomParameter\>

\</CustomParameterList\>

\</ScanModuleParameters\>

\</ScanModuleParametersList\>

### Stateless Attack Modules

During the running of the scan, the attacker invokes the attack module multiple times. Every time it invokes the module method it creates a new ICSModule object. And for every one of those objects, it calls method ICSModule::Load to allow the module to bind to its ModuleRunner object. For instance, the object that was used to run CalculateNumberOfAttacks will be destroyed right after the call to that function, and a different object will be constructed for running the attack (by calling method ICSModule::RunAttack). The state of the object cannot be preserved between function calls. The exception, of course, is the method ICSModule::Load which is always called after a new object is constructed.

### Concurrency

AppSpider creates multiple threads to run multiple attacks. Each attack is executed from beginning to end in the same thread. However, it is possible that two instances of the same attack module will be executed at the same time. If the code of the attack module uses a shared resource, the attack module writer is responsible for synchronizing access to the shared resource.

## What's Next?

<menuproxy data-mc-skin="/Project/Skins/SideMenu.flskn" mc-linked-toc="/Project/TOCs/as-custom-attack-module-api.fltoc" style="mc-toc-depth: 1;mc-context-sensitive: True;mc-include-parent: True;mc-include-siblings: True;mc-include-children: True;" madcap:conditions="General.Online_Only"></menuproxy>