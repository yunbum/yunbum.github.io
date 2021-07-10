---
layout: post
read_time: true
show_date: true
title: "자율주행 플랫폼 SRC 란, what is SRC (Self Driving Rc Car?"
date: 2021-04-02
img: posts/20210402/SRC-B2_2.jpg # post7-header.webp
tags: [Robot, RC, GPS, Camera, Lidar]
category: theory
author: Ybbaek
description: "SRC 모바일로봇 이란: SRC Intro."
---
SRC 은 GPS, Camera, Lidar, IMU, 등의 센서를 기반으로 자율주행 교육 및 주행알고리즘, 센서퓨전 등을 쉽고 효과적으로 개발 할 수 있는 자율주행 모바일로봇 플랫폼 입니다.:
- [This Powerful Self Driving HW Led to Developer and students in this field.](https://github.com/yunbum/SRC)
- [Check detail picture, code examples and hw information](https://cafe.naver.com/iltech)
- [Other videos on Youtube for SRC](https://www.youtube.com/channel/UCd23NgICe3702uqAAk4HYFQ/videos)

![HW SW 모듈개발 및 주행테스트](./assets/img/posts/20210402/src_hw-sw.png)
<small>다양한 HW 및 SW 모듈로 주행알고리즘 검증 및 센서퓨전 테스트에 적용완료 </small>

차량제어는 Python, C, 등의 컴퓨터언어와도 호환이 되도록 시리얼통신으로 제어할 수 있습니다. LabVIEW 라고하는 National Instrument 사의 프로그래밍 언어도 지원합니다.

SRC (**S**elf driving **R**emote control **C**ar) 는 자율주행 차량의 영어 약자 이면 현재 SRC-A,B,C,D 등의 타입이 있습니다.
![SRC models](./assets/img/posts/20210402/SRC_models.png)
<small>개발시간 전체 약 10여년. 최종 전체 금속기반의 구조는 2019년 완성</small>

주요특징: 프레임은 전체가 알루미늄, 철 등의 금속. 일반 휴대용 보조배터리 파워. 통 고무 타이어.  ([source](https://www.thinkautomation.com/bots-and-ai/a-history-of-automation-the-rise-of-robots-and-ai/)), 구조와 강성이 상당히 개량되어 전체적인 안정성은 일반 플라스틱 RC 카에 비할 수 없고, 현재 수십 km 실외 운행으로 내구성 검증도 완료:

![Frame body](./assets/img/posts/20210402/src-b2_3.jpg)
<small>개발시간 전체 약 10여년. 최종 전체 금속기반의 구조는 2019년 완성</small>

개별 모듈들의 구성은 맞춤형으로 제공 될 수 있으며, 기본 모터와 모터드라이버, 상위제어기(아두이노) 만으로도 제공이 되며 제어명령은 USB 을 통한 시리얼 통신으로 제어가 가능합니다..

![sensors & modules](./assets/img/posts/20210402/SRC-B_parts.png)
<small>Full option 상태의 센서 및 기타 모듈 구성도</small>

SRC model / SRC 차량의 모델은 A,B,C,D 타입등으로 모터사양, 크기, 디자인 등으로 구분이 되어 나뉘고 동일한 모델에서는 이중모터로 업그레이드가 가능합니다. (Dual moter) .

<center><img style="float: left;margin-right: 1em;" src='./assets/img/posts/20210402/dual_motor.jpg' width="310" height="300"></center>
<small>레이싱 모델인 이중모터(Dual motor) 구조</small>

모바일 로봇의 종류는 기본 SRC 차량모델에 이어 ASV 보트(선박) 모델도 있으며 교육목적의 Pendulum, Ball Balance robot 등도 있습니다.

The neural network.

#### 3. Replying to us

Once Alexa understood what we meant, it then proceeds to execute the action of the command it interpreted and it replies to us in turn using natural language. This is accomplished using a technique called speech synthesis, things like pitch, duration and intensity of the words and phonems are selected based on the "meaning" of what Alexa will respond to us: "Playing songs by Van Halen on Spotify" sounding quite naturally. And all is accomplished with neural networks executing many simple math operations.

![post7-alexa-steps](./assets/img/posts/20210402/post7-alexa-steps.png)
<small>Although it seems quite complex, the process for AI to understand us can be boiled down to simple math operations</small>

