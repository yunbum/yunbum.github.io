---
layout: post
read_time: true
show_date: true
title: "ASV 자율운항 보트 / Autonomous Surface Vehicle"
date: 2021-03-24
img: posts/20210324/usv-a1.jpg
tags: [general blogging, thoughts, life]
author: Ybbaek
description: "무인 자율운항 보트/선박 ASV"
---

자율운항 선박개발 및 알고리즘 테스트 목적으로 RLmodel ASV-A1 을 출시, 자율운항 선박(보트) 등의 주행알고리즘 개발이나 선박주행의 센서퓨전, 기타 제어로직 연구에 적합하도록 개발되었습니다.
사양:
- 수중모터(Thruster) 2개의 속도제어를 이용하여 방향제어
- GPS, Lidar 를 활용하여 주행경로, 충돌회피 등에 적용

추가옵션:
- 방향제어를 위한 키 추가 장착가능
- 사양에 맞게 배터리 옵션, 제어기 설정등 맞춤형 제작 가능
  
<iframe width="560" height="315" src="https://www.youtube.com/embed/PfX4jajMRxE" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

For my next project I think I will start to do the basic hand-written digits recognition, which is the Machine Learning Hello World, for this I think I will start to use Tensorflow already.

### 자율운항 보트 대회등의 목적에 적합하도록 기본 제어 매뉴얼 및 예제 코드 제공.

#### ESC Calibration instruction
초기에 제공되는 ESC 는 기본적으로 초기 Calibration 이 필요하며 Arduino 를 활용하여 모터의 Min/Max speed 설정을 하여 사용을 해야 합니다..

There is a myriad of website generators nowadays, after a lengthy search the ones I ended up considering are:
- [wordpress](https://wordpress.com/)
- [wix](https://www.wix.com/)
- [squarespace](https://www.squarespace.com/)
- [ghost](https://ghost.org/)

I started with the web interfaced generators with included hosting in their offerings:

I have tried [wix](https://www.wix.com/) and [squarespace](https://www.squarespace.com/) before, they are fantastic for quick and easy website generation, but their free offering has ads, so again, a big no for me.

Finally it came self sailing boat
1. keep it all online, special `gh-pages` .
2. Have a synchronized local copy of the source files for the website.

I picked up a template, like:
- SEO meta tags
- Dark mode 
- comments 'courtain' to mask the disqus interface

![my new blog](./assets/img/template_screenshots/homepage-responsive.jpg)

![night theme toggle](./assets/img/template_screenshots/light-toggle.png)

As a summary, Hugo and Gatsby might be much faster than Jekyll to build the sites.

You can use the modified template yourself by [forking my repository](https://github.com/the-mvm/the-mvm.github.io/fork/). 

#### Hosting
Since I decided on Jekyll to generate my site, the choice for hosting was quite obvious, **[Github Pages](https://pages.github.com)** is very nicely integrated with it, it is free, and it has no ads! Plus the domain name isn't too terrible ([the-mvm.github.io](https://the-mvm.github.io)).

