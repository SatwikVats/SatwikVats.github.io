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
    [![asciicast](https://asciinema.org/a/pzzcJ4ayAUglUXLOHFxFpKbQK.svg)](https://asciinema.org/a/pzzcJ4ayAUglUXLOHFxFpKbQK)

  - Tried creating my first Docker container but failed, due to denial of some permissions.
    [![asciicast](https://asciinema.org/a/UshelqIMVU9Wnu4FeHykHShiR.svg)](https://asciinema.org/a/UshelqIMVU9Wnu4FeHykHShiR)
  
  - Tried pulling Nginx image, but failed due to lack of storage. My Asciinema recording stopped abruptly due to the same.
    [![asciicast](https://asciinema.org/a/uyUyl1VTwIHVl0asDS7U1Uj0X.svg)](https://asciinema.org/a/uyUyl1VTwIHVl0asDS7U1Uj0X)

- Working with containers.

  - Successfully pulled Nginx Image.
  
  - Got to know how to check the status of containers whether they are active or running.
    **docker ps** command for the list of active running containers.
    **docker ps -a** command for the list of stopped containers.
    
  - Locally hosted the Nginx Image.
    ![Nginx image locally hosted.](/posts/Daily Updates/nginxtrialsitessday7.png)
  
  - Learnt how to remove a stopped container by using **docker rm <ContainerID>** command.
  
    [![asciicast](https://asciinema.org/a/qy4mU0eJnRxHp1HaZmOUALSKB.svg)](https://asciinema.org/a/qy4mU0eJnRxHp1HaZmOUALSKB)