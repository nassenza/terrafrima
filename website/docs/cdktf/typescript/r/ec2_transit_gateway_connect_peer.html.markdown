---
subcategory: "Transit Gateway"
layout: "aws"
page_title: "AWS: aws_ec2_transit_gateway_connect_peer"
description: |-
  Manages an EC2 Transit Gateway Connect Peer
---

# Resource: aws_ec2_transit_gateway_connect_peer

Manages an EC2 Transit Gateway Connect Peer.

## Example Usage

```terraform
resource "aws_ec2_transit_gateway_connect" "example" {
  transport_attachment_id = aws_ec2_transit_gateway_vpc_attachment.example.id
  transit_gateway_id      = aws_ec2_transit_gateway.example.id
}

resource "aws_ec2_transit_gateway_connect_peer" "example" {
  peer_address                  = "10.1.2.3"
  inside_cidr_blocks            = ["169.254.100.0/29"]
  transit_gateway_attachment_id = aws_ec2_transit_gateway_connect.example.id
}
```

## Argument Reference

The following arguments are supported:

* `bgpAsn` - (Optional) The BGP ASN number assigned customer device. If not provided, it will use the same BGP ASN as is associated with Transit Gateway.
* `insideCidrBlocks` - (Required) The CIDR block that will be used for addressing within the tunnel. It must contain exactly one IPv4 CIDR block and up to one IPv6 CIDR block. The IPv4 CIDR block must be /29 size and must be within 169.254.0.0/16 range, with exception of: 169.254.0.0/29, 169.254.1.0/29, 169.254.2.0/29, 169.254.3.0/29, 169.254.4.0/29, 169.254.5.0/29, 169.254.169.248/29. The IPv6 CIDR block must be /125 size and must be within fd00::/8. The first IP from each CIDR block is assigned for customer gateway, the second and third is for Transit Gateway (An example: from range 169.254.100.0/29, .1 is assigned to customer gateway and .2 and .3 are assigned to Transit Gateway)
* `peerAddress` - (Required) The IP addressed assigned to customer device, which will be used as tunnel endpoint. It can be IPv4 or IPv6 address, but must be the same address family as `transitGatewayAddress`
* `tags` - (Optional) Key-value tags for the EC2 Transit Gateway Connect Peer. If configured with a provider [`defaultTags` configuration block](https://registry.terraform.io/providers/hashicorp/aws/latest/docs#default_tags-configuration-block) present, tags with matching keys will overwrite those defined at the provider-level.
* `transitGatewayAddress` - (Optional) The IP address assigned to Transit Gateway, which will be used as tunnel endpoint. This address must be from associated Transit Gateway CIDR block. The address must be from the same address family as `peerAddress`. If not set explicitly, it will be selected from associated Transit Gateway CIDR blocks
* `transitGatewayAttachmentId` - (Required) The Transit Gateway Connect

## Attributes Reference

In addition to all arguments above, the following attributes are exported:

* `id` - EC2 Transit Gateway Connect Peer identifier
* `arn` - EC2 Transit Gateway Connect Peer ARN
* `tagsAll` - A map of tags assigned to the resource, including those inherited from the provider [`defaultTags` configuration block](https://registry.terraform.io/providers/hashicorp/aws/latest/docs#default_tags-configuration-block).

## Timeouts

[Configuration options](https://developer.hashicorp.com/terraform/language/resources/syntax#operation-timeouts):

- `create` - (Default `10M`)
- `delete` - (Default `10M`)

## Import

`awsEc2TransitGatewayConnectPeer` can be imported by using the EC2 Transit Gateway Connect Peer identifier, e.g.,

```
$ terraform import aws_ec2_transit_gateway_connect_peer.example tgw-connect-peer-12345678
```

<!-- cache-key: cdktf-0.17.0-pre.15 input-1f5256822c622c77c21ea6bcc2a5888752a92236b8b89351636b84119799598d -->