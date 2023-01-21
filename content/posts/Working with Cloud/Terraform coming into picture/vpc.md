---
title: "Vpc"
date: 2020-06-08T06:00:20+06:00
menu:
  sidebar:
    name: Vpc
    identifier: vpc
    parent: terraform
    weight: 2
---

- Created a VPC(Virtual Private Cloud) for my infrastructure. VPC is an isolated network in your AWS environment.
  - Copied the appropriate resources tags from [Terraform official documentation](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/subnet) into the main.tf file.
  - ID of subnet should be defined according to the name of corresponding vpc.
  - `resource "aws_vpc" "firstvpc" {
     cidr_block = "10.0.0.0/16"
     tags = {
     Name = "vpc1"
     }
     }`
  - `resource "aws_subnet" "subnet1" {
     vpc_id     = aws_vpc.firstvpc.id
     cidr_block = "10.0.1.0/24"
     tags = {
      Name = "Main"
       }
      }`
  {{<asciinema hNRdOFmSL3I3svBvfd1FqCJPj>}}