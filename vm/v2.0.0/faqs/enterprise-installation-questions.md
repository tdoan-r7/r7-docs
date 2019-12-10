---
title: "enterprise-installation-questions"
excerpt: ""
---
# Common Installation Questions for AppSpider Enterprise

## Should I install my AppSpider Engine with AppSpider Enterprise?

Technically, you can install an engine on the same machine as AppSpider Enterprise as long as you have enough system resources. However, it's not recommended. You should install your AppSpider engines on separate machines.

There is no benefit to run AppSpider Enterprise and AppSpider Pro on the same machine because you'll still only be able to run one scan per machine.

It is recommended that you have a separate, dedicated machine to run AppSpider Enterprise.

## What does IIS need to be installed with?

- .NET 3.5

    - Framework

    - HTTP Activation 
 
- .NET 4.5

    - Framework

    - HTTP Activation

- .NET Extensibility 4.5

- .NET Extensibility 3.5

- ASP.NET 3.5

- ASP.NET 4.5

- ISAPI Extensions

- ISAPI Filters

- IIS 6 Management Compatibility 
 

## How do I set up my database?

How to install SQL express on the box or use an existing database (provide creds)