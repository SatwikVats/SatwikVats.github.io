---
title: "VMs"
date: 2020-06-08T06:00:20+06:00
menu:
  sidebar:
    name: VMs
    identifier: vms
    parent: terraform
    weight: 2
---

- Tried building AWS Cloud Infrastructure using Terraform.
  - Created a new directory.
  - Initialize Terraform in it by using `terraform init` command.
  - Created main.tf file and specified provider and region. In this case, provider is `aws`, and the region is `ap-south-1`(Mumbai).
    - `provider "aws" { 
       region = "ap-south-1" 
       }`
    {{<asciinema kySBeoFxTnA8xrvXOTDpt0fl0>}}
  - Created security credentials(access key and secret key) on the AWS management console and fetched it for main.tf.
    {{<asciinema D2UDgjNPeDiAw7yxqBgAoXw9G>}}


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

- An attempt to deploy a VM as an IAM user.
  
  - Created a directory and initialized Terraform in it.
    {{<asciinema 45q0k5gvvUmmZrHv3ccpPjxJZ>}}
  
  - Installed AWS CLI package whic is required for using `aws` commands.
  
  - Used `aws configure` to provide necessary fields like Access Key ID, Secret Access Key, Default Region and Default Output Format.
    {{<asciinema YrDwVH8WqTOOt5lLNx6tmSjxo>}}
    
  - Though, the since the credentials were revoked, it didn't work out.