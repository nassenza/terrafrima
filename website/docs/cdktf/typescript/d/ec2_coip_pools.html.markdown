---
subcategory: "Outposts (EC2)"
layout: "aws"
page_title: "AWS: aws_ec2_coip_pools"
description: |-
    Provides information for multiple EC2 Customer-Owned IP Pools
---

# Data Source: aws_ec2_coip_pools

Provides information for multiple EC2 Customer-Owned IP Pools, such as their identifiers.

## Example Usage

The following shows outputting all COIP Pool Ids.

```terraform
data "aws_ec2_coip_pools" "foo" {}

output "foo" {
  value = data.aws_ec2_coip_pools.foo.ids
}
```

## Argument Reference

* `tags` - (Optional) Mapping of tags, each pair of which must exactly match
  a pair on the desired aws_ec2_coip_pools.

* `filter` - (Optional) Custom filter block as described below.

More complex filters can be expressed using one or more `filter` sub-blocks,
which take the following arguments:

* `name` - (Required) Name of the field to filter by, as defined by
  [the underlying AWS API](https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_DescribeCoipPools.html).

* `values` - (Required) Set of values that are accepted for the given field.
  A COIP Pool will be selected if any one of the given values matches.

## Attributes Reference

* `id` - AWS Region.
* `poolIds` - Set of COIP Pool Identifiers

## Timeouts

[Configuration options](https://developer.hashicorp.com/terraform/language/resources/syntax#operation-timeouts):

- `read` - (Default `20M`)

<!-- cache-key: cdktf-0.17.0-pre.15 input-c1c9a426e16105b7a02e1c1b1adc831132ac241239b921ea8b6a60157547ed64 -->