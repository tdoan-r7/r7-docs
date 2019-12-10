---
title: "List Apps (custom)"
excerpt: "List the apps your user has access to"
---
```
GET https://api.insight.rapid7.com/ias/v1/apps
```

## Response
```json
 {
      "id": "string",
      "name": "string",
      "description": "string",
      "default_scan_config": {
        "id": "string"
      }
}
```

## Permissions
- Read Apps
[block:callout]
{
  "type": "info",
  "title": "Note",
  "body": "Your user will gain access to this app by default"
}
[/block]