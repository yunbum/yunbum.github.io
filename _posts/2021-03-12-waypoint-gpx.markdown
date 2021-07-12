---
layout: post
read_time: true
show_date: true
title:  경로파일 (waypoint) / GPX route editor 
date:   2021-03-12 13:32:20 -0600
description: GPX format file editor tool.
img: posts/20210312/tm_interpolation.png
tags: [waypoint, gpx, tm, point]
author: Ybbaek
github: yunbum
mathjax: yes # leave empty or erase to prevent the mathjax javascript from loading
toc: yes # leave empty or erase for no TOC
---
## GPX 파일처리 / GPX format file handling
SRC 기본 프로그램은 실외 자율주행 경로생성을 위한 툴로 GPX editor를 사용하고 있습니다. 위성지도 혹은 일반 지도상에 이동하려는 경로를 클릭하면 해당 지점들의 정보가 xml 포맷으로 저장되어 생성됩니다.

### GPX Route editor
[source](http://www.gpsnote.net/)

<center><img src='./assets/img/posts/20210312/route-editor-small.jpg' width="540">
<small>GPX route editor 실행화면</small></center>

### 위도/경도 xml 데이타 추출
gpx 파일에 있는 위도/경도 데이타를 읽고 TM 좌표변환 후에 실제 주행경로 로직에 반영하여 계산합니다.

<center><img src='./assets/img/posts/20210312/latlong_point.png' width="540">
<small>GPX 파일의 위도/경도 값 읽어 TM 좌표로 표시</small></center>

gpx 파일에서 TM 좌표 변환을 한 후에는 촘촘히 interpolation 하여 최종 실제 경로로 사용합니다.
<center><img src='./assets/img/posts/20210312/tm_interpolation.png' width="540">
<small>TM 좌표들의 점들을 interpolation 하여 최종경로 그래프</small></center>

