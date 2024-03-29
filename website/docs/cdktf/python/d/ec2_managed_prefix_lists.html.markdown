---
subcategory: "VPC (Virtual Private Cloud)"
layout: "aws"
page_title: "AWS: aws_ec2_managed_prefix_lists"
description: |-
    Get information on managed prefix lists
---

# Data Source: aws_ec2_managed_prefix_lists

This resource can be useful for getting back a list of managed prefix list ids to be referenced elsewhere.

## Example Usage

The following returns all managed prefix lists filtered by tags

```python
import constructs as constructs
import cdktf as cdktf
# Provider bindings are generated by running cdktf get.
# See https://cdk.tf/provider-generation for more details.
import ...gen.providers.aws as aws
class MyConvertedCode(cdktf.TerraformStack):
    def __init__(self, scope, name):
        super().__init__(scope, name)
        data_aws_ec2_managed_prefix_lists_test_env =
        aws.data_aws_ec2_managed_prefix_lists.DataAwsEc2ManagedPrefixLists(self, "test_env",
            tags={
                "Env": "test"
            }
        )
        # In most cases loops should be handled in the programming language context and
        #     not inside of the Terraform context. If you are looping over something external, e.g. a variable or a file input
        #     you should consider using a for loop. If you are looping over something only known to Terraform, e.g. a result of a data source
        #     you need to keep this like it is.
        data_aws_ec2_managed_prefix_list_test_env_count = cdktf.TerraformCount.of(
            cdktf.Fn.length_of(data_aws_ec2_managed_prefix_lists_test_env.ids))
        data_aws_ec2_managed_prefix_list_test_env =
        aws.data_aws_ec2_managed_prefix_list.DataAwsEc2ManagedPrefixList(self, "test_env_1",
            id=cdktf.Token.as_string(
                cdktf.property_access(
                    cdktf.Fn.tolist(data_aws_ec2_managed_prefix_lists_test_env.ids), [data_aws_ec2_managed_prefix_list_test_env_count.index])),
            count=data_aws_ec2_managed_prefix_list_test_env_count
        )
        # This allows the Terraform resource name to match the original name. You can remove the call if you don't need them to match.
        data_aws_ec2_managed_prefix_list_test_env.override_logical_id("test_env")
```

## Argument Reference

* `filter` - (Optional) Custom filter block as described below.
* `tags` - (Optional) Map of tags, each pair of which must exactly match
  a pair on the desired .

More complex filters can be expressed using one or more `filter` sub-blocks,
which take the following arguments:

* `name` - (Required) Name of the field to filter by, as defined by
  [the underlying AWS API](https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_DescribeManagedPrefixLists.html).
* `values` - (Required) Set of values that are accepted for the given field.
  A managed prefix list will be selected if any one of the given values matches.

## Attributes Reference

* `id` - AWS Region.
* `ids` - List of all the managed prefix list ids found.

## Timeouts

[Configuration options](https://developer.hashicorp.com/terraform/language/resources/syntax#operation-timeouts):

- `read` - (Default `20m`)

<!-- cache-key: cdktf-0.17.0-pre.15 input-34b67ee42a5e4e01675b0661ae691e66cc897092214d5887d7cc8ea40ac77b4a -->