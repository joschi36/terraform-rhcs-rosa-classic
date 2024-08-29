# ROSA Classic public with IDP and machine pools

## Introduction

This is a Terraform manifest example for creating a Red Hat OpenShift Service on AWS (ROSA) cluster. This example provides a structured configuration template that demonstrates how to deploy a ROSA cluster within your AWS environment by using Terraform.

This example includes:
- A ROSA cluster with public access and managed OIDC.
- All AWS resources (IAM and networking) that are created as part of the ROSA cluster module execution.
- "Day 2" Machine pool resources - created after the cluster creation is completed.
- "Day 2" Identity provider resource - created after the cluster creation is completed.

Note: This example involves the creation of various identity providers using placeholder values for illustrative purposes. These providers will not grant access to the cluster with the exception of the HTPasswd identity provider. You must supply your own pre-configured values for authentic identity providers.

## Prerequisites

* You have installed the [Terraform CLI](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli) (1.4.6+).
* You have an [AWS account](https://aws.amazon.com/free/?all-free-tier) and [associated credentials](https://docs.aws.amazon.com/IAM/latest/UserGuide/security-creds.html) that you can use to create resources. The credentials configured for the AWS provider (see the [Authentication and Configuration](https://registry.terraform.io/providers/hashicorp/aws/latest/docs#authentication-and-configuration) section in the AWS Terraform provider documentation).
* You have completed the [ROSA getting started AWS prerequisites](https://console.redhat.com/openshift/create/rosa/getstarted).
* You have a valid [OpenShift Cluster Manager API Token](https://console.redhat.com/openshift/token) configured (see [Authentication and configuration](https://registry.terraform.io/providers/terraform-redhat/rhcs/latest/docs#authentication-and-configuration) for more info).
* Recommended: You have installed the following CLI tools:
    * [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)
    * [ROSA CLI](https://docs.openshift.com/rosa/cli_reference/rosa_cli/rosa-get-started-cli.html)
    * [Openshift CLI (oc)](https://docs.openshift.com/rosa/cli_reference/openshift_cli/getting-started-cli.html)

<!-- BEGIN_AUTOMATED_TF_DOCS_BLOCK -->
## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) | >= 1.0 |
| <a name="requirement_aws"></a> [aws](#requirement\_aws) | >= 5.0 |
| <a name="requirement_random"></a> [random](#requirement\_random) | >= 2.0 |
| <a name="requirement_rhcs"></a> [rhcs](#requirement\_rhcs) | >= 1.6.2 |

## Providers

| Name | Version |
|------|---------|
| <a name="provider_random"></a> [random](#provider\_random) | >= 2.0 |

## Modules

| Name | Source | Version |
|------|--------|---------|
| <a name="module_github_idp"></a> [github\_idp](#module\_github\_idp) | ../../modules/idp | n/a |
| <a name="module_gitlab_idp"></a> [gitlab\_idp](#module\_gitlab\_idp) | ../../modules/idp | n/a |
| <a name="module_google_idp"></a> [google\_idp](#module\_google\_idp) | ../../modules/idp | n/a |
| <a name="module_htpasswd_idp"></a> [htpasswd\_idp](#module\_htpasswd\_idp) | ../../modules/idp | n/a |
| <a name="module_ldap_idp"></a> [ldap\_idp](#module\_ldap\_idp) | ../../modules/idp | n/a |
| <a name="module_machine_pool_1"></a> [machine\_pool\_1](#module\_machine\_pool\_1) | ../../modules/machine-pool | n/a |
| <a name="module_machine_pool_2"></a> [machine\_pool\_2](#module\_machine\_pool\_2) | ../../modules/machine-pool | n/a |
| <a name="module_openid_idp"></a> [openid\_idp](#module\_openid\_idp) | ../../modules/idp | n/a |
| <a name="module_rosa"></a> [rosa](#module\_rosa) | ../../ | n/a |

## Resources

| Name | Type |
|------|------|
| [random_password.client_id](https://registry.terraform.io/providers/hashicorp/random/latest/docs/resources/password) | resource |
| [random_password.client_secret](https://registry.terraform.io/providers/hashicorp/random/latest/docs/resources/password) | resource |
| [random_password.password](https://registry.terraform.io/providers/hashicorp/random/latest/docs/resources/password) | resource |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| <a name="input_cluster_name"></a> [cluster\_name](#input\_cluster\_name) | Name of the cluster. After the creation of the resource, it is not possible to update the attribute value. | `string` | n/a | yes |
| <a name="input_openshift_version"></a> [openshift\_version](#input\_openshift\_version) | The required version of Red Hat OpenShift for the cluster, for example '4.1.0'. If version is greater than the currently running version, an upgrade will be scheduled. | `string` | `"4.14.9"` | no |

## Outputs

No outputs.
<!-- END_AUTOMATED_TF_DOCS_BLOCK -->
