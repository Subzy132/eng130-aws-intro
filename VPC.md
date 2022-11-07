# VPC
### What is a VPC? 

A virtual private cloud is an isolated virtual netwrok on the AWS cloud. Here you are able to specify IP address ranges for the VPC, add subnets, gateways and add security groups. 

---

### What is an Internet Gateway?

It is a VPC component that allows communication between the internet and the VPC by supporting IPv4 and IPv6 traffic. 

---
### What is a Route table? 

The route table contains existing routes with targets other than a network interface, Gateway Load Balancer endpoint, or the default local route. The route table contains existing routes to CIDR blocks outside of the ranges in your VPC. Route propagation is enabled for the route table.

---
### What is CIDR blocks?

This CIDR block determines the range of IP addresses allocated for your apps in the VPC. For an Anypoint VPC, the size of this CIDR needs to be a number between 24 (256 Ips) and 16 (65,536 IPs).

---

### What is a subnet? 

A subnet is a range of IP addresses in your VPC. You launch AWS resources, such as Amazon EC2 instances, into your subnets. You can connect a subnet to the internet, other VPCs, and your own data centers, and route traffic to and from your subnets using route tables.

---
### What is a NACL?

A network access control list (NACL) is an optional layer of security for your VPC that acts as a firewall for controlling traffic in and out of one or more subnets. You might set up network ACLs with rules similar to your security groups in order to add an additional layer of security to your VPC.

---
### What is the difference between NACL and security group?

Security group is the security on an instance level and a NACL is a security procedure on a subnet level.These are stateless, meaning any change applied to an incoming rule isn't automatically applied to an outgoing rule.

---

### how to connect app subnet - to db subnet in order facilitate the user request for db

Set up a subnet that allows deals with only the user requests and then when there is a request that needs the database the database only allows access from the app's subnet so the app will be able to go through the NACL and retrieve the request. 

