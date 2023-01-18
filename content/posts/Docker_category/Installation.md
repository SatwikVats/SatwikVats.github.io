---
title: "Introduction to Docker"
date: 2020-06-08T06:00:20+06:00
menu:
  sidebar:
    name: Introduction to Docker
    identifier: intro_docker
    parent: abt_docker
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