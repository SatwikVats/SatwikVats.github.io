---
title: "Hugo"
date: 2020-06-08T08:06:25+06:00
description: Introduction to Sample Post
menu:
  sidebar:
    name: Hugo
    identifier: Hugo
    weight: 10
---

Wanna launch your own website, but you aren't acquainted with HTML/CSS/React.js/Node.js? You don't wanna take and easy route via Wordpress! Don't worry, Hugo has got you covered. It's a widely used framework for deploying a static site, where a set of themes are made availabe to the user for customization. Elaborate documentation guides the user to make use of the theme in a better way. CI/CD tools further make it easy for the user to continuously push changes into the repository and update the site without deploying it again and again.

## Installing Hugo on Linux.

## Basic Hugo Commands.

## Creating a new Hugo Site.

Follow these steps to create your own Hugo Site.

- Initializing a Hugo Site.

{{<asciinema 3hNwm6KZqV8Duqtli0i9HwHv9>}}

- Remotely adding to Github Repository.

{{<asciinema 9xVaI78ItMng5RLAVxWC4YPIK>}}

## Customizing your Hugo Site.

- Adding an appropriate theme to the site.

{{<asciinema lzTv87ZZK3lBiXLmf2Y9fb5og>}}

- Adding a post to the site.

{{<asciinema S7O4pFNNbILFpk9FPv4Asr3cp>}}
  
- Setiing up the homepage with some relevant content.

{{<asciinema P5ojQAdJKfVwp0AUd07C6Stgs>}}

## Hosting the Site locally.

{{<asciinema 418763>}}

- Working with VM.
 
  - Created a tag for VM.
    ```
    aws ec2 create-tags --resource i-08431b825258399a3 --tags Key=Name,Value=SkvInstance
    
    ```
