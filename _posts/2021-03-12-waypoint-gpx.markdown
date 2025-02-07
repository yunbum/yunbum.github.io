---
layout: post
read_time: true
show_date: true
title:  경로파일 (waypoint) / GPX route editor 
date:   2021-03-12 13:32:20 -0600
description: GPX format file editor tool.
img: posts/2021/20210312/gpx_route_sample.png
tags: [waypoint, gpx, tm, point]
author: Ybbaek
github: yunbum
mathjax: yes # leave empty or erase to prevent the mathjax javascript from loading
toc: yes # leave empty or erase for no TOC
---
## GPX 파일처리 / GPX format file handling
SRC 경로 waypoint 파일은 GPX, NMEA, TM 등의  위성지도 혹은 일반 지도상에 이동하려는 경로를 클릭하면 해당 지점들의 정보가 xml 포맷으로 저장되어 생성됩니다.

### GPX Route editor
경로를 생성하는 툴로 GPX 파일포맷을 지원하는 'GPX route editor' 추천 합니다. 무료이고 클릭만으로 경로가 생성되고 gpx 파일로 생성을 할 수 있게하는 툴입니다.
[source](http://www.gpsnote.net/)

<center><img src='./assets/img/posts/2021/20210312/route-editor-small.jpg' width="540">
<small>GPX route editor 실행화면</small></center>

### 위도/경도 xml 데이타 추출
gpx 파일에 있는 위도/경도 데이타를 읽고 TM 좌표변환 후에 실제 주행경로 로직에 반영하여 계산합니다.

<center><img src='./assets/img/posts/2021/20210312/latlong_point.png' width="540">
<small>GPX 파일의 위도/경도 값 읽어 TM 좌표로 표시</small></center>

gpx 파일에서 TM 좌표 변환을 한 후에는 촘촘히 interpolation 하여 최종 실제 경로로 사용합니다.
<center><img src='./assets/img/posts/2021/20210312/tm_interpolation.png' width="540">
<small>TM 좌표들의 점들을 interpolation 하여 최종경로 그래프</small></center>

