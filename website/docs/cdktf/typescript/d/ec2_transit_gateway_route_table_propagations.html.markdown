---
subcategory: "Transit Gateway"
layout: "aws"
page_title: "AWS: aws_ec2_transitgateway_route_table_propagations"
description: |-
   Provides information for multiple EC2 Transit Gateway Route Table Propagations
---

# Data Source: aws_ec2_transitgateway_route_table_propagations

Provides information for multiple EC2 Transit Gateway Route Table Propagations, such as their identifiers.

## Example Usage

### By Transit Gateway Identifier

```terraform
data "aws_ec2_transit_gateway_route_table_propagations" "example" {
  transit_gateway_route_table_id = aws_ec2_transit_gateway_route_table.example.id
}
```

## Argument Reference

The following arguments are required:

* `transitGatewayRouteTableId` - (Required) Identifier of EC2 Transit Gateway Route Table.

The following arguments are optional:

* `filter` - (Optional) Custom filter block as described below.

More complex filters can be expressed using one or more `filter` sub-blocks,
which take the following arguments:

* `name` - (Required) Name of the field to filter by, as defined by
  [the underlying AWS API](https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_GetTransitGatewayRouteTablePropagations.html).

* `values` - (Required) Set of values that are accepted for the given field.
  A Transit Gateway Route Table will be selected if any one of the given values matches.

## Attributes Reference

In addition to all arguments above, the following attributes are exported:

* `id` - AWS Region.
* `ids` - Set of Transit Gateway Route Table Association identifiers.

<!-- cache-key: cdktf-0.17.0-pre.15 input-a62abe28e531fd8e1af6114d984180c2997a6bff69c0a5c03d6e3a0644a3e17c -->