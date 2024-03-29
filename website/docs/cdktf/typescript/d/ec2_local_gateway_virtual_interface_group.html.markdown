---
subcategory: "Outposts (EC2)"
layout: "aws"
page_title: "AWS: aws_ec2_local_gateway_virtual_interface_group"
description: |-
    Provides details about an EC2 Local Gateway Virtual Interface Group
---

# Data Source: aws_ec2_local_gateway_virtual_interface_group

Provides details about an EC2 Local Gateway Virtual Interface Group. More information can be found in the [Outposts User Guide](https://docs.aws.amazon.com/outposts/latest/userguide/outposts-networking-components.html#routing).

## Example Usage

```terraform
data "aws_ec2_local_gateway_virtual_interface_group" "example" {
  local_gateway_id = data.aws_ec2_local_gateway.example.id
}
```

## Argument Reference

The following arguments are optional:

* `filter` - (Optional) One or more configuration blocks containing name-values filters. See the [EC2 API Reference](https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_DescribeLocalGatewayVirtualInterfaceGroups.html) for supported filters. Detailed below.
* `id` - (Optional) Identifier of EC2 Local Gateway Virtual Interface Group.
* `localGatewayId` - (Optional) Identifier of EC2 Local Gateway.
* `tags` - (Optional) Key-value map of resource tags, each pair of which must exactly match a pair on the desired local gateway route table.

### filter Argument Reference

The `filter` configuration block supports the following arguments:

* `name` - (Required) Name of the filter.
* `values` - (Required) List of one or more values for the filter.

## Attribute Reference

In addition to all arguments above, the following attributes are exported:

* `localGatewayVirtualInterfaceIds` - Set of EC2 Local Gateway Virtual Interface identifiers.

## Timeouts

[Configuration options](https://developer.hashicorp.com/terraform/language/resources/syntax#operation-timeouts):

- `read` - (Default `20M`)

<!-- cache-key: cdktf-0.17.0-pre.15 input-540e4780997710333dc225582410f2a266ebddd6e5fe16521de29c067a33a32d -->