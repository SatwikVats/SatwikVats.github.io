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
    
- Attempted deploying Kubernetes cluster by following this [tutorial](https://www.youtube.com/watch?v=ndNKI5GBdd0).

  - Created a Master Node and established SSH connection.
    {{<asciinema 0YGqVFaWcGh5q2mth9Jc7QM86>}}
    
  - Installed AWS CLI and configured with my credentials.
  
  - To mask-off highly confidential credentials like secret access key on terminal, we may use the following commands.
    ```
    #Any user input provided on terminal is rendered invisible.
    stty -echo
    
    ```
    ```
    #To return back to normal mode.
    stty echo
    
    ```
    {{<asciinema PvjCw5Z1LeD9njd80xrgolOk4>}}
    
  - Installed all the necessary packages including kubectl.
    ```
    curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl
    chmod +x ./kubectl
    sudo mv ./kubectl /usr/local/bin/kubectl
    curl -LO https://github.com/kubernetes/kops/releases/download/$(curl -s https://api.github.com/repos/kubernetes/kops/releases/latest | grep tag_name | cut -d '"' -f 4)/kops-lin
    ux-amd64
    chmod +x kops-linux-amd64
    sudo mv kops-linux-amd64 /usr/local/bin/kops
    
    ```
  - Started exploring about Route 53 since it was required in this method.
    {{<asciinema WjzKnHwDTg7I7DOwhWaejHR7g>}}
    
  - Since I found a simpler approach, terminated this instance and started afresh.
  
- References:
  
  - [Learning about Route 53](https://aws.amazon.com/route53/)
  - [Kubernetes setup](https://www.youtube.com/watch?v=ndNKI5GBdd0)
  - [Github Guide](https://github.com/ValaxyTech/DevOpsDemos/blob/master/Kubernetes/k8s-setup.md)


