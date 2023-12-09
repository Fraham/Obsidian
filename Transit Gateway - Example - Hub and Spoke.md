Hub and Spoke is an example of a [[Transit Gateway]] architecture. All traffic needs to go through the central hub before going to its destination. This method helps when building a network that needs to have a controlled ingress/egress and [[Traffic Inspection]]

A typical design is to have each workload in its own [[VPC]], a VPC for handing internet traffic and a Traffic Inspection VPC.

## Design

The Transit Gateway can be setup with two [[Transit Gateway - Route Table]]s. One will handle the traffic as its comes from its source VPC and the other will handle traffic after it has been inspected. 

As all traffic in our network needs to be inspected before reaching its destination the first route table will send all traffic to the inspection VPC. The second route table is in charge of making sure the traffic gets to its destination.

In terms of [[Transit Gateway - Route Table - Association]]s, the inspection VPC will have an association to the second route table and all the other VPCs will be associated with the first.

In terms of [[Transit Gateway - Route Table - Propagation]]s, the inspection VPC will propagate on the first route table and the rest will be on the second route table.

In terms of [[Transit Gateway - Route Table - Route]]s, the first route table will have a route for all traffic (`0.0.0.0/0`) to go to the inspection VPC. In the second route table, the propagations should handle making most of the routes for us, we just need to define a route for all non-matching traffic (`0.0.0.0/0`) to go to the ingress/egress VPC and then out to the internet.

## Example Flows

- [ ] Add some flows here

## Concerns

* How do we stop traffic going from one environment to another that it shouldn't have access to?
* What do the NAT gateways look like with their IP addresses, what would a third party white-list?
* Connecting in other regions, would the traffic be inspected twice?