---
title: "Docker"
date: 2020-06-08T08:06:25+06:00
description: Introduction to Sample Post
menu:
  sidebar:
    name: Docker
    identifier: Docker
    weight: 10
---

# Docker

- Installed Docker package and engine on my system. Followed the official [Docker documentation](https://docs.docker.com/engine/install/ubuntu/#install-from-a-package) and a [Youtube Tutorial](https://www.youtube.com/watch?v=kkazBPHc4bk)
  
  - Firstly, attempted installing it through the repository method.
    * Made sure if there were any previously installed versions, got removed.
    * Got updates.
    * Installed the package.
    * Added Docker's official GPG key.
    * Faced issues while installing the Docker engine.
    
    [![asciicast](https://asciinema.org/a/Ok4K53fq62IgX0AtMhaGdIi6e.svg)](https://asciinema.org/a/Ok4K53fq62IgX0AtMhaGdIi6e)
        
  - Second attempt to manually import Docker package and install it.
    * Checked Ubuntu version to find a corresponding Docker package from the given [link](https://download.docker.com/linux/ubuntu/dists/focal/pool/stable/amd64/) and downloaded it.
    * In this process, an error incurred while specifying the path of .deb file.
    
    [![asciicast](https://asciinema.org/a/vVCUkTw5A4sjRH3ZtGfcJQdhL.svg)](https://asciinema.org/a/vVCUkTw5A4sjRH3ZtGfcJQdhL)
    [![asciicast](https://asciinema.org/a/0vXWajk8VrZBPZAaZMscWSpz2.svg)](https://asciinema.org/a/0vXWajk8VrZBPZAaZMscWSpz2)
    
    * Imported a missing Docker package, thus rectifying my previous mistake.
    * Checked version.
    * Made sure its working fine, by running a test image.
    * Managed to successfully complete installation part.
    
    [![asciicast](https://asciinema.org/a/iIvMGkEjtXWVgAuYu3urg4DtG.svg)](https://asciinema.org/a/iIvMGkEjtXWVgAuYu3urg4DtG)
    
  - Checked whether Docker is actively running or not. Even tried running a test image.
    [![asciicast](https://asciinema.org/a/5hufWQD6JLMrDivOjga5GALrQ.svg)](https://asciinema.org/a/5hufWQD6JLMrDivOjga5GALrQ)
  
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

- Attempted locally hosting the docker image.

  - Created **index.md** and **about.md** files in a repository.
  
  - Used command `docker run -d -p 8000:80 -v ~/nginxtrial:/usr/share/nginx/md --name trialsite nginx` to run it. **trialsite** is the name of the image here.
  {{<asciinema 4pyCCIfWy0E8boWjQhuVZ7oMe>}}
  
  - But when launched the docker container on port 8000, it displayed error 404:Not found.
  
  - Repeated the same process, but with **index.html** and **about.html** files this time around and got the desired results.
  {{<asciinema uZD87ZEDJXD8dQUKDWgmIjgbd>}}
  
  -Tried tampering the **about.html** file and the changes were reflected on the server accordingly, on refreshing.
  {{<asciinema 0ulPOVB0dSxqWewn5ypQFWbBt>}}

- Making a Docker container for Hugo site by following a [Youtube tutorial](https://www.youtube.com/watch?v=kkazBPHc4bk&t=198s).

  - Made two directories namely `ansible-build` and `docker-build` in the Hugo repository. Shifted content of Hugo website to Docker-build.
  
  - Made a Dockerfile. Specified Nginx static file location and localhost ports in the file.
  
  - Built the Docker container and ran it. Failed in the earlier attempt since I forgot to make Dockerfile.
    * `docker build docker-build -t nginx-docker-build-demo`:Sends build context to Docker Daemon.
    * `docker run -it --rm -d -p 8000:80 --name web-server-docker nginx-docker-build-demo`:Runs the Docker on web-server.
    {{<asciinema sQzHGL7umB6JpnjzsbWIyP1ez>}}
    
  - The site showed default Nginx. Added just the public repository contents of Hugo site to the Docker-build and removed previous content to fix that issue.
    {{<asciinema O9dzIKFXv7YBRQpVGkubtEt3k>}}
  
  - Locally hosted Hugo site to croos-verify how site should look, since my Hugo theme was not rendered while running Docker container.
    {{<asciinema sdle0vIj2PgxSEM9eUIITa7Ah>}}
    
    Expected outcome
    ![Expected outcome](/posts/Daily Updates/desiredsiteday9.PNG)
    
    Actual outcome
    ![Actual outcome](/posts/Daily Updates/siteobtainedday9.PNG)

- References-
  * [Understanding Dockers and Containers](https://www.youtube.com/watch?v=JSLpG_spOBM)
  * [Nginx Images](https://hub.docker.com/_/nginx)

# Test post
