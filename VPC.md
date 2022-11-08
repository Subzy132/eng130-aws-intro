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

### Steps on creating a vpc

1. Create a `VPC` - 10.0.0.0/16
2. Create an `internet gateway (IG)`
   1. Attch the `IG` to our `VPC`
3. Create a `public subnet` - 10.0.1.0./24
4. Create a `route table (RT)` - attatch to VPC
   1. Add routes to connect to IG - 0.0.0.0/0
   2. Associate RT to public subnet
5. Launch new ec2
6. To load app launch `new ec2` using a app ami and ssh in 
   

Public CIDR block 10.0.12.0/24
private CIDR block 10.0.24.0/24

## Detailed steps on creating VPC

### Creating the VPC

1. Search for `VPC`
2. On the left hand side click `VPC`
3. Now click on `create VPC`
4. A pop-up will appear
5. Click `VPC only`
6. Add `10.0.0.0/16`
7. and leave the rest how it is

 ### Creating the internet gateway

 1. On the left hand side of VPC dashboard click `internet gateway`
 2. Click on `create internet gateway`
 3. Enter name using best practices i.e `eng130-subhaan-ig`
 4. Click `create internet gateway`

### Attaching the IG to VPC

1. On the left hand side of the VPC dashboard
2. Click on `Internet Gateways`
3. Select the `Internet Gateway` that you just created 
4. Click on `Actions`
5. Click on `Attach to VPC`
6. Select the VPC `eng130-subhaan-vpc`
7. Click on Attach Internet Gateway


### Creating the subnets

1. On the left hand side of the VPC dashboard
2. Click on `Subnets`
3. Click on `Create Subnet`
4. Enter `eng130-subhaan-public-subnet`
5. Select the VPC `eng130-subhaan-vpc`
6. Enter a IPv4 CIDR block `10.0.12.0/24` for the public subnet
7. You can repeat these steps to create a private subnet
8. Change the name tag to `eng130-subhaan-private-subnet`
9. Change the IPv4 CIDR block to 10.0.24.0/24

### Creating Route Tables

1. Click on `Route Tables`
2. Click on `Create Route Table` button
3. Enter an appropriate name `eng130-subhaan-public-rt`
4. Select the VPC `eng130-subhaan-vpc`
5. Click on `Create Route Table`
6. You can then repeat these steps to create a private route table
7. Change the name tag to `eng130-subhaan-private-rt`

### Add Route to the Route Tables

1. Click on `Route Tables`
2. Select the route table you just made 
3. Click on `Routes`
4. Click on `Edit routes`
5. Click on `Add route`
6. Enter a destination `0.0.0.0/0`
7. Select the internet gateway as the target `eng130-subhaan-ig`
8. Click on `Save routes`
9. Add Route

### Associating the Route Table with the Subnet

1. Click on `Route Tables`
1. Select the newly created public route table
1. Click on Subnet Associations
1. Click on Edit subnet associations
1. Select the public subnet eng130-public-subnet
1. Click on Save subnet associations
1. Repeat the steps to associate the private route table with the private subnet
1. Associate Route Table

### Launch an EC2 Instance in the Public Subnet
Follow the steps to launch an EC2 instance
Select the App Server AMI
Edit the network settings
Select the newly created VPC eng130-vpc
Select the public subnet as No Preference
Enable auto-assign public IP
Select create a new security group
Enter a name tag eng130-app-sg
Add a rule to allow HTTP traffic
Add a rule to allow SSH traffic
Click on Review and Launch
Launch EC2 Instance

## Launch an EC2 Instance in the Private Subnet
Follow the steps to launch an EC2 instance
Select the Database Server AMI
Edit the network settings
Select the newly created VPC eng130-vpc
Select the private subnet as No Preference
Disable auto-assign public IP
Create a new security group
Enter a name tag eng130-db-sg
Add a rule to allow SSH traffic
Add a rule to allow Mongodb traffic from the app server public subnet i.e. port: 27017 source: 10.0.X.0/24
Click on Review and Launch