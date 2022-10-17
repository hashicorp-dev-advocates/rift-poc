---
creatordisplayname: "Rob Barnes"
lastmodifierdisplayname: "Rob Barnes"
# title: Rift
---
# Rift Documentation

## Rift is an event-driven access control orchestrator proof of concept for incident management.

![workflow](rift-workflow.png?height=300px&classes=shadow "")

It is designed to work with event sources like PagerDuty and Alert Manager to orchestrate access controls in HashiCorp Boundary.

### Least Priviledged Access

The principle of least privileged access means engineers should not have access to production systems to perform their role. When an incident occurs, this may change as they may need access to troubleshoot and resolve incident. Once the incident is resolved, their access to the systems should be revoked to keep in line with the principle of least privilege.

Rift is a tool that is designed to automate that workflow based on events from your chosen alerting platform.

## How It Works

![diagram](Rift-under-the-hood.gif "")

## Getting started

1. [Install Rift](/installation)
2. [Configure Boundary prerequisites](/boundary)
3. [Configure event source prerequisites](/event-sources)
4. [Create a Rift configuration file](/rift-configuration)
