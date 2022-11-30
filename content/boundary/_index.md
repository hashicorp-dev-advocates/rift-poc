---
type: "page"
creatordisplayname: "Rob Barnes"
creatoremail: ""
lastmodifierdisplayname: "Rob Barnes"
lastmodifieremail: ""
title: "Boundary Configuration for Rift"
weight: 10
---

Rift supports self-hosted Boundary Clusters and managed Clusters on HashiCorp Cloud platform.  In order for Rift to orchestrate Access controls, The following things are needed:

For PagerDuty Event Source:

- A Rift user in Boundary with permissions to manage Identity and Access Management resources at all scopes that are subject to Rift orchestration.
- The org_id that will contain the projects and sub-resources that Rift will orchestrate access for. Note: The Rift user created in Boundary will need permissions at this scope.
- An OIDC auth method at the org scope in step 2. Note: This will need to be configured as the primary auth method for the scope.

_**NOTE: User will need to log in to Boundary via this OIDC auth method in order to have their accounts automatically created in Boundary. The Rift workflow for PagerDuty will not work unless this step has been completed by all on-call engineers**_

For Alertmanager Event Source:

- A Rift user in Boundary with permissions to manage Identity and Access Management resources at all scopes that are subject to Rift orchestration.
- The org_id that will contain the Boundary projects and sub-resources that Rift will orchestrate access for. Note: The Rift user created in Boundary will need permissions at this scope.
- The Boundary Project, Host Catalogs, Hosts, Host Sets and Targets for your infrastructure.
- An account,associated user and group containing the user for your engineers.
