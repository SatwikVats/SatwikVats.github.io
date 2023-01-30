---
title: "Terraform Setup"
date: 2020-06-08T06:00:20+06:00
menu:
  sidebar:
    name: Terraform Setup
    identifier: terraform_setup
    parent: terraform
    weight: 2
---

- Installed Terraform on terminal, following the steps in the given doc-
  [Step-by-step guide on Terraform installation](https://learn.hashicorp.com/tutorials/terraform/install-cli?in=terraform/aws-get-started)
  {{<asciinema EQbv1VTWDamOOS6IhWEvcyf2y>}}
  
- Made a Docker container out of Terraform and locally hosted the Nginx image.
  - Created a new directory.
  - Initialized Terraform in it by using `terraform init` command.
  - Created main.tf file. Specified resources and providers there.
  - Finally ran the image on LocalHost:8000
    ![Nginx Image hosted using Terraform](/posts/Daily Updates/nginxsiteterraformday11.PNG)
  - Learnt some of the basic Terraform commands like `plan`, `apply` , `destroy` along the way.
    - `plan` does a dry run of your configuration and tell you what all chanes would be applied once you use `terraform apply`.
    - `apply` deploys the changes according to final state of main.tf file, compared to earlier changes. 
    - `destroy` destroys the whole infrastructure created till the point.
    - Got a basic understanding of how declarative mode of programming works.
   {{<asciinema GYxglIjUsJDgQxNLfIZqNXxp0>}}

- Installed Terraform extension on my Visual Studio code as well.

- `terraform apply --auto-approve` skips the task of responding `yes`, which recurrs while executing `terraform apply`.

- Discovered that two new files, `terraform.tfstate` and `terraform.tfstate.backup` are created on initializing terraform in a directory.
  {{<asciinema kiWSf61ZVE1hmjY0FucJt1lqI>}}



- References:
  * [Introduction to Terraform](https://www.youtube.com/watch?v=l5k1ai_GBDE)
  * [Understanding declarative and imperative programming](https://www.youtube.com/watch?v=6RAQynw2Sy8)
  * [Automate your AWS Cloud Infrastructure using Terraform, right from scratch](https://www.youtube.com/watch?v=SLB_c_ayRMo)
  * [Automating your AWS Cloud Infrastructure](https://www.youtube.com/watch?v=SLB_c_ayRMo&t=5847s)