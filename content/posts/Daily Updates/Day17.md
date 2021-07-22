---
title: "Day 17"
date: 2020-06-08T06:00:20+06:00
menu:
  sidebar:
    name: 29 June
    identifier: Daily Updates-day16
    parent: Daily Updates
    weight: 10
---

- Continuation of previous day's project on making a webserver-
  
  - Passed on some user data in the file.
    ```
    #Passing on user data to run some commands.
    user_data = <<-EOF
                #!/bin/bash
                
                sudo apt update -y
                sudo apt install apache2 -y
                sudo systemct1 start apache2
                sudo bash -c 'echo my first web-server > /var/www/html/index.html'
                EOF
                
    tags = {
    Name = "web-server"
    }
    
    ```
  - Found out that there were errors in defining cidr_blocks IP addresses.
    {{<asciinema VjryZ9jYicarZ9N3l4Yxa7idp>}}
    
  - Applied the terraform after rectifying few syntactical errors. Still, there were some issues in cofiguring routes.
    {{<asciinema 82L56hs3NOLT8HxSjjytkuucb>}}
     
  - Destroyed the whole AWS Web-server infrastructure by erasing all resources from main.tf file.
    {{<asciinema KhJNFz7cb86rqG8UXZ7jSqaRI>}}
    
- Creating first key-pair using AWS CLI.

  - Used the command :
    ```
    aws ec2 create-key-pair --key-name FirstKeyPair --query 'KeyMaterial' --output text > FirstKeyPair.pem
    
    ```
    Here, we can modify the arguments including key-pair names according to our needs.
    
  - To check whether key-pair has been made correctly, we can either visit the console manually or use a command.
    ```
    aws ec2 describe-key-pairs
    
    ```
    This command lists down all the key-pairs created by the user.
    {{<asciinema pcBZX99KrIGevMYQuGNOy4IyY>}}

  - Was unable to use the previous command at first go due to output error. Hence changed the output type to `json` in configuration. It worked fine, thereafter.
    {{<asciinema p4VET2UcRJV7BDxQ4m9s0LLV7>}}
  
- Deployed an Ec2 instance using CLI.

  - Command used :
    ```
    aws ec2 run-instances --image-id ami-0c1a7f89451184c8b --count 1 --instance-type t2.micro --key-name FirstKeyPair
    
    ```
    Arguments such as ami, instance type and key name should be varied according to our needs and resources available.
    
  - In my case, I have used ami for Ubuntu server and key-pair which I had created earlier.
    
  - All the VM specifications get displayed in the JSON format once the VM is deployed.
    {{<asciinema x4Knr2GzaBvBbpPzdEEwMNE6v>}}
    
- References :
  - [AWS Command Line Interface official documentation](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-welcome.html)
  - [AWS CLI for beginners](https://www.youtube.com/watch?v=PWAnY-w1SGQ&t=1055s)
  
    

