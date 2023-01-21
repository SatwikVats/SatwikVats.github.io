---
title: "ec2"
date: 2020-06-08T06:00:20+06:00
menu:
  sidebar:
    name: ec2
    identifier: ec2
    parent: aws_cli
    weight: 1
---

- Deployed an Ec2 instance using CLI.

  - Command used :
    ```
    aws ec2 run-instances --image-id ami-0c1a7f89451184c8b --count 1 --instance-type t2.micro --key-name FirstKeyPair
    
    ```
    Arguments such as ami, instance type and key name should be varied according to our needs and resources available.
    
  - In my case, I have used ami for Ubuntu server and key-pair which I had created earlier.
    
  - All the VM specifications get displayed in the JSON format once the VM is deployed.
    {{<asciinema x4Knr2GzaBvBbpPzdEEwMNE6v>}}

- Working with VM.
 
  - Created a tag for VM.
    ```
    aws ec2 create-tags --resource i-08431b825258399a3 --tags Key=Name,Value=SkvInstance
    
    ```
  - Stopped the VM once I was done with my experimentation.
    ```
    aws ec2 stop-instances --instance-ids i-08431b825258399a3
    
    ```
    {{<asciinema VMQMuurIEmpWMjYilA6kZMgTZ>}}
    
  - Terminated an instance created previously.
    ```
    aws ec2 terminate-instances --instance-ids i-09165cb7fe11c4b0b
    
    ```
    {{<asciinema 9kjpixqG7CCenXz0HTBwQSlft>}}
