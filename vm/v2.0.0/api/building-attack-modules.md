---
title: "building-attack-modules"
excerpt: ""
---
# Building Attack Modules 
 

The Attack Module SDK includes the SampleSQLi attack module, which you can use to build a custom attack module. The SampleSQLi attack module injects an attack payload that intentionally contains invalid SQL syntax and then looks for common SQL errors in the response. The SampleSQLi module is implemented to attack Parameter Attack Points and only has code specific to those attack points. You can attack other attack points similarly, but the implementation of the function ICSModule::RunAttack would look different.

## Creating the configuration files

To register an Attack Module, at least two files should be created in a module-specific subdirectory in the `C:\Program Files (x86)\Rapid7\AppSpider 6\ScanEngine\Modules`. Please create a directory 'SampleSQLi' in directory `C:\Program Files (x86)\Rapid7\AppSpider 6\ScanEngine\Modules\`. Then copy into 'SampleSQLi' directory the `attack.cfg` and `module.cfg` files from the SampleSQLi example.

## Creating a DLL project

The SampleSQLi example already has a project setup that creates a DLL, so there is no need to create a new project. If you create a new module you will have to create a new C# Class Library project.

## Implementing the class factory

To be able to create a module, AppSpider expects the Attack Module DLL to implement a class named `CSModuleFactory`, derived from the ICSModuleFactory interface. Every time a module is created, AppSpider instantiates the factory and calls the `ICSModuleFactory::CreateModule` method.

Below is the implementation of the CSModuleFactory class:

`class` `CSModuleFactory` :` ICSModuleFactory`

{

`public bool` CreateModule(`Guid `moduleGuid, `out ``ICSModule` module)

{

`Guid `correctGuid = `new ``Guid`("25A9426A-3E12-4B98-A573-5208460C91A1");

`if `(correctGuid == moduleGuid)

module = `new ``SampleSQLi`();

`else`

module = `null`;

`return` module != `null`;

}

}

Note that the same attack module DLL can host several attack modules. The class factory will know which attack module class it should create by using parameter 'moduleGuid' which contains the GUID of the module that AppSpider wants to create.

## Implementing the ICSModule interface

An attack module must implement the ICSModule interface (see C# Interface section for details). The minimal implementation of the module should include implementation of the following functions:

-  Load

-  CalculateNumberOfAttacks

- RunAttack (for active attacks that send network requests) or RunPassiveAttack (for passive attacks that analyze responses from the Crawler and do not send network requests)

### Implementing ICSModule::Load

This function is called every time a module instance is created. The purpose of this function is to let Attack Module connect to the ModuleRunner object created specifically for this instance of the AttackModule. Below is the code from method ICSModule::Load implemented in the SampleSQLi example:

`class` `SampleSQLi` : `ICSModule`

{

AttackerCOMLib.`IModuleRunner` \_moduleRunner;

`public void` Load(`uint` moduleRunnerId)

{

\_moduleRunner = `new` AttackerCOMLib.`ModuleRunner`();

\_moduleRunner.SetModuleInstanceID(moduleRunnerId);

}

.....

}

As you can see, the class has a member variable \_moduleRunner that is initialized in ICSModule::Load function. The member \_moduleRunner will be used by the module in subsequent calls to access data specific to this instance of the module: Attack Point, Attack Config, etc.

### Implementing ICSModule::CalculateNumberOfAttacks

The purpose of this function is to let module tell AppSpider how many attack it needs to run on a given Attack Point with a given Attack Config. Below is the implementation of the function in example SampleSQLi:

`public uint` CalculateNumberOfAttacks()

{

AttackerCOMLib.`IAttackPoint` attackPoint = \_moduleRunner.GetAttackPoint();

`if` (attackPoint.Type == AttackerCOMLib.`AttackPointType`.ATTACKPOINT\_PARAMETER)

{

// This module only performs parameter attacks.

`return 1`;

}

`else`

{

`// Other attack points are:`

`// CrawlResult`

`// File`

`// Directory`

`// Host`

`return` 0;

}

}

Because this module only attacks Parameter Attack Points, and runs one attack per parameter, it returns one for Parameter Attack Points, and zero for all other Attack Points.

In the example given here, the only criterion used is the type of the Attack Point, and only one attack is scheduled. However, an attack module may utilize other criteria, completely at the discretion of the module itself, based on information in the Attack Point. This can result in zero attacks being the return value, or more than one attack. During the attacking phase, RunAttack is called with an index for each attack. For example, if CalculateNumberOfAttacks returns 3, then RunAttack is called with indices 0 through 2.

