---
title: "Day 24"
date: 2020-06-08T06:00:20+06:00
menu:
  sidebar:
    name: 8 July
    identifier: Daily Updates-day24
    parent: Daily Updates
    weight: 10
---

- Started working with EKS, following the official [Hashicorp documentation](https://learn.hashicorp.com/tutorials/terraform/eks)

  - Cloned the following directory.
    ```
    git clone https://github.com/hashicorp/learn-terraform-provision-eks-cluster
    
    ```
  - Configured AWS in the given directroy.
  
  - The directory has various terraform files.
    
    - `eks-cluster.tf`: It provisions all the resources required to setup EKS cluster.
    
    - `kubernetes-dashboard-admin.rbac.yaml`: It creates cluster binding and connects API.

    - `kubernetes.tf`: Provisions Kubernetes as a provider along with host and token.
    
    - `outputs.tf`: Defines output configuartion.
    
    - `README.md`: Default Readme file.
    
    - `security-groups.tf`: Provisions all the sercurity groups to be used by EKS cluster.
    
    - `versions.tf`: Sets the latest Terraform version.
    
    - `vpc.tf`: Provisions a VPC along with subnets and availability zones.
    
    {{<asciinema VrctJSMSRmJYDO7iqX3fhEWve>}}
  
  - Initialized Terraform of the latest version in the directory.
    ```
    terraform init -upgrade
    
    ```
  - Used `terraform plan` to analyze the cluster infrastructure changes.
    {{<asciinema VpTwxfmoChNVUfT8rNT9AGr91>}}
    
  - Attempted deploying the cluster using `terraform apply`, but failed since IAM permissions weren't granted.
    {{<asciinema LRMzaLh5jyfUIuepa0wFblC7j>}}
    
    
- References:
 
  - [Provisioning an EKS Cluster](https://learn.hashicorp.com/tutorials/terraform/eks) 

