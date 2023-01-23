---
title: "Key-pair"
date: 2020-06-08T06:00:20+06:00
menu:
  sidebar:
    name: Key-pair
    identifier: k_p
    parent: aws_cli
    weight: 3
---

### Creating key-pair using AWS CLI.

  - ```
    #Here, we may modify the arguments including key-pair names.
    aws ec2 create-key-pair --key-name FirstKeyPair --query 'KeyMaterial' --output text > FirstKeyPair.pem
    
    ```
    
  - To check whether key-pair has been made correctly, we can either visit the console manually or use the following command.
    ```
    aws ec2 describe-key-pairs
    
    ```
### Listing down all the key-pairs created by user.

  - This generates all the key-pairs.
    {{<asciinema pcBZX99KrIGevMYQuGNOy4IyY>}}

  - Troubleshooting : If you are unable to generate list of Key-pairs due to output error, try changing the output type to `json` in configuration.
    {{<asciinema p4VET2UcRJV7BDxQ4m9s0LLV7>}}