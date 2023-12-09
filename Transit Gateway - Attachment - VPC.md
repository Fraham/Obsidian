[AWS Documentation](https://docs.aws.amazon.com/vpc/latest/tgw/tgw-vpn-attachments.html)

Allows to connect a [[VPC]] to [[Transit Gateway]]

Make sure each [[Subnet]] has a [[Subnet - Route Table - Route]] pointing back to the [[Transit Gateway]] for any outbound or returning traffic. Use the [[CIDR]] of the destination.

Can only attach [[VPC]]s that are in the same [[Region]] as the [[Transit Gateway]]. To link across multiple [[Region]]s a second [[Transit Gateway]] is required with a [[Transit Gateway - Attachment - Transit Gateway]].