For example, if the attack point needs to meet certain criteria for a particular attack to be relevant, that can be determined here and the attack point excluded from attacking for this attack point by returning zero. This will prevent unnecessary scheduling of attacks. Alternatively, an attack module could have a certain number of variants to be tried. CalculateNumberOfAttacks could return that number so that each variant gets its own invocation of RunAttack.

The implementation of this function should be compatible with the AttackPoints members of the AttackConfig structure and AttackModulePolicy structure in the module.cfg and attacks.cfg files. In particular, the test for Attack Point type should normally be the same. For example, if the AttackPoints in the config files specifies only File Attack Points, but CalculateNumberOfAttacks only allows Directory Attack Points, then no attack will ever be scheduled. This is because CalculateNumberOfAttacks will only be called by the framework for File Attack Points. While checking for the same attack point type in both places is redundant, it does help for clarity.

### Implementing ICSModule::RunAttack

In ICSModule::RunAttack, the SampleSQLi module does the following actions:

- Accesses Data from Module Runner

- Provides custom attack payload

- Sends request

-  Analyzes response

-  Creates vulnerabilities

#### Accessing Data from the Module Runner

As it was mentioned before, nearly all of the information required for attacking is provided to the module via the ModuleRunner object. SampleSQLi module uses the ModuleRunner to retrieve the objects required to perform an attack. Below is the code from the example:

AttackerCOMLib.`IAttackConfiguration` attackConfig = \_moduleRunner.GetAttackConfig();

AttackerCOMLib.`IAttackPoint` attackPoint = \_moduleRunner.GetAttackPoint();

AttackerCOMLib.`IParameterAttackPoint` parameterAttackPoint = (AttackerCOMLib.IParameterAttackPoint)attackPoint;

AttackerCOMLib.`IParameterAttack` parameterAttack = parameterAttackPoint.GetParameterAttack();

Note that ModuleRunner::GetAttackPoint returns an IAttackPoint interface. Because the module attacks Parameter Attack Points, it needs to cast 'attackPoint' to interface IParameterAttackPoint to get access to functionality that allows attacking a parameter.

#### Providing the custom attack payload

A typical attack that attacks a Parameter Attack Point performs two actions:

- It injects the attack payload into the parameter.

- It checks the response for something that indicates a vulnerability.

The code below from the SampleSQLi module injects the attack payload into the parameter value:

1 `string` originalValue = parameterAttackPoint.AttackParameter.OriginalValue;

2 `string` attackString = attackConfig.CustomParameters.GetParameter("AttackString");

3 `string` attackValue = attackString + originalValue;

4 parameterAttack.ParameterValue = attackValue;

Here's a breakdown of what's happening in each line:

- **Line 1** - The module reads the original value of the parameter, the value that the crawler discovered.

- **Line 2** - The module reads the attack payload from the AttackConfig structure (see files module.cfg and attacks.cfg) via the Attack Module API.

- **Line 3** - The module prepends the attack payload to the original value of the parameter.

- **Line 4** - The module tells AppSpider to use the new value of the parameter (with attack payload).

#### Sending the request to the server

After the module provides the attack payload to AppSpider, it needs to send the request with the parameter value that contains the attack payload. The SampleSQLi module achieves that with the following call:

AttackerCOMLib.`IResponse` attackResponse = parameterAttack.SendNextRequest();

The name of the method includes the word “next” which is key to its context: sequences. Parameter attacks and CrawlResult attacks can be part of multiple step sequences. Based on various criteria, the framework selects one or more steps in a given sequence for attack. Each is considered a separate attack and warrants a separate invocation of RunAttack. The framework pre-runs the steps in the sequence before the attack step before invoking RunAttack. It then remains for the attack module to run the attack step, and any more steps in the sequence it desires to do so, each with a separate call to SendNextRequest. When the sequence is finished, SendNextRequest returns null instead of sending a request. For simplicity, attacks that are not sequences are treated by the framework as a sequence with only one step.

N.B. The uint parameter of RunAttack does not indicate a sequence step. It is the attack id, and correlates to the number returned by CalculateNumberOfAttacks, as discussed above. The API does not tell the module the current step of the sequence, nor how many steps there are.

SendNextRequest should normally be run in a loop that exits upon null return of SendNextRequest. A simplified version would look like this:

`for` (; ; )

