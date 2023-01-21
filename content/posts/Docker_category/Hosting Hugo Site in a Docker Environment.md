---
title: "Hosting a Hugo Site in Docker Environment"
date: 2020-06-08T06:00:20+06:00
menu:
  sidebar:
    name: Hosting a Hugo Site in Docker Environment
    identifier: hugo_site_in_docker
    parent: abt_docker
    weight: 4
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
    ![Expected outcome](/posts/Daily Updates/desiredsiteday9.PNG)
    
    Actual outcome
    ![Actual outcome](/posts/Daily Updates/siteobtainedday9.PNG)