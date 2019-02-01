# Common resources

Before installation of any blueprint, suitable resource group, networks and security group have to be created.

## Prerequesites:

Prior to installation You have to upload plugins and create secrets.

### Plugins 

Upload:
* **cloudify-azure-plugin** - Tested for version 2.1.1
* **cloudify-utilities-plugin** - Tested for version 1.12.0

### Secrets

Create below secrets on secrets store management:
* **Azure secrets:**
    * *azure_client_id* - Service Principal appId
    * *azure_client_secret* - Service Principal password
    * *azure_subscription_id* - Service Principal ID
    * *azure_tenant_id* - Service Principal tenant
    * *azure_location* - Specifies the supported Azure location for the resource

## Environment creation

### Inputs
* *retry_after* - The number of seconds for each task retry interval (in the
          case of iteratively checking the status of an asynchronous operation) - default: 5
* *resource_prefix* - Prefix of every resource created at this deployment on Azure - default: cfy
* *resource_suffix* - Suffix of every resource created at this deployment on Azure - default: 0
* *mgmt_subnet_cidr* - Management subnet CIDR - default: 10.10.1.0/24
* *public_subnet_cidr* -Public subnet CIDR - default: 10.10.2.0/24
* *wan_subnet_cidr* - WAN subnet CIDR - default: 10.10.3.0/24
* *lan_subnet_cidr* - LAN subnet CIDR - default: 10.10.4.0/24
* *network_api_version* - API Version for Network - default: "2015-06-15"

### Installation

Install using VNFM-Networking-Prov-Azure-networks.yaml blueprint:

``cfy install  VNFM-Networking-Prov-Azure-networks.yaml -b  VNFM-Networking-Prov-Azure-networks``

**It should be installed only one time before start of provisioning services.**
It will be reused automatically by blueprints using capabilities mechanism.
