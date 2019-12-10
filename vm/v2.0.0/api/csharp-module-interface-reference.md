---
title: "csharp-module-interface-reference"
excerpt: ""
---
# C# Module Interface Reference

This section describes interfaces that a C# attack module should implement.

## Interface ICSModuleFactory

A C# attack module should implement a class named CSModuleFactory (it will be loaded by AppSpider by name) which should be derived from the following interface:

`public interface` `ICSModuleFactory`

{

`bool `CreateModule(`Guid `moduleGuid, `out ``ICSModule `module);

}

| Method | Description |

| --- | --- |

| CreateModule | This function is invoked to create an instance of the Attack Module. Parameters: moduleGuid - GUID of the module. This parameter is used by the class factory to decide which module to instantiates if the DLL implements multiple Attack Modules. module [out, retval] - output parameter initialized with the module reference Return value: True - if operation was successful False - if operation failed |

## Interface ICSModule

Every Attack Module should implement the following interface:

`public interface` ICSModule

{

`void `Load(uint moduleRunnerId);

`void `InitForScan();

`void `UninitForScan();

`void `InitForAttackConfig();

`void `UninitForAttackConfig();

`void `InitForCrawlResult();

`void `UninitForCrawlResult();

`void `InitForAttackPoint();

`void `UninitForAttackPoint();

`bool `AttackPointIsRelevant();

`uint `CalculateNumberOfAttacks();

`bool `RunAttack(uint attackIndex);

`void `RunPassiveAnalysis();

}

| Method | Description |

| --- | --- |

| Load | 
 

This function is invoked immediately after a module is created by ICSModuleFactory::CreateModule. The purpose of this function in to bind a C# Attack Module object to a ModuleRunner object.

Parameters:

- moduleRunnerId - identifier of the module runner that was created by AppSpider for this instance of the module. The module should connect to the module runner object by creating a ModuleRunner COM class and passing moduleRunnerId to that class.

  |

| InitForScan | 
 

Not invoked, reserved for future versions

  |

| UninitForScan | 
 

Not invoked, reserved for future versions

  |

| InitForAttackConfig | 
 

Not invoked, reserved for future versions

  |

| UninitForAttackConfig | 
 

Not invoked, reserved for future versions

  |

| InitForCrawlResult | 
 

Not invoked, reserved for future versions

  |

| UninitForCrawlResult | 
 

Not invoked, reserved for future versions

  |

| InitForAttackPoint | 
 

Not invoked, reserved for future versions

  |

| UninitForAttackPoint | 
 

Not invoked, reserved for future versions

  |

| AttackPointIsRelevant | 
 

Not invoked, reserved for future versions

  |

| CalculateNumberOfAttacks | 
 

Calculates number of attacks for a given Attack Point and Attack Configuration. If the module is not interested in a given Attack Point it should return zero.

  |

| RunAttack | 
 

This function is invoked to run an active attack.

Parameters:

- 'attackIndex' is a zero-based index based on the number returned by function CalculateNumberOfAttack. If CalculateNumberOfAttacks returns 3, RunAttack will be invoked three times with attack indices 0, 1 and 2.

Return value:

- true: AppSpider should re-run the attack

-  false: there is no need to re-run the attack

  |

| RunPassiveAnalysis | 
 

This function is invoked to run passive analysis on the response.

  |

## What's Next?

<menuproxy data-mc-skin="/Project/Skins/SideMenu.flskn" mc-linked-toc="/Project/TOCs/as-custom-attack-module-api.fltoc" style="mc-toc-depth: 1;mc-context-sensitive: True;mc-include-parent: True;mc-include-siblings: True;mc-include-children: True;" madcap:conditions="General.Online_Only"></menuproxy>