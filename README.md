## Overview

- This repository contains Terraform configurations to provision and manage Azure infrastructure for Dev, Test, and Prod environments.


## Terraform State Storage

- The Terraform state files for Dev, Test, and Prod environments are stored in the Production storage account:

## Requirements

| Name | Version |
|------|---------|
| terraform | >= 1.2 |
| azurerm | ~>3.0 |

## Providers

| Name | Version |
|------|---------|
| azurerm | 3.114.0 |

## Modules

| modules|
|--------|
| acr |
| alerts |
| automation_account |
| backup_storage_account |
| cognitive_account_OpenAI |
| cosmosdb |
| key_vault |
| log_analystics_workspace |
| private_dns |
| resource_group |
| search_service |
| storage_account |
| subnets |
| vnet |
| weba_app|

## Resources

| Name | Type |
|------|------|
| [azurerm_resource_group.rg](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/resource_group) | resource |
| [azurerm_container_registry](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/container_registry) | resource |
| [azurerm_monitor_autoscale_setting](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/azurerm_monitor_autoscale_setting) | resource |
| [azurerm_monitor_action_group](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/azurerm_monitor_action_group) | resource |
| [azurerm_monitor_metric_alert](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/azurerm_monitor_metric_alert) | resource |
| [azurerm_automation_account](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/azurerm_automation_account) | resource |
| [azurerm_automation_runbook](https://registry.terraform.io/providers/hashicorp/azurerm/4.24.0/docs/resources/automation_runbook.html) | resource |
| [azurerm_automation_schedule](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/) | resource |
| [azurerm_automation_variable_string](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/) | resource |
| [azurerm_storage_account](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/) | resource |
| [](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/) | resource |


## Inputs

| Name | Type |
|------|------|
| env | string |
| location | string |
| service_endpoints | list(string) |
| whitelisting-ip | set(string) |
| version_upgrade_option | string |
| rai_policy_name | string |
| vnet-ip | list(string) |
| sub-pub-ip | string |
| sub-pvt-ip | string |
| searchsub-pvt-ip | string |
| tf_state_storageacc_name | string |
| storageacc_name | string |
| container_list | list(string)
| backup_storageacc_name | string | 
| backupstorage_location | string | 
| custom_subdomain_name | string | 
| os_type | string |
| app-plan-sku | string |
| offer_type | string |
| db_kind | string |
| mongo_server_version | string |
| system_prompt_chat_response | string |
| system_prompt_search_query | string |
| hostname | string |
| redirect_uris_spa | string |
| redirect_uris_web | string |
| cors_origin | string |
| ip_address | list(string) |
| ip_address_cosmos | string |
| storage_allowed_origins | string |
| homepage_url | string |
| user_firstName | string (sensitive) |
| user_lastName | string (sensitive) |
| emailid | string (sensitive) |
| phone_number | string (sensitive) |
| retention_in_days | string |
| local_authentication_disabled | string |
| newrelic_account_id | string |
| newrelic_integration_name | string |
| search_backup_runbook | string |
| storage_backup_runbook | string |
| schedule_name | string |
| API_VERSION | string |
| CONTAINER_NAME | string |
| cosmosdb_connection_secret_name | string |
| dest_account_url | string |
| openai_key_secret_name | string |
| search_key_secret_name | string |
| source_account_url | string |
| storage_connection_secret_name | string |
| connection_string_secret_name | string |
| storage_key_secret_name | string |
| TARGET_CONTAINERS | string |
| container1 | string |
| container2 | string |
| container3 | string |
| search_service_key | string |
| automation_search_secret_name | string
| backup_storage_conncc_string | string |

- The following input variables must be defined in a .tfvars file with values before running Terraform.


## Output

| Name | Description |
|----- |-------------|
| docker_registry_password | Password for Azure Container Registry (ACR) |
| docker_registry_username | Username for Azure Container Registry (ACR) |
| login_server | Login server URL for Azure Container Registry (ACR) |
| backup_storage_account_id | ID of the backup storage account |
| backup_storage_account_name | Name of the backup storage account |
| openai_service_name | Name of the Azure OpenAI service |
| openai_service_id | ID of the Azure OpenAI service |
| cosmos_account_name | Name of the Azure Cosmos DB account |
| cosmos_account_id | ID of the Azure Cosmos DB account |
| key_vault_uri | URI of the Azure Key Vault |
| key_vault_tenant_id | Tenant ID associated with Azure Key Vault |
| key_vault_id | ID of the Azure Key Vault |
| keyvault_name | Name of the Azure Key Vault |
| log_analytics_workspace_id | ID of the Azure Log Analytics Workspace |
| resource_group_name | Name of the resource group |
| id | ID of the resource group |
| search_service_id | ID of the Azure Cognitive Search service |
| search_service_name | Name of the Azure Cognitive Search service |
| storage_account_id | ID of the primary storage account |
| storage_account_name | Name of the primary storage account |
| public_subnet_name | Name of the public subnet |
| private_subnet_name | Name of the private subnet |
| search_subnet_name | Name of the search service subnet |
| private_subnet_id | ID of the private subnet |
| public_subnet_id | ID of the public subnet |
| search_subnet_id | ID of the search service subnet |
| virtual_network_name | Name of the virtual network |
| virtual_network_id | ID of the virtual network |
| default_hostname | Default hostname of the frontend web application |
| service_plan_id | ID of the Azure App Service Plan |
| backend_appname | Name of the backend web application |
| backend_app_id | ID of the backend web application |

## Manual Configurations Required (Not Included in Terraform)
Once the infrastructure is created using Terraform, the following configurations must be done manually:

# OpenSearch Indexes

- OpenSearch indexes are not provisioned through Terraform.

- You need to create necessary indexes manually using API requests or OpenSearch Dashboards.

- Define index mappings based on application requirements.

# Key Vault Values

- The Key Vault is created via Terraform, but secrets and keys must be added manually.

- Add necessary values such as database credentials, API keys, and connection strings.

- Use Managed Identity or an appropriate authentication method for secure access.

# Azure AD B2C Configuration

- Azure AD B2C tenant and identity configuration are not handled in Terraform.

- You need to manually set up an Azure AD B2C tenant.

- Register applications for authentication and configure user flows (sign-in, sign-up, and password reset).
