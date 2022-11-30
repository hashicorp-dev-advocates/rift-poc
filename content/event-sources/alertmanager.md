---
type: "page"
creatordisplayname: "Rob Barnes"
creatoremail: ""
lastmodifierdisplayname: "Rob Barnes"
lastmodifieremail: ""
title: "Alert Manager"
weight: 10
---
Grafana alertmanager will need to have a webhook contact point created which will send notifications to Rift when an alert is triggered. All alerts should have the following labels attached to them:

- `project` - Boundary Project Name Containing Affected Infrastructure
- `alertname` - The Name Of The Alert Being Sent To Rift.
- `teams` - A Comma Separated List of Bounday Group IDs That Should Be Granted Access To The Affected Infrastructure
