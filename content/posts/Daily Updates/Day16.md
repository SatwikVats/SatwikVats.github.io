---
title: "Day 16"
date: 2020-06-08T06:00:20+06:00
menu:
  sidebar:
    name: 28 June
    identifier: Daily Updates-day16
    parent: Daily Updates
    weight: 10
---

- An attempt to deploy a VM as an IAM user.
  
  - Created a directory and initialized Terraform in it.
    {{<asciinema 45q0k5gvvUmmZrHv3ccpPjxJZ>}}
  
  - Installed AWS CLI package whic is required for using `aws` commands.
  
  - Used `aws configure` to provide necessary fields like Access Key ID, Secret Access Key, Default Region and Default Output Format.
    {{<asciinema YrDwVH8WqTOOt5lLNx6tmSjxo>}}
    
  - Though, the since the credentials were revoked, it didn't work out.
  
- Started making my own web-server using Terraform.

  - Defined the required resources listed as follows.
    
     ```
     provider "aws" {
     region  = "ap-south-1"
     access_key = "AKIAZNAFREL3FOSYINVD"
     secret_key = "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"
     }

     resource "aws_vpc" "prod-vpc" {
     cidr_block = "10.0.0.0/16"
     tags = {
     Name = "production_vpc"
     }
     }

     #To have a public address, we need to have an internet gateway.
     resource "aws_internet_gateway" "gw" {
     vpc_id = aws_vpc.prod-vpc.id

     }

     resource "aws_route_table" "prod-route-table" {
     vpc_id = aws_vpc.prod-vpc.id

     route {
     cidr_block = "0.0.0.0/0"
     gateway_id = aws_internet_gateway.gw.id
     }

    route {
    ipv6_cidr_block        = "::/0"
    egress_only_gateway_id = aws_internet_gateway.gw.id
    }

    tags = {
    Name = "prod"
    }
    }

    #Hard-coded the availability zone.
    resource "aws_subnet" "subnet-1" {
    vpc_id     = aws_vpc.main.id
    cidr_block = "10.0.1.0/24"
    availability_zone = "ap-south-1a"

    tags = {
    Name = "Main"
    }
    }

    resource "aws_route_table_association" "a" {
    subnet_id      = aws_subnet.subnet-1.id
    route_table_id = aws_route_table.prod-route-table.id
    }

    resource "aws_security_group" "allow_traffic" {
    name        = "allow_traffic"
    description = "Allow web traffic"
    vpc_id      = aws_vpc.prod-vpc.id

    ingress {
    description      = "HTTP"
    from_port        = 70
    to_port          = 70
    protocol         = "tcp"
    cidr_blocks      = [0.0.0.0/0]
    }

    ingress {
    description      = "SSH"
    from_port        = 5
    to_port          = 5
    protocol         = "tcp"
    cidr_blocks      = [0.0.0.0/0]
    }


    egress {
    from_port        = 0
    to_port          = 0
    protocol         = "-1"
    cidr_blocks      = ["0.0.0.0/0"]
    ipv6_cidr_blocks = ["::/0"]
    }

    tags = {
    Name = "allow_tls"
    }
    }

    resource "aws_network_interface" "web-server-1" {
    subnet_id       = aws_subnet.subnet-1.id
    private_ips     = ["10.0.1.50"]
    security_groups = [aws_security_group.allow_traffic.id]

    }

    resource "aws_eip" "one" {
    vpc                       = true
    network_interface         = aws_network_interface.web-server-1.id
    associate_with_private_ip = "10.0.0.50"
    depends_on = aws_internet_gateway.gw.id
    }
    
    #launching an ubuntu server
    resource "aws_instance" "web-server-instance" {
    ami = "ami-0c1a7f89451184c8b"
    instance_type = "t2.micro"
    availability_zone = "ap-south-1a"
    key_name = "main-key"

    network_interface {
    device_index = 0
    network_interface_id = aws_network_interface.web-server-1.id
    }
    }
    
    ```
    
  - Terminal recording for the same.
    {{<asciinema x7YDxkt9W9JkKfxz7pWNfrkOi>}}

- Few pointers to keep in mind.

  - Specifying IP as 0.0.0.0/0 indicates that our traffic can go/come from any IP address on the internet.
  
  - We may assign multiple IPs for network interface.
  
  - We must use the same private ip for aws_eip, the one we used for network interface.
  
  - We must use the same availability zone for subnet as well as Ubuntu server.
  
  - An availability zone may have multiple data centres. In case of a failure, other would work fine and hence, it is advisable to hard-code the availability zone with data-centre.
  
- References-

  - [Automating your AWS Cloud Infrastructure](https://www.youtube.com/watch?v=SLB_c_ayRMo&t=5847s)


