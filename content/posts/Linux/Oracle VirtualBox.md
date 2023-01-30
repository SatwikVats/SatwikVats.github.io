---
title: Oracle Virtualbox
menu:
  sidebar:
    name: Oracle Virtualbox
    identifier: oracle_virtualbox
    parent: linux
    weight: 300
---

- Installed VS code for my Linux VM.

  - Downloaded the .deb file from [Visual Studio official site](https://code.visualstudio.com/).
  
  - Installed it by running `sudo dpkg -i code_1.57.0-1623259737_amd64.deb` on terminal.
  {{<asciinema BHiOiWpjaAdpczDONNkNgPhx2>}}
  
  - The VS application can be opened from terminal by using `open code .`

- Since the past few days, I have been trying to figure out how to enable full-screen display for my VM.
  * After several futile attempts of installing new ISOGuestAdditions and changing disc image, found a different method in a [Youtube guide](https://www.youtube.com/watch?v=FtGvtgnLiE8).
  * In the virtualBox Manager, altered a few settings. Increased Video memory and changed Graphics Controller to VBoxSVGA.
  * Restarted the machine and got desired results.

- Follow-up process in an attempt to deploy full-screen through GuestAdditionsISO.

    [![asciicast](https://asciinema.org/a/23ndBE4SnRKdDuPdqr8AwAxOi.svg)](https://asciinema.org/a/23ndBE4SnRKdDuPdqr8AwAxOi)

- Dynamically Increasing Storage:
    Increased my storage by referring a [YT tutorial](https://www.youtube.com/watch?v=jpMaTnnmcyI). I had opted for dynamic storage space while setting up the VM, hence the process was relatively     easier for me.
  