---
layout: post
read_time: true
show_date: true
title: "스마트팜 / Smart Farm Mobile robots!"
date: 2021-09-02
img: posts/20210902/right.jpg # post8-rembrandt.jpg
tags: [gmap, labview, map, .net]
category: opinion
author: Ybbaek
description: "LabVIEW Front panel UI 상에 지도(위성, 하이브리드, 등)을 쉽게 표시하고 경로 설정등을 할 수 있는 vi"
---
## 기본기능
알엘모델 SRC-D Smart farm 버전의 목적은 실내외 특히 야외에 있는 농작물의 다양한 발육상태, 이상유무 등을 원격에서도 최대 4대의 카메라를 통해 확인/분석/전송을  편리하게 할 수 있게하여 더운 여름이나 오지에 가야하는 불편함을 줄여줄 수 있습니다. 

### 상세설명
기본적으로 로봇이 이동하는 경로를 위성지도를 활용하여 설정하고 작성된 경로파일(waypoint) 을 전송하여 로봇이 기본적으로 경로를 바탕으로 GPS 기반으로 이동하여 동작하게 됩니다.
![Field](./assets/img/posts/20210902/field.jpg)
<small>[RLMap-UI] 야외 경작지 이동화면.</small>
![RLMap-prj](./assets/img/posts/20210902/grass.jpg)
<small>[RLMap-prj] 다양한 환경의 오프로드 테스트 진행.</small>

### 주행설정/분석
![GPS 관련 소프트웨어](./assets/img/posts/20210902/Seed_log.jpg)
<small>[log file] 주행후 로그파일을 분석하여 경로확인 및 평가.</small>
설정된 경로확인 및 실제주행 경로와의 비교. 그리고 전체 경로의 정밀도 제어값 등 다양한 정보들을 다시 분석하고 확인 할 수 있는 SW로 준비되어 있습니다.

### 센서모듈 추가/선택
![ robot](./assets/img/posts/20210902/left.jpg)
<small>[Map provider] ex) Street4U 화면.</small>
기본 장착되어 있는 카메라,라이다, GPS, 등의 센서를 변경하거나 추가하여 기능을 보완이 가능.

### 부가기능
![SRC hw option](./assets/img/posts/20210902/trailer.jpg)
<small>[SRC history] 모바일 로봇에 별도의 trailer 를 추가장착한 사진.</small>
트레일러를 추가하여 배터리 확장을 비롯한 추가 장비나 물품을 실을 수 있음.

### 검토기능
![The Next SRC](./assets/img/posts/20210902/laser.jpg)
<small>[The Next SRC](https://github.com/yunbum/SRC) 추가 장착레이져.</small>
참고로 산업용 레이져를 추가하여 직진성, 라이다 감지거리 등을 확인하여 테스트 할 수 있도록 하였 추가 검토 중 입니다.

### 응용
![cartpole](./assets/img/posts/20210902/offroad-2.jpg)
<small>다양한 목적의 위치표시 </small>
자율주행에 의한 모니터링 이외에도 간단한 잡초제거, 대기질 측정, 방역 등의 기능으로 응용이 될 수 있습니다.