---
type: "page"
creatordisplayname: "Rob Barnes"
creatoremail: ""
lastmodifierdisplayname: "Rob Barnes"
lastmodifieremail: ""
title: "Rift Configuration"
weight: 13
---

Example config file"

```json
{
  "log": {
    "level": "debug"
  },
  "pagerduty": {
    "enabled": true,
    "token": "..."
  },
  "alertmanager": {
    "enabled": false
  },
  "boundary": {
    "organization": "o_1234567890",
    "addr": "http://localhost:9200",
    "scope": "o_1234567890",
    "auth": {
      "method": "ampw_1234567890",
      "username": "admin",
      "password": "password"
    }
  }
}
```
