---
title: "Week 2 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.2. </b> "
---

**Full Name:** Dinh Tuan Minh &emsp; | &emsp; **Student ID:** 2280601918

**Company Mentor:** Nguyen Gia Hung – Head of Solution Architect &emsp; | &emsp; **Academic Supervisor:** Vo Pham Thanh Luan

### Week 2 Objectives:

* Understand the fundamentals of Amazon Virtual Private Cloud (VPC), including how to design a virtual private network, split subnets, set up routing, and connect AWS resources to the Internet.
* Understand VPC network security components such as Security Groups, Network ACLs, inbound/outbound traffic control mechanisms, and how to organize a multi-VPC architecture.
* Practice building AWS network connectivity models such as NAT Gateway, EC2 Instance Connect Endpoint, Route 53 Resolver, VPC Peering, and Transit Gateway.
* Build a network architecture design mindset for the cloud that is secure, scalable, and easy to manage.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                                    | Start Date | Completion Date | Reference Material                        |
| --- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------- | ----------------------------------------- |
| 2   | - AWS Virtual Private Cloud: CIDR block, subnet, route table, Internet Gateway, NAT Gateway, splitting public/private subnets <br> - VPC Security and Multi-VPC: Security Group, Network ACLs, VPC Peering, Transit Gateway <br> - VPN, Direct Connect, Load Balancer, and additional resources | 04/27/2026 | 04/27/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - **Practice basic VPC:** <br>&emsp; + Learn Subnets, Route table, Internet Gateway, NAT Gateway <br>&emsp; + Practice Security Group and Network ACLs, observe the VPC Resource Map <br>&emsp; + Create a VPC, Subnet, Internet Gateway, Route table, and Security Group <br>&emsp; + Create an EC2 instance in a subnet and test connectivity <br>&emsp; + Create a NAT Gateway and an EC2 Instance Connect Endpoint | 04/28/2026 | 04/28/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - **Practice Hybrid DNS with Route 53 Resolver:** <br>&emsp; + Generate a Key Pair, initialize a CloudFormation template, configure Security Group <br>&emsp; + Connect to RDGW and set up DNS <br>&emsp; + Create Route 53 Outbound Endpoint, Resolver Rules, and Inbound Endpoint <br>&emsp; + Test results and clean up resources | 04/29/2026 | 04/29/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - **Practice VPC Peering:** <br>&emsp; + Initialize CloudFormation, create Security Group and EC2 instance <br>&emsp; + Update Network ACL, create a Peering Connection <br>&emsp; + Configure Route tables and enable Cross-Peer DNS <br>&emsp; + Clean up resources | 04/30/2026 | 04/30/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - **Practice AWS Transit Gateway:** <br>&emsp; + Prepare resources, create a Transit Gateway <br>&emsp; + Create Transit Gateway Attachments and Route Tables <br>&emsp; + Update VPC Route Tables, clean up resources <br> - Consolidate knowledge, write the Week 2 report | 05/01/2026 | 05/01/2026      | <https://cloudjourney.awsstudygroup.com/> |

### Week 2 Achievements:

* Completed the core theory of Amazon VPC, gaining a better understanding of VPC's role in designing network infrastructure on AWS.
* Learned to distinguish and use the main networking components: VPC, subnet, route table, Internet Gateway, NAT Gateway, Security Group, and Network ACLs.
* Practiced deploying a public/private subnet model, configuring outbound Internet routing, testing EC2 connectivity, and understanding how to protect resources in a private subnet.
* Learned the Hybrid DNS model with Route 53 Resolver, including inbound endpoint, outbound endpoint, and resolver rule.
* Understood the difference between VPC Peering and Transit Gateway: VPC Peering suits point-to-point connections, while Transit Gateway suits a hub-and-spoke model when many VPCs need centralized connectivity.
* Practiced the mindset of cleaning up resources after labs to avoid unnecessary costs.

### Challenges and Solutions:

| Challenge | Solution |
| --- | --- |
| Easy to confuse Security Group and Network ACL since both relate to traffic control. | Built a comparison table: Security Group operates at the instance/ENI level and is stateful; Network ACL operates at the subnet level and is stateless. |
| Route table configuration has many different cases, such as routing via IGW, NAT Gateway, VPC Peering, or Transit Gateway. | Took notes following the traffic flow diagram: source, destination, next hop, and applicable subnet to avoid misconfiguring routes. |
| Hybrid DNS concepts, inbound/outbound endpoints, and resolver rules were still new. | Redrew the DNS query model along the direction of the request to clearly understand which endpoint receives/answers the query. |
| Practicing many labs created a large number of resources, which were easy to miss during clean up. | Rechecked each resource group after each lab, such as EC2, NAT Gateway, VPC endpoint, Route 53 Resolver endpoint, peering connection, and Transit Gateway attachment. |

### Lessons Learned:

* When designing a network on AWS, clearly define the purpose of each subnet before deployment: which subnet is public, which is private, and which is used for endpoints or internal resources.
* The route table determines the path of traffic. Creating a gateway or peering connection alone is not enough; routes must be configured correctly in both directions for the connection to work reliably.
* Network security should be implemented in multiple layers. Security Group controls at the instance level, while Network ACL adds a control layer at the subnet level.
* For systems with multiple VPCs, choose the right connectivity model. VPC Peering is simple for a few VPCs, but Transit Gateway is easier to manage as the number of VPCs grows.
* Always clean up resources after practicing, especially NAT Gateway, Transit Gateway, and Route 53 Resolver Endpoint, since these resources can incur costs if left running.

### Next Week's Plan:

* Continue the Bootcamp First Cloud AI Journey program, moving on to AWS Compute and Storage Services.
* Learn Amazon EC2: Instance Type, AMI, EBS, Instance Store, User Data, and EC2 Auto Scaling.
* Learn extended services: Amazon EFS, FSx, Lightsail, and AWS MGN (Application Migration Service).
* Practice labs on AWS Backup, AWS Storage Gateway, and deploying a static website on S3 combined with Amazon CloudFront.