{

AttackerCOMLib.`IResponse` originalResponse = parameterAttack.OriginalResponse;

AttackerCOMLib.`IResponse` attackResponse = parameterAttack.SendNextRequest();

`if` (attackResponse == null)

`break`; `// end of sequence`

`if` (!parameterAttack.PreProcessResponse())

`continue`; `// built-in checks did not pass`

`// TODO: Analyze response`

}

After SendNextRequest, a set of built-in checks should be executed by calling PreProcessResponse. For all attack types, it verifies several entries in the AttackConfig: Discard404, ResponseCode, ForbiddenResponseCode, ResponseContentCharset, and ResponseContentType.

For sequence attacks, PreProcessResponse additionally checks each step of the sequence against the criteria for “attackability.” That is, that if the framework would not schedule a given step of a sequence as an attack step, then it should be excluded from having a vulnerability found for it when executed after the attack step.

For example, if the framework scheduled the second step of a five step sequence for attack, then the attack module can (and probably should) send requests two through five. But if step three would not have been scheduled itself for attack, then the attack module should not find a vulnerability for that step, even though it must be executed to get from step two to steps four and five, which might be allowed to have vulnerabilities. In this case, PreProcessResponse will return false for step three, but might still return true (contingent on the other checks) for the succeeding steps.

Using PreProcessResponse is not absolutely required. Unless there is a very good reason specific to the attack module, however, it should always be called and its return value respected.

#### Analyzing responses and adding vulnerabilities

IParameterAttack::SendNextRequest returns the IResponse object that contains the response from the server. This response can be analyzed to detect a vulnerability. If the response passes the checks of PreProcessResponse, then further checks can be implemented in the module. Given that the SampleSQLi module intentionally injects invalid SQL syntax, it expects to find in the response some common SQL error. This is achieved by the code below:

`string` vulnRegex = attackConfig.CustomParameters.GetParameter("VulnRegex");

`Match `match = `Regex`.Match(response.Body, vulnRegex, `RegexOptions`.IgnoreCase);

`if` (match.Success)

{

`// Check the match against the original response to prevent false positive.`

`string` errorString = match.Value;

`string` originalBody = originalResponse.Body;

match = `Regex`.Match(originalBody, vulnRegex, `RegexOptions`.IgnoreCase);

`if` (match.Success && errorString == match.Value)

`continue`; `// The matched string was in the original response`

AttackerCOMLib.`IResult` result = parameterAttack.CreateResult();

result.AttackValue = attackValue;

result.ErrorString = match.Value;

\_moduleRunner.SaveResult(result);

}

A typical way of checking for false positives is included above. The same regular expression is applied to both the attack response and original response. If the same result is obtained, it is excluded as a vulnerability, and the sequence continued. This may or may not be applicable to any individual attack, but it is included here to illustrate a typical implementation.

N.B. The original request and/or response used for this or similar purpose must be obtained from the attack object before calling SendNextRequest. The example code shows this (see above). Once SendNextRequest is called, the underlying iterator will have moved forward one step in the sequence and will be incorrect for the current step.

When a module detects a vulnerability, it needs to create an IResult object and initialize it with vulnerability details. The code above shows how the SampleSQLi module achieves that.

#### SendNextRequest vs SendRequest

Parameter attacks and CrawlResult attacks are derived from interface ISequenceCapableAttack. For these attacks, use of SendNextRequest is available. All other attacks must use SendRequest instead. These attacks correlate to host, directory, and file attack points. In these cases, the attack must first be set up using CreateRequest. Once this is done, the request configured by the attack module is sent using SendRequest.

With Parameter attacks, normally SendNextRequest is used, but the CreateRequest/SendRequest pair can be used, as well. Typically this would be done to send requests outside the sequence provided for attacking. As many CreateRequest/SendRequest pairs as desired may be sent without affecting the progress of the sequence in the framework. Care should be taken, however, as this may affect the behavior of the sequence on the server side.

Alternatively, CreateRequest can be used to replace a step in the sequence. In this case, CreateRequest is called followed by SendNextRequest with no intervening SendRequest. Be sure this is what is desired. For parameter attacks, this approach should probably never be used for the attack step of a sequence (i.e., before calling SendNextRequest for the first time), as it will replace the request that would otherwise contain the altered parameter value (set by parameterAttack.ParameterValue).

#### Return Value

