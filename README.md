# **Table of Contents**

- [**Table of Contents**](#table-of-contents)
- [Introduction](#introduction)
- [Automation Host Prerequisites](#automation-host-prerequisites)
    - [Terraform Providers](#terraform-providers)
- [PowerVS Prerequisites](#powervs-prerequisites)
- [OCP Install](#ocp-install)
- [Contributing](#contributing)


# Introduction

This repo contains Terraform templates to help deployment of OpenShift Container Platform (OCP) 4.x on [IBM® Power Systems™ Virtual Server on IBM Cloud](https://www.ibm.com/cloud/power-virtual-server).

This project leverages the helpernode [ansible playbook](https://github.com/RedHatOfficial/ocp4-helpernode) internally for OCP deployment on IBM Power Systems Virtual Servers (PowerVS).

:heavy_exclamation_mark: *For bugs/enhancement requests etc. please open a GitHub issue*

For general PowerVS usage instructions please refer to the following links:
- https://cloud.ibm.com/docs/power-iaas?topic=power-iaas-getting-started
- https://www.youtube.com/watch?v=RywSfXT_LLs
- https://www.youtube.com/playlist?list=PLVrJaTKVPbKM_9HU8fm4QsklgzLGUwFpv


# Automation Host Prerequisites

The automation needs to run from a system with internet access. This could be your laptop or a VM with public internet connectivity. This automation code have been tested on the following Operating Systems:
- Mac OSX (Darwin)
- Linux (x86_64)
- Windows 10


Install the following packages on the automation host.

- **Terraform >= 0.13.0**: Please refer to the [link](https://learn.hashicorp.com/terraform/getting-started/install.html) for instructions on installing Terraform. For validating the version run `terraform version` command after install.

- **IBM Cloud Terraform Provider v1.9.0**: Please refer to the section "Install the IBM Cloud Provider plug-in" from the [link](https://cloud.ibm.com/docs/terraform?topic=terraform-getting-started#install) for instructions on installing the provider plugin.

- **PowerVS CLI**: Please download and install the CLI by referring to the following [instructions](https://cloud.ibm.com/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference).

- **Git**: [*OPTIONAL*] Please refer to the [link](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) for instructions on installing Git.

### Terraform Providers

At present Terraform registry does not support below plugins. Third-party providers can be manually installed using [local filesystem as a mirror](https://www.terraform.io/docs/commands/cli-config.html#filesystem_mirror). This is in addition to the provider plugins that are downloaded by Terraform during `terraform init`.

**Ignition provider v2.1.0**

1. Download the zip archive from [community-terraform-provider releases page](https://github.com/community-terraform-providers/terraform-provider-ignition/releases/tag/v2.1.0) .

2. Depending on your Operating System, create the Terraform plugins directory on your local filesystem if does not exist already.

> Linux: ~/.local/share/terraform/plugins OR /usr/local/share/terraform/plugins, OR /usr/share/terraform/plugins.

> Mac OSX: ~/Library/Application Support/io.terraform/plugins OR /Library/Application Support/io.terraform/plugins

> Windows: %APPDATA%/HashiCorp/Terraform/plugins

3. Under the path created in Step 2 please create the Igniton provider directory: `registry.terraform.io/terraform-providers/ignition/`
4. Place the downloaded zip file in Step 1 to `registry.terraform.io/terraform-providers/ignition/`

This is how the directory look for `linux_amd64`:
```
$ ls ~/.local/share/terraform/plugins/registry.terraform.io/terraform-providers/ignition/
terraform-provider-ignition_2.1.0_linux_amd64.zip
$
```
# PowerVS Prerequisites

Follow the [guide](docs/ocp_prereqs_powervs.md) to complete the PowerVS prerequisites.

# OCP Install

Follow the [quickstart](docs/quickstart.md) guide for OCP installation on PowerVS.


# Contributing
Please see the [contributing doc](https://github.com/ocp-power-automation/ocp4-upi-powervs/blob/master/CONTRIBUTING.md) for more details.
PRs are most welcome !!
