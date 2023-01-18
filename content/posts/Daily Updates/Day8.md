---
title: "Day 8"
date: 2020-06-08T06:00:20+06:00
menu:
  sidebar:
    name: 16 June
    identifier: Daily Updates-day8
    parent: Daily Updates
    weight: 10
---

- Installed VS code for my Linux VM.

  - Downloaded the .deb file from [Visual Studio official site](https://code.visualstudio.com/).
  
  - Installed it by running `sudo dpkg -i code_1.57.0-1623259737_amd64.deb` on terminal.
  {{<asciinema BHiOiWpjaAdpczDONNkNgPhx2>}}
  
  - The VS application can be opened from terminal by using `open code .`.
  

  
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
  
- Figured out how to embed Asciicast directly on my site by using my own shortcode.

  - Made a directory 'Shortcodes' under 'Layouts' section of my Hugo site.
  
  - Created a file **asciinema.html** in the same and wrote the shortcode there.
  `<script src="https://asciinema.org/a/{{.Get 0}}.js" id="asciicast-{{.Get 0}}" async></script>`
  
  - Now the asciicast could be directly embedded in Hugo site by writing `{{follow the syntax given below}}` in the markdown file.
  Suppose for **https://asciinema.org/a/I4VLffwlrXJH1r7iooQ4vzX5e** , the synatx would be `<asciinema I4VLffwlrXJH1r7iooQ4vzX5e>`.
  {{<asciinema I4VLffwlrXJH1r7iooQ4vzX5e>}}
  

- References-
  * [Running an Nginx container inside Docker](https://www.youtube.com/watch?v=mgwo8fq-SkA)
  * [How to avoid providing credentials for every Git Push](https://www.freecodecamp.org/news/how-to-fix-git-always-asking-for-user-credentials/)

