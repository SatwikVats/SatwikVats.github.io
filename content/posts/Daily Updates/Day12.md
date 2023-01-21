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


  
- `terraform apply --auto-approve` skips the task of responding `yes`, which recurrs while executing `terraform apply`.

- Discovered that two new files, `terraform.tfstate` and `terraform.tfstate.backup` are created on initializing terraform in a directory.
  {{<asciinema kiWSf61ZVE1hmjY0FucJt1lqI>}}
  
- References
  * [Automate your AWS Cloud Infrastructure using Terraform, right from scratch](https://www.youtube.com/watch?v=SLB_c_ayRMo)


