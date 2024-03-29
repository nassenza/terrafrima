---
subcategory: "Outposts (EC2)"
layout: "aws"
page_title: "AWS: aws_ec2_local_gateway_virtual_interface"
description: |-
    Provides details about an EC2 Local Gateway Virtual Interface
---

# Data Source: aws_ec2_local_gateway_virtual_interface

Provides details about an EC2 Local Gateway Virtual Interface. More information can be found in the [Outposts User Guide](https://docs.aws.amazon.com/outposts/latest/userguide/outposts-networking-components.html#routing).

## Example Usage

```terraform
data "aws_ec2_local_gateway_virtual_interface" "example" {
  for_each = data.aws_ec2_local_gateway_virtual_interface_group.example.local_gateway_virtual_interface_ids

  id = each.value
}
```

## Argument Reference

The following arguments are optional:

* `filter` - (Optional) One or more configuration blocks containing name-values filters. See the [EC2 API Reference](https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_DescribeLocalGatewayVirtualInterfaces.html) for supported filters. Detailed below.
* `id` - (Optional) Identifier of EC2 Local Gateway Virtual Interface.
* `tags` - (Optional) Key-value map of resource tags, each pair of which must exactly match a pair on the desired local gateway route table.

### filter Argument Reference

The `filter` configuration block supports the following arguments:

* `name` - (Required) Name of the filter.
* `values` - (Required) List of one or more values for the filter.

## Attribute Reference

In addition to all arguments above, the following attributes are exported:

* `localAddress` - Local address.
* `localBgpAsn` - Border Gateway Protocol (BGP) Autonomous System Number (ASN) of the EC2 Local Gateway.
* `localGatewayId` - Identifier of the EC2 Local Gateway.
* `peerAddress` - Peer address.
* `peerBgpAsn` - Border Gateway Protocol (BGP) Autonomous System Number (ASN) of the peer.
* `vlan` - Virtual Local Area Network.

## Timeouts

[Configuration options](https://developer.hashicorp.com/terraform/language/resources/syntax#operation-timeouts):

- `read` - (Default `20M`)

<!-- cache-key: cdktf-0.17.0-pre.15 input-8e096e1216ac507f824ce02a9ba18794bf5791c0f496d83b673af9b7c193c051 -->