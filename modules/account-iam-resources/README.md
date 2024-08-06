# account-iam-resources

## Introduction

This Terraform sub-module manages the account-wide IAM roles and their associated policies. These roles are required when creating the necessary AWS resources for ROSA Classic cluster deployment.

These IAM resources can be created once and used across multiple ROSA Classic cluster creations.

For more information, see [About IAM resources for ROSA clusters that use STS](https://docs.openshift.com/rosa/rosa_architecture/rosa-sts-about-iam-resources.html#rosa-sts-about-iam-resources) in the ROSA documentation.

<!-- BEGIN_AUTOMATED_TF_DOCS_BLOCK -->
## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) | >= 1.0 |
| <a name="requirement_aws"></a> [aws](#requirement\_aws) | >= 4.0 |
| <a name="requirement_null"></a> [null](#requirement\_null) | >= 3.0.0 |
| <a name="requirement_random"></a> [random](#requirement\_random) | >= 2.0 |
| <a name="requirement_rhcs"></a> [rhcs](#requirement\_rhcs) | = 1.6.2 |
| <a name="requirement_time"></a> [time](#requirement\_time) | >= 0.9 |

## Providers

| Name | Version |
|------|---------|
| <a name="provider_aws"></a> [aws](#provider\_aws) | >= 4.0 |
| <a name="provider_null"></a> [null](#provider\_null) | >= 3.0.0 |
| <a name="provider_random"></a> [random](#provider\_random) | >= 2.0 |
| <a name="provider_rhcs"></a> [rhcs](#provider\_rhcs) | = 1.6.2 |
| <a name="provider_time"></a> [time](#provider\_time) | >= 0.9 |

## Modules

| Name | Source | Version |
|------|--------|---------|
| <a name="module_account_iam_policy"></a> [account\_iam\_policy](#module\_account\_iam\_policy) | terraform-aws-modules/iam/aws//modules/iam-policy | >=5.34.0 |
| <a name="module_account_iam_role"></a> [account\_iam\_role](#module\_account\_iam\_role) | terraform-aws-modules/iam/aws//modules/iam-assumable-role | >=5.34.0 |

## Resources

| Name | Type |
|------|------|
| [aws_iam_role_policy_attachment.role_policy_attachment](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_role_policy_attachment) | resource |
| [null_resource.validate_openshift_version](https://registry.terraform.io/providers/hashicorp/null/latest/docs/resources/resource) | resource |
| [random_string.default_random](https://registry.terraform.io/providers/hashicorp/random/latest/docs/resources/string) | resource |
| [time_sleep.account_iam_resources_wait](https://registry.terraform.io/providers/hashicorp/time/latest/docs/resources/sleep) | resource |
| [aws_iam_policy_document.custom_trust_policy](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/iam_policy_document) | data source |
| [aws_partition.current](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/partition) | data source |
| [rhcs_info.current](https://registry.terraform.io/providers/terraform-redhat/rhcs/1.6.2/docs/data-sources/info) | data source |
| [rhcs_policies.all_policies](https://registry.terraform.io/providers/terraform-redhat/rhcs/1.6.2/docs/data-sources/policies) | data source |
| [rhcs_versions.all_versions](https://registry.terraform.io/providers/terraform-redhat/rhcs/1.6.2/docs/data-sources/versions) | data source |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| <a name="input_account_role_prefix"></a> [account\_role\_prefix](#input\_account\_role\_prefix) | User-defined prefix for all generated AWS resources (default "account-role-<random>") | `string` | `null` | no |
| <a name="input_openshift_version"></a> [openshift\_version](#input\_openshift\_version) | The Openshift cluster version of the cluster those account roles are used for. | `string` | n/a | yes |
| <a name="input_path"></a> [path](#input\_path) | The ARN path for the account/operator roles as well as their policies. | `string` | `"/"` | no |
| <a name="input_permissions_boundary"></a> [permissions\_boundary](#input\_permissions\_boundary) | The ARN of the policy that is used to set the permissions boundary for the IAM roles in STS clusters. | `string` | `""` | no |
| <a name="input_tags"></a> [tags](#input\_tags) | List of AWS resource tags to apply. | `map(string)` | `null` | no |

## Outputs

| Name | Description |
|------|-------------|
| <a name="output_account_role_prefix"></a> [account\_role\_prefix](#output\_account\_role\_prefix) | The prefix used for all generated AWS resources. |
| <a name="output_account_roles_arn"></a> [account\_roles\_arn](#output\_account\_roles\_arn) | A map of Amazon Resource Names (ARNs) associated with the AWS IAM roles created. The key in the map represents the name of an AWS IAM role, while the corresponding value represents the associated Amazon Resource Name (ARN) of that role. |
| <a name="output_openshift_version"></a> [openshift\_version](#output\_openshift\_version) | The Openshift cluster version of the cluster those account roles are used for. |
| <a name="output_path"></a> [path](#output\_path) | The arn path for the account/operator roles as well as their policies. |
<!-- END_AUTOMATED_TF_DOCS_BLOCK -->