RunAttack can be run with multiple iterations. This is controlled by the return value of RunAttack. Normally, there will be only one iteration, and RunAttack should return false. However, if the return value is true, the attack is re-run. RunAttack is immediately called with the same index. If there is a sequence involved, it is started from the beginning just as with the first iteration of RunAttack, and the designated attack step of the sequence remains the same. This option should be used instead of using a larger return value from CalculateNumberOfAttacks in the following scenarios:

- When the attack should be re-run may not be known until after at least one attack has been executed.

- When a series of attack variants should be run together, and their results compared with each other. This is possible because the object state is maintained between calls to RunAttack when the return value from RunAttack is false. This is by design.

An example of an attack module that utilizes multiple RunAttack iterations is Blind SQL, where a series of requests must be sent and the results compared.

Additional points:

- Do not confuse attack iterations with sequence steps or attack indices. An attack with a given attack index can be iterated (re-run) an arbitrary number of times (by returning false from RunAttack), each of which will restart the sequence (if one exists).

- Care should be taken to avoid an infinite loop by ensuring that RunAttack returns false after a finite number of iterations.

## Using the CSModule Base Class to Implement ICSModule

NTO has created a C# base class that may be used to help create attack modules: class CSModule. This class inherits from the ICSModule interface and already provides a great deal of the necessary boilerplate code necessary for implementing an attack module. Custom attack modules can inherit from CSModule and override the appropriate methods to complete the implementation of ICSModule. Use of CSModule is optional altogether, but even if not used, it provides a reference for canonical attacking generally.

Please note the following with respect to class CSModule:

- CSModule does not implement ICSModuleFactory. The factory method CreateModule still needs to be implemented by the custom module.

- ICSModule.Load is implemented by CSModule and does not need to be implemented by the derived custom class.

- ICSModule.CalculateNumberOfAttacks has a stub implementation in CSModule. It must be overridden by the derived class if active attacks are involved.

-  ICSModule.RunAttack is implemented by CSModule and should not normally need to be overridden by the derived class. Instead, the appropriate methods called from RunAttack should be overridden, depending on the kind of attack.

### Parameter Attacks with the CSModule base class

An example parameter attack using the CSModule class is contained in the SampleSQLi\_CSM attack module that comes with the Attack Module SDK. The functionality is the same as the SampleSQLi example, but it uses base class CSModule.

In the case of Parameter Attacks, the appropriate CSModule methods that need to be overridden for RunAttack to work are SetupParameterAttack and ProcessSequenceCapableAttackResponse.

#### Overriding SetupParameterAttack

CSModule.RunAttack calls CSModule.SetupAttack (always) which in turn calls SetupParameterAttack for the case of a Parameter Attack Point. The primary task is to set the value on the ParameterValue property of the IParameterAttack object. If for some reason there is a problem with setting up the attack, this function can return false, and the attack will not be executed.

In the example code, SetupParameterAttack also stores some local variables: the attack value (a string) and a reference to the Attack Config object. These members are used later in ProcessSequenceCapableAttackResponse. As noted above, the state of the attack module cannot be guaranteed between calls to functions in interface ICSModule. However, object state can be safely relied upon during a single such call. Since both method SetupParameterAttack and method ProcessSequenceCapableAttackResponse are called ultimately from a single invocation of ICSModule.RunAttack, using member variables for this purpose is perfectly safe.

#### Between SetupParameterAttack and ProcessSequenceCapableAttackResponse

After setting up the attack using SetupParameterAttack, CSModule.RunAttack will call CSModule.RunAttackLoop, which performs the standard activities common for an active attack. These include retrieving the original response object for comparison purposes, calling SendNextRequest, and calling PreProcessResponse. Unless there is some compelling reason to not do these things or to do them differently, it is recommended not to override RunAttackLoop.

#### Overriding ProcessSequenceCapableAttackResponse

After performing the standard set of active attack operations, RunAttackLoop will call ProcessSequenceCapableAttackResponse. The same function is used for both Parameter Attacks and CrawlResult Attacks.

In the SampleSQLi\_CSM module, the implementation of ProcessSequenceCapableAttackResponse does the regular expression comparisons and creates IResult objects as appropriate. The return value of this function determines whether or not a sequence (if there is one) should be continued. Normally continuation will be desired, and the return value for continuation is true.

### CrawlResult Attacks with the CSModule base class

An example CrawlResult attack using the CSModule class is contained in the SampleCSRF attack module that comes with the Attack Module SDK. In the case of CrawlResult Attacks, the appropriate CSModule methods that need to be overridden for RunAttack to work are SetupCrawlResultAttack and ProcessSequenceCapableAttackResponse. This example also serves to illustrate some other aspects of using the Attack Module API, described below.

