---
title: "Hosting Nginx Image"
date: 2020-06-08T06:00:20+06:00
menu:
  sidebar:
    name: Hosting Nginx Image
    identifier: hosting_nginx
    parent: abt_docker
    weight: 3
---

- Attempted locally hosting the docker image.

  - Created **index.md** and **about.md** files in a repository.
  
  - Used command `docker run -d -p 8000:80 -v ~/nginxtrial:/usr/share/nginx/md --name trialsite nginx` to run it. **trialsite** is the name of the image here.
  {{<asciinema 4pyCCIfWy0E8boWjQhuVZ7oMe>}}
  
  - But when launched the docker container on port 8000, it displayed error 404:Not found.
  
  - Repeated the same process, but with **index.html** and **about.html** files this time around and got the desired results.
  {{<asciinema uZD87ZEDJXD8dQUKDWgmIjgbd>}}
  
  -Tried tampering the **about.html** file and the changes were reflected on the server accordingly, on refreshing.
  {{<asciinema 0ulPOVB0dSxqWewn5ypQFWbBt>}}