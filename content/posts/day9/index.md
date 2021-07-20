---
title: "17 June 2021"
date: 2020-06-08T08:06:25+06:00
description: Introduction to Sample Post
menu:
  sidebar:
    name: Introduction
    identifier: introduction
    weight: 10
---

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
    ![Expected outcome](/posts/day9/desiredsite.PNG)
    
    Actual outcome
    ![Actual outcome](/posts/day9/siteobtained.PNG)
    
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



