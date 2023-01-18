---
title: "Day 9"
date: 2020-06-08T06:00:20+06:00
menu:
  sidebar:
    name: 17 June
    identifier: Daily Updates-day9
    parent: Daily Updates
    weight: 10
---


    
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



