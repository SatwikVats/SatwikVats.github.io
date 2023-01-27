---
title: "Kubernetes"
date: 2020-06-08T08:06:25+06:00
description: Introduction to Sample Post
menu:
  sidebar:
    name: Kubernetes
    identifier: kubernetes
    parent: devops
    weight: 10
---

# Kubernetes

- Spent some time on learning about Kubernetes.
  
  - Its utility as a Container Management Tool.
  - Procedure of installation via three nodes- one master along with two slave nodes.

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
  
  - [Possible reasons for not getting a public DNS for SSH client](https://stackoverflow.com/questions/20941704/ec2-instance-has-no-public-dns)
  - [SSH to EC2 Instances using Linux or Mac Tutorial](https://www.youtube.com/watch?v=8UqtMcX_kg0)

# Test post
