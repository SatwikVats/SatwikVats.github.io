---
title: "key-pair"
date: 2020-06-08T06:00:20+06:00
menu:
  sidebar:
    name: key-pair
    identifier: k_p
    parent: aws_cli
    weight: 3
---

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