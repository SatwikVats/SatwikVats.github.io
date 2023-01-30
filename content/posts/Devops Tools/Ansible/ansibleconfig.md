---
title: Ansible Config
menu:
  sidebar:
    name: Ansible Config
    identifier: ansible_config
    parent: ansible
    weight: 300
---


- Installed necessary Ansible package on my system, follwed by Python which is necessary for running Ansible.
[![asciicast](https://asciinema.org/a/3Usqq3IbjQ4TWelFzGShOoIZJ.svg)](https://asciinema.org/a/3Usqq3IbjQ4TWelFzGShOoIZJ)

- Working around with Ansible.

  - Checked Ansible version.
  {{<asciinema usXyeJGiUNea0Td0IrCq8yhmJ>}}
  
  - Install the net-tools package, which is necessary to run `ifcongig` command.
  
  - Ran the `ifcongig` command to fetch the host IP address. The IP address was present in the log under the section **enp0s3:inet**.
  
  - Made a directory **ansibleinventory** to store the inventory file **myhosts.txt**. Again, had to install the **vim** package before proceeding.
  {{<asciinema TD0Ng5gy9l3omaHkATyYCWdxW>}}
  
  - Had to recap certain aspects of Vi editor such as enterin insert mode, saving and quitting the editor mode by referring to the [article](https://www.guru99.com/the-vi-editor.html).
  
  - Added host IP along with authorization key and password in the inventory file.
  `10.0.2.15 ansible_ssh_user=root ansible_ssh_pass=..........`
  
- Creating a configuration file for Ansible.

  - Created a ansible.cfg file in the ```/home/satwik/ansibleinventory/ansible``` directory.
  
  - Specified the path of inventory file in the **ansible.cfg**.
  
  - Listed the hosts using `ansible all --list-hosts` command and my host was visible.
  {{<asciinema xPS1EMk5zFhr40oi2N3GgpzJ9>}}
  
- Tried installing **epel** package which was necessary to configure SSH connection. 
  Used command `yum install https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm`.
  Since **yum** command was not available, failed at doing so.
  {{<asciinema fRciWUfrxdYU6S3G2KdhCx40G>}}

- Running Ansible tasks.

  - Made an Ansible Playbook inside the `ansible-build` directory and specified the tasks sequentially there. The required syntax for .yaml playbooks is as follows.
    `name:
     hosts:
     tasks:`
    {{<asciinema eN5RfLSzCWakcOfduYB75OGh5>}}
  
  - Ran the playbook using command `ansible-playbook docker-image-playbook.yaml`. Tasks getting executed can be seen here.
  
  - Ran the site locally but again, the theme was not getting rendered.
    {{<asciinema PfnhlLwFxu5yZqKGjiF1RYkrf>}}

- References-
  * [A comprehensive guide to Docker and Ansible hosting process](https://www.youtube.com/watch?v=kkazBPHc4bk&t=198s)