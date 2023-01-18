---
title: "Working with Containers"
date: 2020-06-08T06:00:20+06:00
menu:
  sidebar:
    name: Working with Containers
    identifier: working_w_containers
    parent: abt_docker
    weight: 10
---

  - GroupAdded Docker and added a user to avoid usage of sudo everytime, using command **$sudo usermod -aG docker $USER**.
    {{<asciinema pzzcJ4ayAUglUXLOHFxFpKbQK>}}

  - Tried creating my first Docker container but failed, due to denial of some permissions.
    {{<asciinema UshelqIMVU9Wnu4FeHykHShiR>}}
  
  - Tried pulling Nginx image, but failed due to lack of storage. My Asciinema recording stopped abruptly due to the same.
    {{<asciinema uyUyl1VTwIHVl0asDS7U1Uj0X>}}

- Working with containers.

  - Successfully pulled Nginx Image.
  
  - Got to know how to check the status of containers whether they are active or running.
    **docker ps** command for the list of active running containers.
    **docker ps -a** command for the list of stopped containers.
    
  - Locally hosted the Nginx Image.
    ![Nginx image locally hosted.](/posts/Daily Updates/nginxtrialsitessday7.png)
  
  - Learnt how to remove a stopped container by using **docker rm <ContainerID>** command.
  
    {{<asciinema qy4mU0eJnRxHp1HaZmOUALSKB>}}