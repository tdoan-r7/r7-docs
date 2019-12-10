---
title: "Scan templates appendix"
excerpt: ""
---
This appendix lists all built-in scan templates available in InsightVM. It provides a description for each template and suggestions for when to use it.

# Template Directory

* [CIS](doc:scan-templates#section-cis)
* [DISA](doc:scan-templates#section-disa)
* [Denial of service](doc:scan-templates#section-denial-of-service)
* [Discovery scan](doc:scan-templates#section-discovery-scan)
* [Discovery scan (aggressive)](doc:scan-templates#section-discovery-scan-aggressive-)
* [Exhaustive](doc:scan-templates#section-exhaustive)
* [FDCC](doc:scan-templates#section-fdcc)
* [Full audit](doc:scan-templates#section-full-audit)
* [Full audit without Web Spider](doc:scan-templates#section-full-audit-without-web-spider)
* [HIPAA compliance](doc:scan-templates#section-hipaa-compliance)
* [Internet DMZ audit](doc:scan-templates#section-internet-dmz-audit)
* [Linux RPMs](doc:scan-templates#section-linux-rpms)
* [Microsoft hotfix](doc:scan-templates#section-microsoft-hotfix)
* [PCI ASV external audit](doc:scan-templates#section-pci-asv-external-audit)
* [PCI internal audit](doc:scan-templates#section-pci-internal-audit)
* [Penetration test](doc:scan-templates#section-penetration-test)
* [Safe network audit](doc:scan-templates#section-safe-network-audit)
* [Sarbanes-Oxley (SOX) compliance](doc:scan-templates#section-sarbanes-oxley-sox-compliance)
* [SCADA audit](doc:scan-templates#section-scada-audit)
* [USGCB](doc:scan-templates#section-usgcb)
* [Web audit](doc:scan-templates#section-web-audit)

##CIS

This template incorporates the Policy Manager scanning feature for verifying compliance with Center for Internet Security (CIS) benchmarks. The scan runs application-layer audits. Policy checks require authentication with administrative credentials on targets. Vulnerability checks are not included.

##DISA

This scan template performs Defense Information Systems Agency (DISA) policy compliance tests with application-layer auditing on supported DISA-benchmarked systems. Policy checks require authentication with administrative credentials on targets. Vulnerability checks are not included. Only default ports are scanned.

##Denial of service

This basic audit of all network assets uses both safe and unsafe (denial-of-service) checks. This scan does not include in-depth patch/hotfix checking, policy compliance checking, or application-layer auditing. You can run a denial of service scan in a preproduction environment to test the resistance of assets to denial-of service conditions.

##Discovery scan

This scan locates live assets on the network and identifies their host names and operating systems. This template does not include enumeration, policy, or vulnerability scanning.

You can run a discovery scan to compile a complete list of all network assets. Afterward, you can target subsets of these assets for intensive vulnerability scans, such as with the Exhaustive scan template.

##Discovery scan (aggressive)

This fast, cursory scan locates live assets on high-speed networks and identifies their host names and operating systems. The system sends packets at a very high rate, which may trigger IPS/IDS sensors, SYN flood protection, and exhaust states on stateful firewalls. This template does not perform enumeration, policy, or vulnerability scanning.

This template is identical in scope to the discovery scan, except that it uses more threads and is, therefore, much faster. The trade-off is that scans run with this template may not be as thorough as with the Discovery scan template.

##Exhaustive

This thorough network scan of all systems and services uses only safe checks, including patch/hotfix inspections, policy compliance assessments, and application-layer auditing. This scan could take several hours, or even days, to complete, depending on the number of target assets.

Scans run with this template are thorough, but slow. Use this template to run intensive scans targeting a low number of assets.

##FDCC

This template incorporates the Policy Manager scanning feature for verifying compliance with all Federal Desktop Core Configuration (FDCC) policies. The scan runs application-layer audits on all Windows XP and Windows Vista systems. Policy checks require authentication with administrative credentials on targets. Vulnerability checks are not included. Only default ports are scanned.

If you work for a U.S. government organization or a vendor that serves the government, use this template to verify that your Windows Vista and XP systems comply with FDCC policies.

##Full audit

This full network audit of all systems uses only safe checks, including network-based vulnerabilities, patch/hotfix checking, and application-layer auditing. The system scans only default ports and disables policy checking, which makes scans faster than with the Exhaustive scan. Also, This template does not check for potential vulnerabilities.

Use this template to run a thorough vulnerability scan.

##Full audit without Web Spider

This full network audit uses only safe checks, including network-based vulnerabilities, patch/hotfix checking, and application-layer auditing. The system scans only default ports and disables policy checking, which makes scans faster than with the Exhaustive scan. It also does not include the Web spider, which makes it faster than the full audit that does include it. Also, This template does not check for potential vulnerabilities.

This is the default scan template. Use it to run a fast vulnerability scan right “out of the box.”

##HIPAA compliance

This template uses safe checks in this audit of compliance with HIPAA section 164.312 (“Technical Safeguards”). The scan will flag any conditions resulting in inadequate access control, inadequate auditing, loss of integrity, inadequate authentication, or inadequate transmission security (encryption).

Use this template to scan assets in a HIPAA-regulated environment, as part of a HIPAA compliance program.

##Internet DMZ audit

This penetration test covers all common Internet services, such as Web, FTP, mail (SMTP/POP/IMAP/Lotus Notes), DNS, database, Telnet, SSH, and VPN. This template does not include in-depth patch/hotfix checking and policy compliance audits.

Use this template to scan assets in your DMZ.

##Linux RPMs

This scan verifies proper installation of RPM patches on Linux systems. For best results, use administrative credentials.

Use this template to scan assets running the Linux operating system.

##Microsoft hotfix

This scan verifies proper installation of hotfixes and service packs on Microsoft Windows systems. For optimum success, use administrative credentials.

Use this template to verify that assets running Windows have hotfix patches installed on them.

##PCI ASV external audit
[block:callout]
{
  "type": "info",
  "body": "Previously called **Payment Card Industry (PCI) audit**."
}
[/block]
This audit of Payment Card Industry (PCI) compliance uses only safe checks, including network-based vulnerabilities, patch /hotfix verification, and application-layer testing. All TCP ports and well-known UDP ports are scanned. Policy checks are not included.

This template should be used by an Approved Scanning Vendor (ASV) to scan assets as part of a PCI compliance program. For your internal PCI discovery scans, use the PCI Internal audit template.

##PCI internal audit

This template is intended for discovering vulnerabilities in accordance with the Payment Card Industry (PCI) Data Security Standard (DSS) requirements. It includes all network-based vulnerabilities and web application scanning. It specifically excludes potential vulnerabilities as well as vulnerabilities specific to the external perimeter.

This template is intended for your organization's internal scans for PCI compliance purposes.

##Penetration test

This in-depth scan of all systems uses only safe checks. Host-discovery and network penetration features allow the system to dynamically detect assets that might not otherwise be detected. This template does not include in-depth patch/hotfix checking, policy compliance checking, or application-layer auditing.

With this template, you may discover assets that are out of your initial scan scope. Also, running a scan with this template is helpful as a precursor to conducting formal penetration test procedures.

##Safe network audit

This non-intrusive scan of all network assets uses only safe checks. This template does not include in-depth patch/hotfix checking, policy compliance checking, or application-layer auditing.

This template is useful for a quick, general scan of your network.

##Sarbanes-Oxley (SOX) compliance

This is a safe-check Sarbanes-Oxley (SOX) audit of all systems. It detects threats to digital data integrity, data access auditing, accountability, and availability, as mandated in Section 302 (“Corporate Responsibility for Fiscal Reports”), Section 404 (“Management Assessment of Internal Controls”), and Section 409 (“Real Time Issuer Disclosures”) respectively.

Use this template to scan assets as part of a SOX compliance program.

##SCADA audit

This is a “polite,” or less aggressive, network audit of sensitive Supervisory Control And Data Acquisition (SCADA) systems, using only safe checks. Packet block delays have been increased; time between sent packets has been increased; protocol handshaking has been disabled; and simultaneous network access to assets has been restricted.

Use this template to scan SCADA systems.

##USGCB

This template incorporates the Policy Manager scanning feature for verifying compliance with all United States Government Configuration Baseline (USGCB) policies. The scan runs application-layer audits on all Windows 7 systems. Policy checks require authentication with administrative credentials on targets. Vulnerability checks are not included. Only default ports are scanned.

If you work for a U.S. government organization or a vendor that serves the government, use this template to verify that your Windows 7 systems comply with USGCB policies.

##Web audit

This audit of all Web servers and Web applications is suitable public-facing and internal assets, including application servers, ASPs, and CGI scripts. The template does not include patch checking or policy compliance audits. Nor does it scan FTP servers, mail servers, or database servers, as is the case with the DMZ Audit scan template.

Use this template to scan public-facing Web assets.