[AWS Documentation](https://docs.aws.amazon.com/vpc/latest/tgw/tgw-peering.html)

Also know as Transit Gateway Peering. This attachment allows for 2 or more [[Transit Gateway]]s to talk with each other.

The main use case is to connect different accounts or [[Region]]s together.
Make sure to setup [[Transit Gateway Route]] to all the [[CIDR]]s in the connecting [[Transit Gateway]]s.

To connect gateways together, one will send a request to the other. In [[Terraform]] make sure not to create requests going both ways.