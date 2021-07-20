---
title: "15 June 2021"
date: 2020-06-08T08:06:25+06:00
description: Introduction to Sample Post
menu:
  sidebar:
    name: Introduction
    identifier: introduction
    weight: 10
---

- Created a Hugo group site.
  
  - Initialized an empty Hugo site and remotely added it to Github Repository.
  [![asciicast](https://asciinema.org/a/9xVaI78ItMng5RLAVxWC4YPIK.svg)](https://asciinema.org/a/9xVaI78ItMng5RLAVxWC4YPIK)
  
  - Added my group members as collaborators on the repository containing this Hugo Site.
  
  - Added an appropriate theme to the site.
  [![asciicast](https://asciinema.org/a/lzTv87ZZK3lBiXLmf2Y9fb5og.svg)](https://asciinema.org/a/lzTv87ZZK3lBiXLmf2Y9fb5og)
  
  - Setup the homepage with some relevant content and added a bolg.
  [![asciicast](https://asciinema.org/a/P5ojQAdJKfVwp0AUd07C6Stgs.svg)](https://asciinema.org/a/P5ojQAdJKfVwp0AUd07C6Stgs)
  
  - Hosted the site locally, even though there were kinks.
  
- Checked whether Docker is actively running or not. Even tried running a test image.
[![asciicast](https://asciinema.org/a/5hufWQD6JLMrDivOjga5GALrQ.svg)](https://asciinema.org/a/5hufWQD6JLMrDivOjga5GALrQ)
  
- GroupAdded Docker and added a user to avoid usage of sudo everytime, using command **$sudo usermod -aG docker $USER**.
[![asciicast](https://asciinema.org/a/pzzcJ4ayAUglUXLOHFxFpKbQK.svg)](https://asciinema.org/a/pzzcJ4ayAUglUXLOHFxFpKbQK)

- Installed necessary Ansible package on my system, follwed by Python which is necessary for running Ansible.
[![asciicast](https://asciinema.org/a/3Usqq3IbjQ4TWelFzGShOoIZJ.svg)](https://asciinema.org/a/3Usqq3IbjQ4TWelFzGShOoIZJ)

- Tried creating my first Docker container but failed, due to denial of some permissions.
[![asciicast](https://asciinema.org/a/UshelqIMVU9Wnu4FeHykHShiR.svg)](https://asciinema.org/a/UshelqIMVU9Wnu4FeHykHShiR)
  
- Tried pulling Nginx image, but failed due to lack of storage. My Asciinema recording stopped abruptly due to the same.
[![asciicast](https://asciinema.org/a/uyUyl1VTwIHVl0asDS7U1Uj0X.svg)](https://asciinema.org/a/uyUyl1VTwIHVl0asDS7U1Uj0X)
  
- Increased my storage by referring a [YT tutorial](https://www.youtube.com/watch?v=jpMaTnnmcyI). I had opted for dynamic storage space while setting up the VM, hence the process was relatively     easier for me.
  
- Working with containers.

  - Successfully pulled Nginx Image.
  
  - Got to know how to check the status of containers whether they are active or running.
    **docker ps** command for the list of active running containers.
    **docker ps -a** command for the list of stopped containers.
    
  - Locally hosted the Nginx Image.
  ![Nginx image locally hosted.](/posts/day7/nginxtrialsitess.png)
  
  - Learnt how to remove a stopped container by using **docker rm <ContainerID>** command.
  
  [![asciicast](https://asciinema.org/a/qy4mU0eJnRxHp1HaZmOUALSKB.svg)](https://asciinema.org/a/qy4mU0eJnRxHp1HaZmOUALSKB)


    
- References-
  * [Understanding Dockers and Containers](https://www.youtube.com/watch?v=JSLpG_spOBM)
  * [Nginx Images](https://hub.docker.com/_/nginx)
  * [Ansible playbooks](https://www.youtube.com/watch?v=1id6ERvfozo)
    
