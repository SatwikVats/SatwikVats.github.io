---
title: "Day 19"
date: 2020-06-08T06:00:20+06:00
menu:
  sidebar:
    name: 1 July
    identifier: Daily Updates-day19
    parent: Daily Updates
    weight: 10
---

- Experimentation with various AWS resources using CLI.
 
  - Created a VPC.
    ```
    aws ec2 create-vpc --cidr-block 10.10.1.0/24
    
    ```
    
  - Attempted making a subnet linked to that VPC, but failed since the CIDR turned out to be invalid.
    ```
    aws ec2 create-subnet --vpc-id vpc-0fd87e36fb326f175 --cidr-block 10.10.1.0/16
    
    ```
    {{<asciinema Qq4NnuOFLvJnYm74qgaCz620K>}}
    
  - Created Internet Gateway and attached it to a VPC.
    ```
    aws ec2 create-internet-gateway
    aws ec2 attach-internet-gateway --vpc-id vpc-0fd87e36fb326f175 --internet-gateway-id igw-0f75ad3c966f9bb6b
    
    ```
  - Created a route-table and linked the route to the gateway as well.
    ```
    aws ec2 create-route-table --vpc-id vpc-0fd87e36fb326f175
    aws ec2 create-route --route-table-id rtb-060a13637f368b43d --destination-cidr-block 0.0.0.0/0 --gateway-id igw-0f75ad3c966f9bb6b
    
    ``` 
    {{<asciinema A7X1IVDcaNqgmdsyKSSMw5sOQ>}}
    
  - Tried changing IP of VPC, but realised that I was using `modify` command in an improper way.
    {{<asciinema fwpBqBOB1TZeBhIDF6b8yx57W>}}
    
  - Managed to create a subnet after associating a secondary cidr block with new IP range.
    ```
    aws ec2 create-subnet --vpc-id vpc-0fd87e36fb326f175 --cidr-block 10.0.1.0/16
    
    ```
    {{<asciinema 91nMiwoaR0NH3P0YJ2IZDpPKB>}}
  
- IP address are 32 bits represented by 4 integers separated by "." Each integer ranges from 0 to 255. /16 implies only first 16 bits are required rest are part of the subnet.

- Terminated an instance created previously.
  ```
  aws ec2 terminate-instance --instance-id i-08431b825258399a3
  
  ```
  {{<asciinema gqo6TMWfbeUhYWBL3o1Ga5V12>}}
  
- Spent some time on learning about Kubernetes.
  
  - Its utility as a Container Management Tool.
  - Procedure of installation via three nodes- one master along with two slave nodes.
  
- References-
  
  - [Kubernetes for beginners](https://www.youtube.com/watch?v=l_lWfipUimk)