### Using CalculateNumberOfAttacks to check criteria other than AttackPoint type

As noted above, CalculateNumberOfAttacks can be used to apply any criteria desired to determine if an attack should be scheduled or not. In this example module, CalculateNumberOfAttacks applies a few more criteria beyond simply checking the AttackPoint type. Note that these particular checks are specific to this module, are not somehow linked to CrawlResult attacks vs other sorts of attacks, and should not be generalized. They are here for illustration purposes only.

- The response code of the AttackPoint’s response must be either 200 or 302.

- The original response must not be a “404” response. Note that the response code is not checked directly. Instead, IResponse.Is404 is called. Many websites use HTTP 404, but others may use a custom page with a 200 response to indicate a “not found” condition. During the crawling phase, the NTO scan engine applies a proprietary algorithm to determine the “not found” page or response specific to the website being scanned. IResponse.Is404 is used to determine if a specific response qualifies as the identified “not found” condition.

- The original request must have a POST body. This implementation determines if this is so by iterating through the attackable parameter list for the request and checking to see if one of them has a POST location.

N.B. There is a mismatch between the terminology in the Attack Module API and the AttackPoints members of the configuration files. The Attack Module API refers to a “CrawlResult” attack point, and the configuration files refer to a “Web Resource” attack point. For the purposes of attacking, these are synonyms. For a CrawlResult attack to work, the AttackPoints members in the configuration files need to include “Web Resource” and the code needs to test for CrawlResult attack points. See the relevant reference sections for details.

#### Overriding SetupCrawlResultAttack

CSModule.RunAttack calls CSModule.SetupAttack (always) which in turn calls SetupCrawlResultAttack for the case of a CrawlResult Attack Point. All of the comments above about overriding SetupParameterAttack apply here except one: there is no one single ParameterValue on the IParameterAttack object to be set. Instead, there are three options available:

- Set multiple parameter values using ICrawlResultAttackPoint.GetParameter to retrieve individual IAttackerParameter objects, and then calling ICrawlResultAttack.SetParameterValue to set the values for those desired.

-  Retrieve the original request using ICrawlResultAttack.AttackedRequest, and modify the request as desired.

- Create an entirely new request using IBaseAttack.CreateRequest, and set it up as desired.

In the example code, the option to modify the retrieved AttackedRequest is used. It might be wondered why using the approach of setting the “referer” attacker parameter is not used instead. In this case, there probably will be no “referer” in the original request, and thus no such parameter. Thus, the “referer” header is added (or changed if present) by calling IRequest.SetHeader.

#### Overriding ProcessSequenceCapableAttackResponse

As with parameter attacks, RunAttackLoop will call ProcessSequenceCapableAttackResponse.

In this particular example, regular expressions are not used to detect a vulnerability. Instead, response signatures are used. NTO response signatures utilize a proprietary algorithm to characterize the general structure of a page while allowing for differences in detail. This allows for detection of the “equality” of two responses that may contain different recordsets from the same database, but are otherwise the same structurally. In this example attack, if the response with a spoofed referer has the same signature as the response without, the attack is deemed to have found a vulnerability.

The use of regular expressions to find vulnerabilities in the parameter attack example, and the use of signatures to find vulnerabilities in the crawl result attack example, should not be taken to imply linkage of concepts. Signatures and regular expressions can, of course, be used with any attack type.

### Other Types of Attacks with the CSModule base class

To implement for non-parameter attack points, the CSModule base class has other functions to be overridden. The logic of the base class implementation along with the included comments should be used to guide the implementor in deciding which methods should be overridden. Typically, the only methods that should be overridden are the stub methods that would throw a NotImplementedException if not overridden. As the example indicates, not all of them need to have an override, but only those necessary for the attack point(s) used by that module. If the correct methods are not chosen, this would typically manifest during debugging with a NotImplementedException. Overriding other methods than these is, of course, possible, but only appropriate in exceptional circumstances.

## What's Next?

<menuproxy data-mc-skin="/Project/Skins/SideMenu.flskn" mc-linked-toc="/Project/TOCs/as-custom-attack-module-api.fltoc" style="mc-toc-depth: 1;mc-context-sensitive: True;mc-include-parent: True;mc-include-siblings: True;mc-include-children: True;" madcap:conditions="General.Online_Only"></menuproxy>