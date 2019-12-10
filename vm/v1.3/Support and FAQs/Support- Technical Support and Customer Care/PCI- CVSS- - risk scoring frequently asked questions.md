---
title: "PCI, CVSS, & risk scoring frequently asked questions"
excerpt: ""
---
This page concerns PCI compliance and scores related to vulnerabilties.

## What are the risk scoring models in InsightVM, and how are they different?

InsightVM calculates risk scores for every asset and vulnerability that it finds during a scan. The scores indicate the potential danger that the vulnerability poses to network and business security based on impact and likelihood of exploit.

Two risk scoring models are available in InsightVM:
* Temporal model
* Weighted model

_Temporal model_

This model emphasizes the length of time that the vulnerability has been known to exist, as well as the nature of the risk. Older vulnerabilities are easier to exploit because attackers have known about them for a longer period of time. The Temporal risk model is a mathematical calculation of the following factors:
* Time-based likelihood (t) is the number of days since vulnerability publicly disclosed. The overall score increases with the number of days.
* Proximity-based impact is the sum of four variables:
   1. access vector (AV) or the likelihood of exploit, based on whether the target is locally accessible, is accessible from within the network, or must be accessed from outside the network; local access results in a higher score
   2. confidentiality impact (C) or disclosure to unauthorized individuals or systems
   3. integrity impact (I) or unauthorized data modification
   4. availability impact (A) or loss of access to data
* exploit difficulty is the sum of two variables:
   1. access complexity (AC) or the likelihood of exploit based on how much skill is required to perform the exploit; an easier exploit results in a higher score
   2. authentication (Au) or the likelihood of exploit based on authentication requirements; no authentication results in a higher score

The score is expressed in high, whole numbers, ranging up to as many as six digits. There is no "highest" number. These numbers are relative to each other.

This scoring model is the most effective means to track the risk associated with vulnerabilities over time. Also, it is the ideal option for new deployments, since its emphasis on time and severity can help you to prioritize remediation projects better.

The following formula is used to calculate the Temporal scoring model:
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d28b56b-m_temp_risk_frmla_text.png",
        "m_temp_risk_frmla_text.png",
        503,
        113,
        "#149c9c"
      ]
    }
  ]
}
[/block]
This formula can be broken down into its components as follows:
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d3ba24a-m_temp_risk_frmla_val.png",
        "m_temp_risk_frmla_val.png",
        352,
        113,
        "#149c9c"
      ]
    }
  ]
}
[/block]
_Weighted model_

The Weighted risk model is based primarily on asset data and vulnerability types, and it emphasizes the following factors:
* vulnerability severity, which is the number—ranging from 1 to 10—that InsightVM calculates for each vulnerability
* number of vulnerability instances
* type of asset, such as a computer, router, or wireless access point (WAP)
* number and types of services on the asset; for example, a database has higher business value
* the level of importance, or weight, that you assign to a site when you configure it; see [Creating and editing sites](doc:creating-and-editing-sites).

Weighted risk scores scale with the number of vulnerabilities. A higher number of vulnerabilities on an asset means a higher risk score. The score is expressed in lower—usually single-digit—numbers with decimals.

See [Working with risk strategies to analyze threats](doc:working-with-risk-strategies-to-analyze-threats).

Risk scores are important tools for prioritizing your vulnerability remediation projects. Another important metric is the CVSS score. See FAQ titled What is a CVSS score?

## If I run a PCI scan and then generate a PCI report that indicates my environment is compliant, does that mean my environment is PCI-compliant?

If you are not an approved scan vendors (ASV), certified by the Payment Card Industry (PCI), then the answer is no. Only certified ASVs can perform PCI-sanctioned compliance audits. It is a good practice, though, to run PCI scans and reports in preparation for a compliance audit or as part of a security maintenance routine.

## What is a"pass" or "fail" PCI audit result based on?

An ASV bases the audit result on the Common Vulnerability Scoring System (CVSS), Version 2, score that is calculated for every vulnerability. Scores range from 0 to 10.0, with 4.0 or higher indicating failure to comply with PCI standards.

Any asset that contains at least one vulnerability with CVSS score of 4.0 or higher is considered non-compliant. And, if at least one asset is non-compliant, the entire organization is considered to be non-compliant.

Also, any vulnerability that exposes an asset to XSS or SQL injection indicates failure to comply with PCI standards, regardless of CVSS score.

## What is a CVSS score?

InsightVM ranks every discovered vulnerability according to various factors, including the Common Vulnerability Scoring System, Version 2 (CVSSv2) and substantial support for CVSSv3. The CVSS score is a computation of base metrics that reflect how much risk a vulnerability poses to network security. Version 2 base metrics include access (ranging from local to remote), access complexity, required authentication, impact on data confidentiality, impact on data integrity, and impact on data availability. Version 3 utilizes the additional **Scope** metric in an effort to measure how much a specific vulnerability could affect resources outside the reach of the asset’s privileges.

The CVSS system rates all vulnerabilities on a scale of 0.0 to 10.0 with 10.0 representing the greatest security risk. A ranking of 4.0 or higher indicates failure to comply with PCI standards.
[block:callout]
{
  "type": "info",
  "body": "InsightVM will prefer Version 3 scores if they are available."
}
[/block]
### CVSSv2 Severity Rating Scale

A moderate vulnerability, which ranges from 0.0 to 3.4 on the CVSS system can only be exploited locally and requires authentication. A successful attacker has little or no access to unrestricted information, cannot destroy or corrupt information, and cannot cause outages on any systems. Examples include default or guessable SNMP community names and the OpenSSL PRNG Internal State Discovery vulnerability.

A severe vulnerability, which ranges from 3.5 to 7.4 on the CVSS system, can be exploited with a moderate level of hacking experience and may or may not require authentication. A successful attacker has partial access to restricted information, can destroy some information, and can disable individual target systems on a network. Examples include Anonymous FTP Writeable and Weak LAN Manager hashing permitted.

A critical vulnerability, which ranges from 7.5 and 10.0 on the CVSS system, can be exploited with easy access and requires little or no authentication. A successful attacker has access to confidential information, can corrupt or delete data, and can cause a system outage. Examples include the ability of anonymous users can obtain a Windows password policy.

### CVSSv3 Severity Rating Scale

Version 3 scoring introduces a more refined scale of severity.  Vulnerabilities are categorized at the following levels:
[block:parameters]
{
  "data": {
    "h-0": "Rating",
    "h-1": "CVSS Score",
    "0-0": "None",
    "0-1": "0.0",
    "1-0": "Low",
    "1-1": "0.1 - 3.9",
    "2-0": "Medium",
    "2-1": "4.0 - 6.9",
    "3-0": "High",
    "3-1": "7.0 - 8.9",
    "4-0": "Critical",
    "4-1": "9.0 - 10.0"
  },
  "cols": 2,
  "rows": 5
}
[/block]
## If CVSS scoring is the framework for a PCI audit result, why do I see "PCI" scores in my report?

InsightVM includes the legacy PCI scoring system as an additional way to rate and prioritize vulnerabilities. This system ranks vulnerabilities on a severity scale from 1 to 5. Any vulnerability ranking above 2 indicates failure to comply with PCI standards.
* Level 5 vulnerabilities permit attacks with remote root or remote administrator capabilities that can compromise an entire host.
* Level 4 vulnerabilities permit attacks with remote user capabilities and partial file system access.
* Level 3 vulnerabilities permit access to specific stored information, such as security settings.
* Level 2 vulnerabilities expose some sensitive host information, such as precise versions of services.
* Level 1 vulnerabilities expose information such as open ports.