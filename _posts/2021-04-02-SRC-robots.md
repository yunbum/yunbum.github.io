---
layout: post
read_time: true
show_date: true
title: "SRC 란 / 자율주행 모바일 로봇 플랫폼"
date: 2021-04-02
img: posts/2021/20210402/SRC-B2_2.jpg # post7-header.webp
tags: [Robot, RC, GPS, Camera, Lidar]
category: theory
author: Ybbaek
description: "SRC 모바일로봇 이란: SRC Intro."
---
## 소개 / Intro
SRC 은 GPS, Camera, Lidar, IMU, 등의 센서를 기반으로 자율주행 교육 및 주행알고리즘, 센서퓨전 등을 쉽고 효과적으로 개발 할 수 있는 자율주행 모바일로봇 플랫폼 입니다.:
- [SRC 는 자율주행 알고리즘 및 교육목적으로 개발 되었습니다.](https://github.com/yunbum/SRC)
- [10여년 간 네이버 카페를 운영하여 관련 예제나 테스트 결과등을 공유하고 있습니다.](https://cafe.naver.com/iltech)
- [다른 RLmodel 유투브 영상들](https://www.youtube.com/channel/UCd23NgICe3702uqAAk4HYFQ/videos)

![HW SW 모듈개발 및 주행테스트](./assets/img/posts/2021/20210402/src_hw-sw.png)
<small>다양한 HW 및 SW 모듈로 주행알고리즘 검증 및 센서퓨전 테스트에 적용완료 </small>

차량제어는 Python, C, 등의 컴퓨터언어와도 호환이 되도록 시리얼통신으로 제어할 수 있습니다. LabVIEW 라고하는 National Instrument 사의 프로그래밍 언어도 지원합니다.

## 모델구분 및 특징
SRC (**S**elf driving **R**emote control **C**ar) 는 자율주행 차량의 영어 약자 이면 현재 SRC-A,B,C,D 등의 타입이 있습니다.
타입별 차이는 크기, 속도, 모터토크 등으로 구분되어 나누어 집니다.
![SRC models](./assets/img/posts/2021/20210402/SRC_models.png)
<small>개발시간 전체 약 10여년. 최종 전체 금속기반의 구조는 2019년 완성</small>

SRC B1  

|항목|스펙|참고|
|:---:|---:|:---:|
|모터|12V DC motor| 속도:8000rpm, 전류: 1.3~7.2A, 감속비 19 |
|동작시간|2.5 hour|배터리 기본사양 시|
|상위제어기|미니 Fanless PC|선택가능|
|하위제어기|아두이노|나노 USB 연결|
|휠|4.0인치|통고무 바퀴|
|카메라|일반 웹캠|USB webcam|
|GPS|NMEA 출력 Netwrok RTK 옵션|상세사양은 변동가능|
|최대속도|0.8m/s|Dual motor 옵션시 약 1.8m/s|
|차량크기|430x190x240|라이다 포함시 높이->250mm|  

<br/>
<iframe width="560" height="315" src="https://www.youtube.com/embed/OcdVl3k5qS0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## 주요특징
프레임은 전체가 알루미늄, 철 등의 금속. 일반 휴대용 보조배터리 파워로 일반 USB 충전이 가능하여 편리하며. 통 고무 타이어로 구성되어 펑크날 위험이 없습니다. ([source](https://www.thinkautomation.com/bots-and-ai/a-history-of-automation-the-rise-of-robots-and-ai/)), 구조와 강성이 상당히 개량되어 전체적인 안정성은 일반 플라스틱 RC 카에 비할 수 없고, 현재 수십 km 실외 운행으로 내구성 검증도 완료:

![Frame body](./assets/img/posts/2021/20210402/src-b2_3.jpg)
<small>개발시간 전체 약 10여년. 최종 전체 금속기반의 구조는 2019년 완성</small>

## 모듈/센서
개별 모듈들의 구성은 맞춤형으로 제공 될 수 있으며, 기본 모터와 모터드라이버, 상위제어기(아두이노) 만으로도 제공이 되며 제어명령은 USB 을 통한 시리얼 통신으로 제어가 가능합니다..

![sensors & modules](./assets/img/posts/2021/20210402/SRC-B_parts.png)
<small>Full option 상태의 센서 및 기타 모듈 구성도</small>

![sensors & modules](./assets/img/posts/2021/20210402/SRC_laser.jpg)
<small>산업용 Laser 장착사진</small>

![sensors & modules](./assets/img/posts/2021/20210402/SRC_extra-battery.jpg)
<small>추가 확장 배터리 장착사진 - 주행시간 6시간 이상으로 연장</small>

![sensors & modules](./assets/img/posts/2021/20210402/SSRC_car-cam-mount-1.jpg)
<small>실제차량에 사용하는 양산용 카메라 마운트 사진1</small>

![sensors & modules](./assets/img/posts/2021/20210402/SSRC_car-cam-mount-2.jpg)
<small>실제차량에 사용하는 양산용 카메라 마운트 사진2</small>

![sensors & modules](./assets/img/posts/2021/20210402/SRC_camx3.jpg)
<small>일반 웹캠 3개 장착 사진</small>

## 주행알고리즘
기본으로 제공하는 SRC/ASV 로봇의 주행 로직은 Pure pursuit 로직과 PID 로직을 조향제어 로직에 연결하여 제어하고 있습니다.

![Driving logic](./assets/img/posts/2021/20210402/driving-logic.png)
<small>PID % Pure pursuit 로직 반영</small>

![Main UI](./assets/img/posts/2021/20210402/main_ui.JPG)
<small>사용자 화면 (Main UI)</small>

## 튜닝/ 업그레이드
각 SRC 모델에 (A,B,C,D) 에 속도, 토크를 2배로 향상할 수 있는 듀얼모터 (Dual moter) 옵션 가능.

<center><img style="float: left;margin-right: 1em;" src='./assets/img/posts/20210402/dual_motor.jpg' width="390" height="250"></center>
프레임 강성을 유지하기 위해 보완 패치들로 접속부분 추가 체결.
모바일 로봇의 종류는 기본 SRC 차량모델에 이어 ASV 보트(선박) 모델도 있으며 교육목적의 Pendulum, Ball Balance robot 등도 있습니다.

## 강화학습 적용 플랫폼
모든 RLmodel 로봇들은 강화학습을 적용하고 테스트 해볼 수 있는 목적으로 개발이 시작되었으며 현재도 다양한 접근으로 예제들을 검토 중입니다.

## 기타 편의사항
SRC 차량은 간단한 시리얼 프로토콜 제어가 가능하고 부가 기능으로는 스피커, LED dot matrix, Light 등을 옵션으로 창작하여 테스트 시 차량의 상태나 프로그램의 동작 세부사항 확인이 쉽도록 하였습니다.

### Log analyzer
기본 주행시 생성되는 로그파일이 있으며 Log analyzer 를 사용하여 재생 및 이동중의 경로추종 정밀도 통계등을 확인 할 수 있습니다.
<center><img src="./assets/img/posts/2021/20210228/log-replay.jpg"></center>

Log replay 는 실행파일로 제공되는 툴이며 기능은 아래와 같습니다.:

- 다중 경로파일 선택 가능 / waypoint files (TM, gpx)
- GPS/GNSS 모듈제조사 완 상관없이 사용 (단, NMEA format 이어야 함)
- 구글맵 연동하여 replay / Google map synch
- 평가항목: +/- 오차 최대/최소/평균, 전체이동거리, 총 waypoint 거리 등
