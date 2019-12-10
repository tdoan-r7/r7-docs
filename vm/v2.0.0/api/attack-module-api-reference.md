---
title: "attack-module-api-reference"
excerpt: ""
---
# Attack Module API Reference

The Attack Module API is a COM-based API. The type library for the API is located in AttackerCOM.dll. To access the type library, the C# client should include in the project a reference to COM component 'AttackerCOMLib'.

## Return Values

This documentation is from a simplified COM point of view; that is, the methods and properties are all functions that all have an HRESULT return value. When imported into C# this is transformed, such that the COM properties will become C# properties with the relevant type, and methods will either return void, or will have a return value of the [out, retval] parameter.

## Input Ranges

The input ranges of the various writable properties and method input parameters are not documented in detail. Common sense should apply based on the property or parameter in question, and the implementor is presumed to have relevant knowledge of the HTTP protocol to make such judgments.

## enum AttackPointType

This enumerator described the type Attack Point. The following are the values of the enumerator:

| Value | Description |

| --- | --- |

| ATTACKPOINT\_HOST | The attack point represents a host. |

| ATTACKPOINT\_DIR | The attack point represents a directory. |

| ATTACKPOINT\_FILE | The attack point represents a file. |

| ATTACKPOINT\_CRAWLRESULT | The attack point represents a unique request. |

| ATTACKPOINT\_PARAMETER | The attack point represents a parameter in a request. |

| ATTACKPOINT\_RESPONSE | The attack point represents a response for one of the requests sent by the crawler. |

## enum ParameterLocation

This enumerator describes the parameter location. The following are the values of the enumerator:

| Value | Description |

| --- | --- |

| PARAMETERLOCATION\_DIR | The parameter is located in the directory part of URI. |

| PARAMETERLOCATION\_FILE | The parameter is located in the file name part of the URI. |

| PARAMETERLOCATION\_PATH | The parameter is located in the path part of the URI. |

| PARAMETERLOCATION\_QUERY | The parameter is a query parameter. |

