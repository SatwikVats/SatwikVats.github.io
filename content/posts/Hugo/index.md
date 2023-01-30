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

Wanna launch your own website, but you aren't acquainted with HTML/CSS/React.js/Node.js? You don't wanna take an easy route via Wordpress either! Don't worry, Hugo has got you covered. It's a widely used framework for building static sites and personal blogs, which has a vast set of catchy templates already available on its site and an individual can make his/her site on similar lines. Elaborate documentation guides the user to make use of the theme in a better way. CI/CD tools like [GitHub Actions](https://github.com/marketplace/actions/deploy-to-github-pages) and [CircleCI](https://circleci.com/blog/automate-your-static-site-deployment-with-circleci/) further make it easy for the user to continuously push changes into the repository and update the site without deploying it again and again.

## Installing Hugo on Linux.

## Basic Hugo Commands.

```
#Creating a new site in a directory of name 'Sitename'
hugo new site <Sitename>

#Creating a new post
hugo new <Path of the new file>

#Tracking the status of hugo site
hugo

hugo new server

hugo server

hugo server -d

hugo server -w

#Building the site
hugo build

```

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

- Modifying content and adding a 'Recent Posts' section.

{{<asciinema 8fz6ypSTsmjIl5ytvbKNyFR5D>}}


## Hosting the Site locally.

{{<asciinema 418763>}}

