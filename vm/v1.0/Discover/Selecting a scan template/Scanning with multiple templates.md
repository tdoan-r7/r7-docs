---
title: "Scanning with multiple templates"
excerpt: ""
---
InsightVM retains all vulnerability results based on different scan templates within a site. This allows you to run targeted scans of your assets with different templates without affecting results that are not part of current scan configuration.

## The benefits

When scheduling scans for your site, you can apply different templates to specific scan windows. For example, schedule a recurring scan to run on the day after Patch Tuesday each month with a template configured to verify the latest Microsoft patches. Then schedule scans with a different template to run on other days.

You will can check the same set of assets for different, specific vulnerabilities. If a zero-day threat is reported, customize a template that only includes checks for that vulnerability. After remediating the zero-day, resume scanning with a template that you routinely use for your site.

## How targeted scanning works

####At the vulnerability level

When you run successive scans for the same vulnerability, even if it was previously scanned with a different template, the most current result replaces previous results in the scan history for the affected site. Take the following example:

1. You run one scan to check for a zero-day vulnerability.
2. Results show that it exists in your environment.
3. You remediate the issue and run the scan again, this time with negative results.
4. After the second scan, your results will no longer show the zero-day vulnerability in your scan history.

#### At the port level

If your alternating scan templates include different target ports, your results depend on which ports you are scanning for a specific vulnerability, as in the following example:

You run one scan to check for a self-signed certificate, using a template that includes port 80. The results are positive. You run another scan for the same vulnerability, but this time you use a template that does not include port 80. Regardless of the results of the second scan, your site's scan data will include a positive result for self-signed certificate on port 80.