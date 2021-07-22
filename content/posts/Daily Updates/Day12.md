---
title: "Day 12"
date: 2020-06-08T06:00:20+06:00
menu:
  sidebar:
    name: 22 June
    identifier: Daily Updates-day12
    parent: Daily Updates
    weight: 10
---

- Created my first AWS server-
  - Launched an Ubuntu instance on AWS console. Selected t2.micro as instance type.
  - Referred the[doc](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/instance) and copied resources tag.
  - Fetched the AMI from Aws management console, for my instance and specified instance type in main.tf file.
  - Successfully deployed 1st ec-2 instance using terraform.
  - `resource "aws_instance" "my-first-server" {
     ami = "ami-0c1a7f89451184c8b"
     instance_type = "t2.micro" 
     }` 
    {{<asciinema Lc0S6hCFOA3rbMJAhzRxTjrsu>}}

- Through main.tf file, we are indicating terraform what our code should look like in the end. If we use `terraform apply` again, it will not re-run the code.
  {{<asciinema DpXvyBLKhVmSmkMKKQB3jgnDE>}}

- In similar way, we can either destroy a server either by using `terraform destroy`, or by making necessary changes to the main.tf file, followed by `terraform apply`.

- Made a change in the file by adding a tag.
  - Added a name tag to the instance.
  - `tags = {
     Name = "Ubuntu"
     }`
  {{<asciinema udoq9ktPbnI6M6J730PCl0czB>}}
 
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
  
- `terraform apply --auto-approve` skips the task of responding `yes`, which recurrs while executing `terraform apply`.

- Discovered that two new files, `terraform.tfstate` and `terraform.tfstate.backup` are created on initializing terraform in a directory.
  {{<asciinema kiWSf61ZVE1hmjY0FucJt1lqI>}}
  
- References
  * [Automate your AWS Cloud Infrastructure using Terraform, right from scratch](https://www.youtube.com/watch?v=SLB_c_ayRMo)


