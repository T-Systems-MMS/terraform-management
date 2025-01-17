<!-- BEGIN_TF_DOCS -->
# management

This module manages the hashicorp/azurerm management resources.
For more information see https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs > management

_<-- This file is autogenerated, please do not change. -->_

## Requirements

| Name | Version |
|------|---------|
| terraform | >=1.5 |
| azurerm | >=2.19.0, <4.0 |

## Providers

| Name | Version |
|------|---------|
| azurerm | >=2.19.0, <4.0 |

## Resources

| Name | Type |
|------|------|
| azurerm_management_lock.management_lock | resource |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| management_lock | resource definition, default settings are defined within locals and merged with var settings | `any` | `{}` | no |

## Outputs

| Name | Description |
|------|-------------|
| management_lock | Outputs all attributes of resource_type. |
| variables | Displays all configurable variables passed by the module. __default__ = predefined values per module. __merged__ = result of merging the default values and custom values passed to the module |

## Examples

Minimal configuration to install the desired resources with the module

```hcl
module "container" {
  source = "registry.terraform.io/telekom-mms/container/azurerm"
  container_registry = {
    crmms = {
      location            = "westeurope"
      resource_group_name = "rg-mms-github"
    }
  }
}

module "management" {
  source = "registry.terraform.io/telekom-mms/management/azurerm"
  management_lock = {
    container_registry = {
      location = "westeurope"
      scope    = module.container.container_registry["crmms"].id
    }
  }
}
```

Advanced configuration to install the desired resources with the module

```hcl
module "container" {
  source = "registry.terraform.io/telekom-mms/container/azurerm"
  container_registry = {
    crmms = {
      location            = "westeurope"
      resource_group_name = "rg-mms-github"
    }
  }
}

module "management" {
  source = "registry.terraform.io/telekom-mms/management/azurerm"
  management_lock = {
    container_registry = {
      name  = "restrict_delete"
      scope = module.container.container_registry["crmms"].id
      notes = "protect resource"
    }
  }
}
```
<!-- END_TF_DOCS -->