| PARAMETERLOCATION\_FRAGMENT | The parameter is located in the fragment (after # character) part of the URL. |

| PARAMETERLOCATION\_POST | The parameter is located in the body of the request. |

| PARAMETERLOCATION\_HEADER | The parameter is one of the headers of the HTTP request. |

| PARAMETERLOCATION\_COOKIE | The parameter is a cookie. |

| PARAMETERLOCATION\_REFERRER | The parameter is the referrer HTTP header. |

## enum ParameterType

This enumerator described the type of the parameter as it was determined by AppSpider.

| Value | Description |

| --- | --- |

| PARAMETERTYPE\_UNCATEGORIZED | AppSpider was not able to categorize parameter. |

| PARAMETERTYPE\_OPERATOR | The parameter value indicates an operation, e.g. ‘deleteuser’. |

| PARAMETERTYPE\_SESSION | The parameter contains session information. |

| PARAMETERTYPE\_DATAQUERY | The parameter is used to retrieve data. |

| PARAMETERTYPE\_ONETIMETOKEN | The parameter is a one-time token (usually a hidden parameter in forms to prevent submission of the same form). |

## enum DataStorageScope

This enumerator describes the scope in which module data should be stored.

| Value | Description |

| --- | --- |

| DATASTORAGESCOPE\_ATTACKPOINT | The module data should be stored for Attack Point. |

| DATASTORAGESCOPE\_CRAWLRESULT | The module data should be stored for CrawlResult. |

| DATASTORAGESCOPE\_PATH | The module data should be stored for a specific path. |

| DATASTORAGESCOPE\_HOST | The module data should be stored for a host. |

| DATASTORAGESCOPE\_GLOBAL | The module data should be stored in global area and can be accessed from everywhere. |

## interface ISignature

Interface ISignature allows operations on response signatures.

| Method/Property | Description |

| --- | --- |

| IsEqual | 
 

This method compares signatures of two responses.

Parameters:

- pVal - the signature object this signature is being compared with

- pbEqual [out, retval] - returns TRUE if signatures are equal or FALSE otherwise

  |

## interface IResponse

Interface IResponse provides access to the HTTP response data received from the server.

| Method/Property | Description |

| --- | --- |

| Code | 
 

This read-only property provides access to the HTTP response code.

Type: unsigned long

  |

| Headers | 
 

This read-only property provides access to the HTTP headers of the response.

Type: string

  |

| Body | 
 

This read-only property provides access to the body of the response.

Type: string

  |

| CreateSignature | 
 

This method creates a signature of the response.

The signature can be used to compare this response with other responses.

Parameters:

- pVal [out, retval] - the signature of the response

  |

| Is404 | 
 

Tests whether response is a 'page not found' response. It can be a standard 404 response or a custom 200 response. AppSpider uses various algorithms to detect whether the page exists on the server, or it is a 'page not found' response.

Parameters:

- pbStatus [out, retval] - returns TRUE if the page is a 'page not found' page

  |

| Duration | 
 

This read-only property returns duration of the response in milliseconds.

Type: unsigned long

  |

## interface IRequest

Interface IRequest provides read-write access to the HTTP request data.

| Method/Property | Description |

| --- | --- |

| ProtocolHostAndPort | 
 

This read-write property provides access to a string that represents the protocol, host, and port of the request, e.g. http://www.webscantest.com:80.

Type: string

  |

| Method | 
 

This read-write property provides access the method of the request: GET, POST, etc.

Type: string

  |

| RequestURI | 
 

This read-write property provides access to the URI portion of the request string. Normally it will be relative URI to host (e.g. '/' or '/dir/file.html'), but it can include the host if desired (as with proxy).

Type: string

  |

| Headers | 
 

This read-write property provides access the HTTP headers of the request.

Type: string

  |

| GetHeaderValue | 
 

This method returns the value of an individual HTTP header.

Parameters:

- headerName - the name of the header which value should be returned pVal [out, retval] - the value of the HTTP header.

  |

| SetHeader | 
 

This method sets the value of an individual HTTP header.

Parameters:

- headerName - the name of the header which value should be set newVal - the value of the header that should be set.

  |

| SetBody | 
 

This method sets the body of the request.

Parameters:

- ar - the new body of the request pbStatus [out, retval] - boolean indicating success/failure.

  |

| GetBody | 
 

This method returns the body of the request.

Parameters:

- ar [out] - the body of the request pbStatus [out, retval] - boolean indicating success/failure. 
 
  |

## interface IResult

Interface IResult represents a vulnerability found by the attack module. Note that some of the properties of the result object will be set by the framework using the Attack Point object, as noted below. Interface IResult has the following members:

| Method/Property | Description |

| --- | --- |

| URL | 
 

This write-only property sets the URL of the vulnerability. It only needs to be set by the attack module if it is different than URL of attack point, as the framework automatically pre-fills the value using the attack point.

Type: string

  |

| AttackValue | 
 

This write-only property sets attack value of the attack. For parameter attacks, the framework automatically pre-fills this value, but for all other attacks it must be set by the attack module (as appropriate).

Type: string

  |

| OriginalValue | 
 

This write-only property sets the original value being replaced by the attack value. For parameter attacks, the framework automatically pre-fills this value, but for all other attacks it must be set by the attack module (as appropriate).

Type: string

  |

| ErrorString | 
 

This write-only property sets the error string, the string that made the module believe that this is a vulnerability. In the \<scanname\>.xml file, this is the VulnString field. In VulnerabilitiesSummary.xml this is the AttackMatchedString field.

Type: string

  |

| Description | 
 

This write-only property allows the module to specify a description of the vulnerability. N.B. This description does not appear in HTML reports. It is a field in the AttackVariance structure in the \<scanname\>.xml file. In VulnerabilitiesSummary.xml this is the AttackDescription field.

Type: string

  |

| PlaybackData | 
 

This method is reserved for future revisions and is not currently used.

  |

## interface IBaseAttack

Interface IBaseAttack is the base interface for several attack interfaces. Its methods allow construction of a simple attack that can send requests to the server. It has the following members:

| Method/Property | Description |

| --- | --- |

| CreateRequest | 
 

Creates a new request for the attack.

Parameters:

- pVal [out, retval] - a reference to a new request object

  |

| SendRequest | 
 

Sends the attack request returned by the method CreateRequest.

Parameters:

- vbAllowOutOfScope [in, defaultvalue(FALSE)] - set to true if the scope restrictions in the scan config file are to be ignored for this request.

- pVal [out, retval] - the response received from the server.

  |

| CreateResult | 
 

Creates a new result object for a vulnerability.

Parameters:

- pVal [out, retval] - a reference to a new result object.

  |

| PreProcessResponse | 
 

Returns whether or not the response passes framework checks. Several entries in the AttackConfig are verified: Discard404, ResponseCode, ForbiddenResponseCode, ResponseContentCharset, and ResponseContentType. Also, in a sequence context (see below), the response for a given step is checked against various attacking criteria to determine if the step should be eligible for a finding.

Parameters:

- pbPasses [out, retval] - returns TRUE if the checks are all passed.

  |

| FollowRedirect | 
 

If the response to the last sent attack request indicates a redirect that can be followed, this function will return a request representing the redirect. If a request is returned, the next send function invocation will use this request. Normally, this function would not be used in sequence capable attacks (see below) because the sequence will include the redirect request.

Parameters:

- pVal [out, retval] - a reference to a IRequest object, or NULL if there is no redirect that can be followed.

  |

## interface ISequenceCapableAttack : IBaseAttack

Interface ISequenceCapableAttack contains methods that are required to implement an attack on either a Parameter Attack Point or a CrawlResult Attack Point. It has the following members:

| Method/Property | Description |

| --- | --- |

| SendNextRequest | 
 

This method sends next request in the sequence, or the single request if there is no sequence. Normally, this method, and not SendRequest, should be used with Parameter Attack Points and CrawlResult Attack Points.

Parameters:

- pVal [out, retval] - response object that contains response received from the server.

  |

| OriginalResponse | 
 

This read-only property provides access to the response that the crawler received during crawling the site.

Type: string

  |

## interface IParameterAttack : ISequenceCapableAttack

Interface IParameterAttack contains methods that are required to implement an attack on a Parameter Attack Point. It has the following members:

| Method/Property | Description |

| --- | --- |

| ParameterValue | 
 

This read-write property provides access to the value of the attacked parameter that will be used during attack. Note this value could be different than the original value.

Type: string

  |

## interface ICrawlResultAttack : ISequenceCapableAttack

Interface ICrawlResultAttack allows performing attacks on a CrawlResult Attack Point. It has the following members:

| Method/Property | Description |

| --- | --- |

| AttackedRequest | 
 

This read-only property provides access to the request that the crawler made during crawling the site. While the property is read-only, the request retrieved can be modified to create the attack request.

Type: IRequest

  |

| CreateNewRequest | 
 

This is a synonym for IBaseAttack.CreateRequest, which is an artifact from older interface schema. This method is deprecated.

  |

| SetParameterValue | 
 

This method provides access to request parameters for attacking.

Parameters:

- pParam (IAttackerParameter) - the parameter to be set (can be obtained from interface ICrawlResultAttackPoint).

- pVal (string) - the value of the parameter being set.

  |

## interface IAttackPoint

Interface IAttackPoint is the base interface for the attack points. It has the following members:

| Method/Property | Description |

| --- | --- |

| Type | 
 

This read-only property returns type of the attack point.

Type: enum AttackPointType

  |

## interface IHostAttackPoint : IAttackPoint

| Method/Property | Description |

| --- | --- |

| Host | 
 

This read-property property contains the protocol, host and port of the site in the format protocol://host:port, e.g. http://www.webscantest.com:443.

Type: string

  |

| GetAttack | 
 

This method returns an attack object that can be used to perform an attack against a Host Attack Point.

Parameters:

- ppAttack[out, retval] - a reference to the attack object

  |

## interface IDirectoryAttackPoint : IAttackPoint

| Method/Property | Description |

| --- | --- |

| Directory | 
 

This read-property property contains the path to the directory.

Type: string

  |

| GetAttack | 
 

This method returns an attack object that can be used to perform an attack against a Directory Attack Point.

Parameters:

- ppAttack[out, retval] - a reference to the attack object

  |

## interface IFileAttackPoint : IAttackPoint

| Method/Property | Description |

| --- | --- |

| File | 
 

This read-property property contains the path to the file.

Type: string

  |

| GetAttack | 
 

This method returns an attack object that can be used to perform an attack against a File Attack Point.

Parameters:

- ppAttack[out, retval] - a reference to the attack object.

  |

## interface IAttackerParameter

| Method/Property | Description |

| --- | --- |

| Name | 
 

This read-only property provides access the name of the parameter.

Type: string

  |

| Type | 
 

This read-only property provides access the type of the parameter.

Type: ParameterType

  |

| Location | 
 

This read-only property provides access the location of the parameter within the request.

Type: ParameterLocation

  |

| OriginalValue | 
 

This read-only property provides access the original value of the parameter, the value that was discovered by the Crawler.

Type: string

  |

| OriginalValues | 
 

All of the original values seen for the parameter.

Type: array of strings

  |

| IsInjectedParameter | 
 

Returns whether or not the parameter is an injected parameter. The framework adds an additional GET parameter with an empty name to all requests. It only appears during the attacking phase, and only when it has a value set by the attack module.

Type: boolean

  |

## interface ICrawlResultAttackPoint : IAttackPoint

| Method/Property | Description |

| --- | --- |

| GetCrawlResultAttack | 
 

Returns a CrawlResultAttack object.

Parameters:

- ppSequenceAttack [out, retval] - a reference to the sequence attack object.

  |

| GetAttack | 
 

Returns a base attack object. The returned attack object can be used to perfom attacks in a non-sequence context.

Parameters:

- ppAttack[out, retval] - a reference to the attack object.

  |

| OriginalRequest | 
 

This read-only property returns the original request for this attack point.

Type: IRequest

  |

| OriginalResponse | 
 

This read-only property returns the original response for this attack point.

Type: IResponse

  |

| ParameterCount | 
 

This read-only property returns the number of parameters of this request.

Type: unsigned long

  |

| GetParameter | 
 

This method returns a parameter by its index.

Parameters:

- index - index of the parameter.

- pVal [out, retval] - the reference to the requested parameter (IAttackerParameter)

  |

## interface IParameterAttackPoint : IAttackPoint

| Method/Property | Description |

| --- | --- |

| GetParameterAttack | 
 

Returns a parameter attack object.

Parameters:

- ppParameterAttack[out, retval] - a reference to the parameter attack object.

  |

| OriginalRequest | 
 

This read-only property provides access to the original request for this attack point.

Type: IRequest

  |

| OriginalResponse | 
 

This read-only property returns the original response for this attack point.

Type: IResponse

  |

| AttackParameter | 
 

This read-only property provides access to the attack parameter.

Type: IAttackerParameter

  |

| ParameterCount | 
 

This read-only property returns number of parameters of this request.

Type: unsigned long

  |

| GetParameter | 
 

This method returns a parameter by its index.

Parameters:

- index - index of the parameter.

- pVal [out, retval] - the reference to the requested parameter.

  |

## interface IResponseAttackPoint : IAttackPoint

| Method/Property | Description |

| --- | --- |

| Request | 
 

This read-only property provides access to the request for this attack point.

Type: IRequest

  |

| Response | 
 

This read-only property provides access to the response for this attack point.

Type: IResponse

  |

| CreateResult | 
 

This method creates a result object for this attack point.

Parameters:

- pVal [out, retval] - a reference to the Result object created by this function.

  |

| ParameterCount | 
 

This read-only property returns number of parameters of this request.

Type: unsigned long

  |

| GetParameter | 
 

This method returned a parameter by its index.

Parameters:

- index - index of the parameter.

- pVal [out, retval] - the reference to the requested parameter.

  |

| PreProcessResponse | 
 

Returns whether or not the response passes framework checks. Several entries in the AttackConfig are verified: Discard404, ResponseCode, ForbiddenResponseCode, ResponseContentCharset, and ResponseContentType.

Parameters:

- pbPasses [out, retval] - returns TRUE if the checks are all passed.

  |

## interface ICustomParameters

| Method/Property | Description |

| --- | --- |

| GetParameter | 
 

This method returns the name of the custom parameter, defined in either the attack config or module config (see use below). If the parameter is not defined, an empty string is returned.

Parameters:

- bstrName - the name of the custom parameter.

- pVal [out, retval] - the value of the custom parameter.

  |

## interface IAttackConfiguration

| Method/Property | Description |

| --- | --- |

| Id | 
 

This read-only property contains an attack id string.

Type: string

  |

| CustomParameters | 
 

This read-only property returns a reference to the custom parameters for the attack config.

Parameters:

- pVal[out, retval] - reference to an ICustomParameters object.

  |

## interface IDataStorage

Interface IDataStorage allows retaining data between function calls to ICSModule functions. Each attack module has its own data storage; modules cannot access the data storage of another module.

| Method/Property | Description |

| --- | --- |

| DataExists | 
 

This method allows testing whether or not data with the given name & scope exists.

Parameters:

- bstrName - the name associated with the data.

- pVal - the DataStorageScope for the data.

- pbStatus [out, retval] - boolean indicating whether or not data with name and scope exists.

  |

| AddData | 
 

This method allows adding data if the name within the specified scope is not already taken. If the name/scope key already exists, the operation fails.

Parameters:

- bstrName - the name associated with the data.

- pVal - the DataStorageScope for the data.

- ar - the data as a SAFEARRAY(BYTE).

- pbStatus [out, retval] - bool for success of the operation.

  |

| ReadData | 
 

This method provides access to the data with the specified name/scope key.

Parameters:

- bstrName - the name associated with the data.

- pVal - the DataStorageScope for the data ar [out] - the data as a SAFEARRAY(BYTE).

- pbStatus [out, retval] - bool for success of the operation.

  |

| DeleteData | 
 

This method deletes data for the specified name/scope key.

Parameters:

- bstrName - the name associated with the data.

- pVal - the DataStorageScope for the data.

- pbStatus [out, retval] - bool for success of the operation.

  |

## interface IModuleRunner

| Method/Property | Description |

| --- | --- |

| SetModuleInstanceID | 
 

Binds this object to the data associated with this instance of attack module.

Parameters:

- moduleInstanceID - module runner instance passed into ICSModule::Load function.

  |

| GetAttackPoint | 
 

Returns current attack point. Note that the returned pointer should be cast by the client to the appropriate attack point interface.

Parameters:

- ppAttackPoint [out, retval] - reference to the attack point object.

  |

| GetAttackConfig | 
 

Returns current attack config object.

Parameters:

- ppAttackConfig [out, retval] - reference to the attack configuration object.

  |

| GetParameters | 
 

Returns custom confuguration parameters from the Module Configuration structure.

Parameters:

- ppCustomParameter[out, retval] - reference to the collection of module parameters.

  |

| GetDataStorage | 
 

Returns object for storing persistent data across several module invokations.

Parameters:

- ppDataStorage [out, retval] - a reference to the datastorage object.

  |

| GetAttackSignatureCollection | 
 

Returns the attack signature collection.

  |

| SaveResult | 
 

Saves the fully initialized result object, created by IResponseAttackPoint::CreateResult or IBaseAttack::CreateResult.

Parameters:

- pVal - a reference to IResult object.

  |

## interface IAttackSignature

Interface IAttackSignature configures a new signature for the module’s Attack Signature Collection. Each signature can have a URL, a parameter (name/value pair), and/or an arbitrary string. A signature can have one or none of each.

| Method/Property | Description |

| --- | --- |

| AddUrl | 
 

This method adds a URL to the signature.

Parameters:

- bstrUrl - the URL to add.

  |

| AddParameter | 
 

This method adds a parameter (name/value pair) to the signature.

Parameters:

- bstrName - the name of the parameter bstrValue - the value of the parameter.

  |

| AddString | 
 

This method adds a string to the signature.

Parameters:

- bstrString - the string to add.

  |

## interface IAttackSignatureCollection

Interface IAttackSignatureCollection provides access to a per-module set of attack signatures. The values are retained between function calls to ICSModule functions. The primary use of these signatures is to limit repetitive attacks and/or findings.

| Method/Property | Description |

| --- | --- |

| CreateSignature | 
 

This method creates a blank IAttackSignature object. It can then be configured, and added using the Add method or checked using the Exists method.

Parameters:

- pVal - [out, retval] the newly created signature. 
 
  |

| Add | 
 

This method adds a signature to the collection.

Parameters:

- pVal - the signature to add.

- pbStatus - [out, retval] true if the signature was added, false if the signature already existed in the collection.

  |

| Exists | 
 

This method tests if a given signature exists in the collection.

Parameters:

- pVal - the signature to check pbStatus - [out, retval] boolean indicating whether or not the signature was found. 
 
  |

| ClearModuleSignatures | 
 

This method clears the signature collection for the module.

  |

## What's Next?

<menuproxy data-mc-skin="/Project/Skins/SideMenu.flskn" mc-linked-toc="/Project/TOCs/as-custom-attack-module-api.fltoc" style="mc-toc-depth: 1;mc-context-sensitive: True;mc-include-parent: True;mc-include-siblings: True;mc-include-children: True;" madcap:conditions="General.Online_Only"></menuproxy>