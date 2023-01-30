---
title: "Walkthrough of AWS"
date: 2020-06-08T06:00:20+06:00
menu:
  sidebar:
    name: Walkthrough of AWS
    identifier: walkthrough_aws
    parent: cloudi
    weight: 2
---

- Made an AWS account alongside exploring AWSEducate portal.
  [AWS Educate](https://aws.amazon.com/education/awseducate/)

- Important terminologies:
  - Ec2: In niche terms, ec2 is equivalent to a Virtual Machine in AWS. We may create, use, terminate and destroy ec2 instances according
    to our needs.


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
  

- Terminated an instance created previously.
  ```
  aws ec2 terminate-instance --instance-id i-08431b825258399a3
  
  ```
  {{<asciinema gqo6TMWfbeUhYWBL3o1Ga5V12>}}

- Tried pinging the VM created.
  {{<asciinema JKThgzuwECCT8I43LJJajpOOU>}}
  
- Experimented around by creating instances with different subnets, security groups and VPCs linked. 
  
  - Discovered that security group must have an inbound SSH rule, which has port 22 as ingress.
  
  - Finally made a successful SSH connection.
    {{<asciinema ACr3ZW8Q8xU4MUt7VtQONu72H>}}
    