---
title: "Day 6"
date: 2020-06-08T06:00:20+06:00
menu:
  sidebar:
    name: Day 6
    identifier: Daily Updates-day6
    parent: Daily Updates
    weight: 10
---

- Tried exploring Docker and Ansible technologies.

- Had a healthy group discussion with my friends on the same, where we shared our ideas on both the technologies mentioned above.Many of our misconceptions were cleared up, and we divided responsibilities amongst us.

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
    
- Since the past few days, I have been trying to figure out how to enable full-screen display for my VM.
  * After several futile attempts of installing new ISOGuestAdditions and changing disc image, found a different method in a [Youtube guide](https://www.youtube.com/watch?v=FtGvtgnLiE8).
  * In the virtualBox Manager, altered a few settings. Increased Video memory and changed Graphics Controller to VBoxSVGA.
  * Restarted the machine and got desired results.

- Follow-up process in an attempt to deploy full-screen through GuestAdditionsISO.

    [![asciicast](https://asciinema.org/a/23ndBE4SnRKdDuPdqr8AwAxOi.svg)](https://asciinema.org/a/23ndBE4SnRKdDuPdqr8AwAxOi)
    
- References-
  * [Understanding Dockers and Containers](https://www.youtube.com/watch?v=JSLpG_spOBM)
  * [Nginx Images](https://hub.docker.com/_/nginx)
  

