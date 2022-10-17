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

- A Rift user in Boundary with permissions to manage Identity and Access Management resources at all scopes that are subject to Rift orchestration.
- The org_id that will contain the projects and sub-resources that Rift will orchestrate access for. Note: The Rift user created in Boundary will need permissions at this scope.
- An OIDC auth method at the org scope in step 2. Note: This will need to be configured as the primary auth method for the scope.

_**NOTE: User will need to log in to Boundary via this OIDC auth method in order to have their accounts automatically created in Boundary. The Rift workflow for PagerDuty will not work unless this step has been completed by all on-call engineers**_

## Configuring Boundary with Terraform

The required Boundary resources can also be created and managed using Terraform. To help you get started, we have created a Terraform module which you can consume in your demo environment. The below Terraform code will provision all of the above resources in Boundary. You will need to pass in variable values for the following configuration parameters:

- `boundary_redirect_address` - This is the address of your Boundary controller
- `org_name` - This is the name of a Boundary org that will be created for you
- `project_name` - This is the name of a project scope that will be created under the org scope

```hcl
module "rift-boundary-setup" {
  source                    = "devops-rob/app-boundary/azuread" # TODO - Update this
  version                   = "0.1.1" # TODO - Update this
  boundary_redirect_address = var.boundary_redirect_address
  org_name                  = var.org_name
  project_name              = var.boundary_project_name
}
```
