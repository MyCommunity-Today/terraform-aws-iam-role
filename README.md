<p align="left"><img width=400 height="100" src="https://www.nclouds.com/img/nclouds-logo.svg"></p>  

![Terraform](https://github.com/nclouds/terraform-aws-iam-role/workflows/Terraform/badge.svg)
# nCode Library

## AWS Identity and Access Management Role (IAM Role) Terraform Module

Terraform module to provision [`IAM Role`](https://aws.amazon.com/iam/) on AWS.

## Usage

### Setup

Create a IAM Role.
```hcl
    module "example_role" {
        source      = "git@github.com:nclouds/terraform-aws-iam-role.git?ref=v0.2.4"
        description = "Example IAM Role"
        iam_policies_to_attach = [
            "arn:aws:iam::aws:policy/service-role/AmazonEC2ContainerServiceforEC2Role",
            "arn:aws:iam::aws:policy/AmazonSSMManagedInstanceCore"
        ]
        aws_service_principal = "ec2.amazonaws.com"
        identifier            = "example-role"
        tags                  = {
            Owner       = "sysops"
            env         = "dev"
            Cost_Center = "XYZ"
        }
    }
```

## Examples
Here are some working examples of using this module:
- [`examples/`](examples/)


<!-- BEGINNING OF PRE-COMMIT-TERRAFORM DOCS HOOK -->
## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) | >= 0.12 |

## Providers

| Name | Version |
|------|---------|
| <a name="provider_aws"></a> [aws](#provider\_aws) | n/a |

## Modules

| Name | Source | Version |
|------|--------|---------|
| <a name="module_common_tags"></a> [common\_tags](#module\_common\_tags) | git@github.com:nclouds/terraform-aws-common-tags.git | v0.1.1 |

## Resources

| Name | Type |
|------|------|
| [aws_iam_instance_profile.profile](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_instance_profile) | resource |
| [aws_iam_role.role](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_role) | resource |
| [aws_iam_role_policy_attachment.attach](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_role_policy_attachment) | resource |
| [aws_caller_identity.current](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/caller_identity) | data source |
| [aws_iam_policy_document.default](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/iam_policy_document) | data source |
| [aws_iam_policy_document.oidc](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/iam_policy_document) | data source |
| [aws_partition.current](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/partition) | data source |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| <a name="input_append_workspace"></a> [append\_workspace](#input\_append\_workspace) | Appends the terraform workspace at the end of resource names, <identifier>-<worspace> | `bool` | `true` | no |
| <a name="input_aws_service_principal"></a> [aws\_service\_principal](#input\_aws\_service\_principal) | The service principal allowed to assume this role. Example: 'ec2.amazonaws.com'. Not needed if using oidc | `string` | `""` | no |
| <a name="input_description"></a> [description](#input\_description) | Description for the IAM role | `string` | `"Created by terraform"` | no |
| <a name="input_iam_policies_to_attach"></a> [iam\_policies\_to\_attach](#input\_iam\_policies\_to\_attach) | List of ARNs of IAM policies to attach | `list(string)` | `[]` | no |
| <a name="input_identifier"></a> [identifier](#input\_identifier) | Name for the resources | `string` | n/a | yes |
| <a name="input_oidc_fully_qualified_subjects"></a> [oidc\_fully\_qualified\_subjects](#input\_oidc\_fully\_qualified\_subjects) | The fully qualified OIDC subjects to be added to the role policy | `set(string)` | `[]` | no |
| <a name="input_principal_type"></a> [principal\_type](#input\_principal\_type) | Principal type to be used i.e. Service, AWS | `string` | `"Service"` | no |
| <a name="input_provider_urls"></a> [provider\_urls](#input\_provider\_urls) | List of URLs of the OIDC Providers | `list(string)` | `[]` | no |
| <a name="input_tags"></a> [tags](#input\_tags) | Tags to be applied to the resource | `map(any)` | `{}` | no |

## Outputs

| Name | Description |
|------|-------------|
| <a name="output_output"></a> [output](#output\_output) | n/a |
<!-- END OF PRE-COMMIT-TERRAFORM DOCS HOOK -->

## Contributing
If you want to contribute to this repository check all the guidelines specified [here](.github/CONTRIBUTING.md) before submitting a new PR.
