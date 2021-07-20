---
title: "6 July 2021"
date: 2020-06-08T08:06:25+06:00
description: Introduction to Sample Post
menu:
  sidebar:
    name: Introduction
    identifier: introduction
    weight: 10
---

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
    
- References

  - [Deploy Kubernetes from scratch](https://www.youtube.com/watch?v=vpEDUmt_WKA)


