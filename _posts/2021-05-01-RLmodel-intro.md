---
layout: post
read_time: true
show_date: true
title: "알엘모델 소개 - RLmodel"
date: 2021-05-01
img: posts/20210501/rlmodel.png # post7-header.webp
tags: [Reinforcement Learning]
category: theory
author: Ybbaek
description: "RLmodel 이란: Intro."
---
## RLmodel (Reinforcement Learning model maker)
알엘모델을 다양한 강화학습,머신러닝 특히 자율주행을 테스트 할 수 있는 모바일 로봇장 플랫폼을 제공하는 업체 입니다.:
- [SRC 는 자율주행 알고리즘 및 교육목적으로 개발 되었습니다.](https://github.com/yunbum/SRC)
- [10여년 간 네이버 카페를 운영하여 관련 예제나 테스트 결과등을 공유하고 있습니다.](https://cafe.naver.com/iltech)
- [다른 RLmodel 유투브 영상들](https://www.youtube.com/channel/UCd23NgICe3702uqAAk4HYFQ/videos)

![HW SW 모듈개발 및 주행테스트](./assets/img/posts/20210402/src_hw-sw.png)
<small>다양한 HW 및 SW 모듈로 주행알고리즘 검증 및 센서퓨전 테스트에 적용완료 </small>

차량제어는 Python, C, 등의 컴퓨터언어와도 호환이 되도록 시리얼통신으로 제어할 수 있습니다. LabVIEW 라고하는 National Instrument 사의 프로그래밍 언어도 지원합니다.

## 제공 제품군
SRC(A,B,C,D 타입), ASV(자율운항보트), Inverted pendulum, Ball Balance robot 등이 있습니다.

## 주요특징
프레임은 전체가 알루미늄, 철 등의 금속. 일반 휴대용 보조배터리 파워로 일반 USB 충전이 가능하여 편리하며. 통 고무 타이어로 구성되어 펑크날 위험이 없습니다. ([source](https://www.thinkautomation.com/bots-and-ai/a-history-of-automation-the-rise-of-robots-and-ai/)), 구조와 강성이 상당히 개량되어 전체적인 안정성은 일반 플라스틱 RC 카에 비할 수 없고, 현재 수십 km 실외 운행으로 내구성 검증도 완료:

![Frame body](./assets/img/posts/20210402/src-b2_3.jpg)
<small>개발시간 전체 약 10여년. 최종 전체 금속기반의 구조는 2019년 완성</small>

## 강화학습 적용 플랫폼

모든 RLmodel 로봇들은 강화학습을 적용하고 테스트 해볼 수 있는 목적으로 개발이 시작되었으며 현재도 다양한 접근으로 예제들을 검토 중입니다.

## SW 모듈
자율주행 모바일 로봇에 적용할 수 있는 Window OS 산에 LabVIEW 언어로 개발된 RLrobotics 가 있습니다.

![post7-alexa-steps](./assets/img/posts/20210402/led-light.png)
<small>야간주행 테스트를 위한 LED light</small>
추가적으로 ROS 환경에 적합하도록 패키지도 개발 중 입니다.