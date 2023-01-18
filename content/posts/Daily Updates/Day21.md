---
title: "Day 21"
date: 2020-06-08T06:00:20+06:00
menu:
  sidebar:
    name: 5 July
    identifier: Daily Updates-day21
    parent: Daily Updates
    weight: 10
---

- Tried pinging the VM created.
  {{<asciinema JKThgzuwECCT8I43LJJajpOOU>}}
  
- Experimented around by creating instances with different subnets, security groups and VPCs linked. 
  
  - Discovered that security group must have an inbound SSH rule, which has port 22 as ingress.
  
  - Finally made a successful SSH connection.
    {{<asciinema ACr3ZW8Q8xU4MUt7VtQONu72H>}}
    

  
- References:
  
  - [Learning about Route 53](https://aws.amazon.com/route53/)
  - [Kubernetes setup](https://www.youtube.com/watch?v=ndNKI5GBdd0)
  - [Github Guide](https://github.com/ValaxyTech/DevOpsDemos/blob/master/Kubernetes/k8s-setup.md)


