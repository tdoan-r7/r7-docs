---
title: "Fingerprint certainty"
excerpt: ""
---
Fingerprint certainty is a measurement of the predicted accuracy of a scan’s attempt to identify the traits of an asset.  You can view the certainty scores of system fingerprints in the Security Console via asset detail and completed scan pages.   Fingerprint certainty is scored according to a scale of 0 to 1.0.

Fingerprint certainty scores determine which vulnerability checks are run against the asset.
[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "Many vulnerability checks will only run if the system fingerprint satisfies a required minimum score.  Fingerprint certainty scores of 1.0 are almost always produced by authenticated scans."
}
[/block]
# Inspect fingerprint certainty scores

You can view certainty scores in the following ways:

## Asset detail view

1. On the **Assets** tab of your Security Console, browse to the “Scanned” table.
2. Open the scanned asset you would like to inspect.
3. On the asset detail page, expand the **Items** dropdown in the upper right corner of your screen.  Select **Fingerprints**.
 * This will add the “Fingerprints” table to your asset detail page.
4. Scroll down to the “Fingerprints” table to examine fingerprint records and their corresponding certainty scores.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/7579ebf-fingerprint_certainty_scores.png",
        "fingerprint_certainty_scores.png",
        1706,
        218,
        "#f7f7f8"
      ]
    }
  ]
}
[/block]
## Completed scan view

1. On the **Home** tab of your Security Console, browse to the “Sites” table.
2. Open a completed scan by clicking a corresponding link under “Scan Status”.
3. In the “Completed Assets” table, open the scanned asset you would like to inspect.
4. Scroll down to the “Node Fingerprints” table to examine fingerprint records and their corresponding certainty scores.
[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "Although the navigation methods described previously are different, the certainty data for each asset will remain the same."
}
[/block]