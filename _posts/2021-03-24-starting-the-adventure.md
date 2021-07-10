---
layout: post
read_time: true
show_date: true
title: "ASV 자율운항 보트 / Autonomous Surface Vehicle"
date: 2021-03-24
img: posts/20210324/usv-a1.jpg
tags: [general blogging, thoughts, life]
author: Armando Maynez
description: "무인 자율운항 보트/선박 ASV"
---

Funnily, this is not my first post. The birth of the blog came very natural as a way to "document" my newly established pursuit for getting myself into Machine Learning. This new adventure of mine comprises several things, and if I want to succeed I need to be serious about them all:
- Setting up a blog to document my journey and share it:
- Establish a learning and blogging routine.

As for the focus areas I will start with:
- Neural Networks fundamentals: history, basic architecture and math behind them
- Deep Neural Networks
  
I selected the above areas to focus on based on my personal interests, I have been fascinated by the developments in reinforcement learning for a long time, in particular [Deep Mind's](https://deepmind.com/blog) awesome [Go](https://deepmind.com/blog/article/innovations-alphago), [Chess](https://deepmind.com/blog/article/alphazero-shedding-new-light-grand-games-chess-shogi-and-go) and [Starcraft](https://deepmind.com/blog/article/AlphaStar-Grandmaster-level-in-StarCraft-II-using-multi-agent-reinforcement-learning) playing agents. Therefore, I started reading a lot about it and even started a personal project for coding a [tic-tac-toe learning agent](./deep-q-learning-tic-tac-toe.html).

As for practical work I decided to start by [coding my first models from scratch](./ML-Library-from-scratch.html) (without using libraries such as Tensorflow), to be able to deeply understand the math and logic behind the models, so far it has proven to be priceless.

For my next project I think I will start to do the basic hand-written digits recognition, which is the Machine Learning Hello World, for this I think I will start to use Tensorflow already.

Thanks for reading!

### P.S. For the geeks like me, here is a snippet on the technical side of the blog.

#### Static Website Generator
I researched a lot on this, when I started I didn't even know I needed a static website generator. I was just sure of one thing, I wanted my blog site to look modern, be easy to update and not to have anything extra or additional content or functionality I did not need.

There is a myriad of website generators nowadays, after a lengthy search the ones I ended up considering are:
- [wordpress](https://wordpress.com/)
- [wix](https://www.wix.com/)
- [squarespace](https://www.squarespace.com/)
- [ghost](https://ghost.org/)
- [webflow](https:webflow.com)
- [netlify](https://www.netlify.com/)
- [hugo](https://gohugo.io/)
- [gatsby](https://www.gatsbyjs.com/docs/glossary/static-site-generator/)
- [jekyll](https://jekyllrb.com/)

I started with the web interfaced generators with included hosting in their offerings:

I have tried [wix](https://www.wix.com/) and [squarespace](https://www.squarespace.com/) before, they are fantastic for quick and easy website generation, but their free offering has ads, so again, a big no for me.

I discovered [ghost](https://ghost.org/) as the platform used by one of the bloggers I follow ([Sebastian Ruder](https://ruder.io/)), turns out is a fantastic evolution over wordpress. It runs on the latest technologies, its interface is quite modern, and it is focused on one thing only: publishing. They have a paid hosting service, but the software is open sourced, therefore free to use in any hosting.

Next were the generators that don't have a web interface, but can be easily set up:

I also tested [gatsby](https://www.gatsbyjs.com/docs/glossary/static-site-generator/) with it's own Gatsby Cloud hosting service, [here is my test site](https://amaynez.gatsbyjs.io/). They also use GitHub as a base to host the source files to build the website, so you create a repository, and it is connected to it. I found the free template offerings quite limited for what I was looking for.

Finally it came the turn for [jekyll](https://jekyllrb.com/), although an older, and slower generator (compared to Hugo and Gatsby), it was created by one of the founders of GitHub, so it's integration with GitHub Pages is quite natural and painless, so much so, that to use them together you don't even have to install Jekyll in your machine! You have two choices:
1. keep it all online, special `gh-pages` .
2. Have a synchronized local copy of the source files for the website.

I picked up a template, just forked the repository and started modifying the files to customize it, it was fast and easy, I even took it upon myself to add some functionality to the template (it served as a coding little project) like:
- SEO meta tags
- Dark mode ([configurable in _config.yml file](https://github.com/the-mvm/the-mvm.github.io/blob/a8d4f781bfbc4107b4842433701d28f5bbf1c520/_config.yml#L10))
- comments 'courtain' to mask the disqus interface until the user clicks on it ([configurable in _config.yml](https://github.com/the-mvm/the-mvm.github.io/blob/d4a67258912e411b639bf5acd470441c4c219544/_config.yml#L13))

![my new blog](./assets/img/template_screenshots/homepage-responsive.jpg)

![night theme toggle](./assets/img/template_screenshots/light-toggle.png)

As a summary, Hugo and Gatsby might be much faster than Jekyll to build the sites.

You can use the modified template yourself by [forking my repository](https://github.com/the-mvm/the-mvm.github.io/fork/). Let me know in the comments or feel free to contact me if you are interested in a detailed walkthrough on how to [set it all up](https://github.com/the-mvm/the-mvm.github.io#Installation). 

#### Hosting
Since I decided on Jekyll to generate my site, the choice for hosting was quite obvious, **[Github Pages](https://pages.github.com)** is very nicely integrated with it, it is free, and it has no ads! Plus the domain name isn't too terrible ([the-mvm.github.io](https://the-mvm.github.io)).

##### Interplanetary File System
To contribute to and test [IPFS](https://github.com/ipfs/ipfs#quick-summary) I also set up a [mirror](https://weathered-bread-8229.on.fleek.co/) in IPFS by using [fleek.co](https://fleek.co).

But this fix did not work for the search function, because it relies on a `search.json` file (also generated programmatically to be served as a static file), therefore when generating this file one either use the relative path for the `root` directory or for a nested directory.
