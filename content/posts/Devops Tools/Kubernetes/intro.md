---
title: "Knets_content"
date: 2020-06-08T06:00:20+06:00
menu:
  sidebar:
    name: Knets_content
    identifier: knets_content
    parent: kubernetes
    weight: 2
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

- Attempted deploying Kubernetes cluster by following this [tutorial](https://www.youtube.com/watch?v=vpEDUmt_WKA).

  - Created three VMs to be used as nodes- One Matser, Two Slaves.
  
  - Started off by installing packages on the Master Node.
    
    - Installed Docker. Referred to [official documentation](https://docs.docker.com/engine/install/ubuntu/) for the same.
      ```
      #Importing some necessary certificates.
      sudo apt-get install \ 
      >     apt-transport-https \ 
      >     ca-certificates \ 
      >     curl \ 
      >     gnupg \ 
      >     lsb-release
      
      sudo apt  install docker.io  # version 20.10.2-0ubu
      
      docker --version
      
      ```
    - Imported a gtg key.
      ```
      sudo apt-get install -y apt-transport-https ca-certificates curl
      sudo curl -fsSLo /usr/share/keyrings/kubernetes-archive-keyring.gpg https://packages.cloud.google.com/apt/doc/apt-key.gpg
      echo "deb [signed-by=/usr/share/keyrings/kubernetes-archive-keyring.gpg] https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee/etc/apt/sources.list.d/kubernetes.list
      
      ```
    - Installed kubelet, kubeadm and kubectl.
      ```
      sudo apt-get install -y kubelet kubeadm kubectl
      sudo apt-mark hold kubelet kubeadm kubectl
      
      ```
    - Enabled the use of IP-tables.
      ```
      echo "net.bridge.bridge-nf-call-iptables=1" | sudo tee -a /etc/sysctl.conf 
      sudo sysctl -p
      
      ```
      {{<asciinema VXnh3KJmjMsIAlnkrp3Cx80XB>}}
      
  - Repeated the same process for Worker Nodes one and two.
    {{<asciinema aw3qRrxiRGhWODfrDoIf4eAkK>}}
    
  - Since the nodes were ready with all the required packages, attempted to initialize the cluster.
  
  - Failed since the RAM of Master node was less than the required 1700 MB.
    ```
    sudo kubeadm init --pod-network-cidr=10.244.0.0/16
    
    ```
    {{<asciinema 0dntls4e0TOs8mWyouz39LAcW>}}
    
  - Teminated the Master Node with instance-type `t2.micro` and created a new one with type as `t2.medium`.
  
  - Repeated the process all over for the VM with improved RAM.
    {{<asciinema RQNLMi8iHVYwf4nG9MLx8rOB3>}}
    
  - Successfully initialized cluster in the Master Node this time.
    ```
    #Initializing the cluster.
    sudo kubeadm init --pod-network-cidr=10.244.0.0/16
    
    mkdir -p $HOME/.kube
    sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
    sudo chown $(id -u):$(id -g) $HOME/.kube/config
    
    #Created a security policy for pods.
    kubectl apply -f https://raw.githubusercontent.com/coreos/flannel/master/Documentation/kube-flannel.yml
    
    ```
  - Nodes can be viewed using th following command.
    ```
    kubectl get nodes
    
    #Watch allows you to automatically repeat a command. It keeps refreshing the node-list every 2 secs.
    watch kubectl get nodes
    
    ```
    {{<asciinema 0HuQ5afgqCQWsznuaTZkZJZfk>}}
    
  - Tried attaching Worker Node 1 to cluster, but failed.
    ```
    sudo kubeadm join 172.31.37.108:6443 --token y5zv1x.8sr3g843mgi3gj72 \ 
    > --discovery-token-ca-cert-hash sha256:b789f80fbcd5b2c6b6b6f795e648ec3b27aa1052652edfc712dbaecf6070050e 
    
    ```
    {{<asciinema RDDR2gWYaPalwFjHMERWeO1g8>}}
  
  - Tried the same for Worker Node 2, but a different error showed up this time.
    {{<asciinema dDmP5cY12UQLzCMvZ8OqJ97lc>}}

- Spent some time in debugging previous day's error.

- Deep-dived into some of the fundamental aspects of cloud computing such as VM, subnets, VPCs and Security Groups. 

- Started learning about EKS Cluster and its deployment method.

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

- References-
  
  * [Kubernetes for beginners](https://www.youtube.com/watch?v=l_lWfipUimk)
  * [Kubernetes setup](https://www.youtube.com/watch?v=ndNKI5GBdd0)
  * [Deploy Kubernetes from scratch](https://www.youtube.com/watch?v=vpEDUmt_WKA)
  * [Provisioning an EKS Cluster](https://learn.hashicorp.com/tutorials/terraform/eks)
  * [Creating an EKS Cluster](https://www.youtube.com/watch?v=p6xDCz00TxU)
  * [Basics of Cloud Computing](https://www.youtube.com/watch?v=dH0yz-Osy54)
  * [Provisioning an EKS Cluster](https://learn.hashicorp.com/tutorials/terraform/eks)  
  * [Possible reasons for not getting a public DNS for SSH client](https://stackoverflow.com/questions/20941704/ec2-instance-has-no-public-dns)
  * [SSH to EC2 Instances using Linux or Mac Tutorial](https://www.youtube.com/watch?v=8UqtMcX_kg0)