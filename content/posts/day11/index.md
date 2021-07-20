---
title: "21 June 2021"
date: 2020-06-08T08:06:25+06:00
description: Introduction to Sample Post
menu:
  sidebar:
    name: Introduction
    identifier: introduction
    weight: 10
---

- Installed Terraform on terminal, following the steps in the given doc-
  [Step-by-step guide on Terraform installation](https://learn.hashicorp.com/tutorials/terraform/install-cli?in=terraform/aws-get-started)
  {{<asciinema EQbv1VTWDamOOS6IhWEvcyf2y>}}
  
- Made a Docker container out of Terraform and locally hosted the Nginx image.
  - Created a new directory.
  - Initialized Terraform in it by using `terraform init` command.
  - Created main.tf file. Specified resources and providers there.
  - Finally ran the image on LocalHost:8000
    ![Nginx Image hosted using Terraform](/posts/day11/nginxsiteterraform.PNG)
  - Learnt some of the basic Terraform commands like `plan`, `apply` , `destroy` along the way.
    - `plan` does a dry run of your configuration and tell you what all chanes would be applied once you use `terraform apply`.
    - `apply` deploys the changes according to final state of main.tf file, compared to earlier changes. 
    - `destroy` destroys the whole infrastructure created till the point.
    - Got a basic understanding of how declarative mode of programming works.
   {{<asciinema GYxglIjUsJDgQxNLfIZqNXxp0>}}

- Installed Terraform extension on my Visual Studio code as well.

- Made an AWS account alongside exploring AWSEducate portal.
  [AWS Educate](https://aws.amazon.com/education/awseducate/)

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

- References:
  * [Understanding declarative and imperative programming](https://www.youtube.com/watch?v=6RAQynw2Sy8)
  * [Automate your AWS Cloud Infrastructure using Terraform, right from scratch](https://www.youtube.com/watch?v=SLB_c_ayRMo)





