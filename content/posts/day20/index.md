---
title: "2 July 2021"
date: 2020-06-08T08:06:25+06:00
description: Introduction to Sample Post
menu:
  sidebar:
    name: Introduction
    identifier: introduction
    weight: 10
---

- Started working around with Kubernetes.

  - Made a directory `kubernetesinstallation` for storing private keys.
  
  - Created a VM to be used as a Master Node for my Kubernetes installation process.
    ```
    aws ec2 run-instances --image-id ami-0c1a7f89451184c8b --count 1 --key-name masternodessh --instance-type t2.micro
    
    ```
    {{<asciinema TBAH4doSotdyhEBFSANzBPLvi>}}
    
- First attempt to connect to my Master Node using SSH. 
  
  - Attempted connecting to my Master Node VM via SSH client but failed to do so, since my connection timed out.
    ```
    ssh -i masternodessh.pem ubuntu@ec2-13-234-225-150.ap-south-1.compute.amazonaws.com
    
    ```
  - To make sure that my private key is not publicly visible, used the following command. Also, the private key file can be downloaded just once and make sure that its in the same directory as your
    working directory.
    ```
    chmod 400 masternodessh.pem
    
    ```
    {{<asciinema yQUixrAIOoGu3Nf8yjlUQ1lSe>}}
    
  - Tried connecting using Ec2 Instance Connect but failed.
  
- Second attempt to connect to my Master Node using SSH.

  - Terminated the previous instance and created a new one with subnet and security group.
    ```
    aws ec2 run-instances --image-id ami-0c1a7f89451184c8b --count 1 --key-name masternodessh --instance-type t2.micro --security-group-ids  --subnet-id subnet-0d373cd18c07e0145
    
    ```
    {{<asciinema qvkGqhecwLzaxOz7akOraX1s2>}}
    
  - Failed to connect via SSH. Later realised that my instance was linked to a private subnet and hence, I didn't get a public DNS.
    ```
    ssh -i "masternodessh.pem" ubuntu@10.0.1.84
    
    ```
    {{<asciinema ya23FcocfqeeplwOWeWatdiJi>}}
    
- Third attempt to connect to my Master Node using SSH.

  - Attached an internet Gateway.
    ```
    aws ec2 attach-internet-gateway --internet-gateway-id igw-014783f25b2794337 --vpc-id vpc-0e595b592d80b7cf4
    
    ```
  - Enabled DNS hostnames in VPC settings and 'auto-assign IPV4 address' in the Subnet settings to 'yes'.
  
  - Terminated the previous instance and created a new one with same subnet and security group.
    {{<asciinema lS26m0pGw27oVeLmjGhObPPKF>}}
    
  - Failed again, despite managing to get a public DNS.
    {{<asciinema HfG8cOfYQr1oosPfgZ5J9sdMN>}}
    
- References:
  
  - [Possible reasons for not getting a public DNS for SSH client](https://stackoverflow.com/questions/20941704/ec2-instance-has-no-public-dns)
  - [SSH to EC2 Instances using Linux or Mac Tutorial](https://www.youtube.com/watch?v=8UqtMcX_kg0)
  
  

    


    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    





