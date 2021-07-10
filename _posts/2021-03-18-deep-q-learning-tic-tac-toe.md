---
layout: post
read_time: true
show_date: true
title:  RL Connect 프로그램 제공 - Free Ntrip client Network RTK
date:   2021-03-18 15:14:20 -0600
description: Free Ntrip client 'RL Connect'
img: posts/20210318/C94-M8P.png
tags: [GPS, Network rtk, Ntrip client, GNSS, fkp, vrs]
author: Ybbaek
github: amaynez/TicTacToe/
toc: yes # leave empty or erase for no TOC
---

## RTK Real Time Kinematic
GPS 의 정밀도를 높이기 위한 RTK mode 중 Network RTK 기능 설정을 위해 필요한 Ntrip client 툴을 직접 개발하여 사용하고, 별로도 독립 툴로 개발하여 배포합니다..

![RL_Connect](./assets/img/posts/20210318/RL_Connect.jpg)
<small>[RL_Connect] Netwrok RTK 모드 설정을 위한 Ntrip client..</small>

기본적으로 RLmodel 의 자율주행 차량과 자율운항 보트에는 기본 내장된 기능
일반 Ntrip client 에는 없는 모드별 분포, 비율을 계산하여 상태를 분석할 수 있도록 지원

<center><img style="float: left;margin-right: 1em;" src='./assets/img/posts/20210318/tm_circle.png' width="310" height="320"></center>

TM 좌표계로 변환 -> 점들을 포함하는 최소원을 계산하여 원의 반경 계산하여 표시

<ul><li>마운트 위치 테이블 정보 수신.</li><li>FKP, VRS mount 기준국 접속 가능.</li><li>접속계정 데이타 DB로 관리</li><li>GPS NMEA 데이타 로거로도 적용 (위성지도 연동) </li></ul>

## Source code / Github
### Python -> LabVIEW

 참고 python 코드 깃헙 <a href="https://github.com/tridge/pyUblox/blob/master/ntrip.py">tridge/pyUblox</a> Ntrip client 소스코드. 

```python
header =\
"GET /{} HTTP/1.1\r\n".format(mountpoint) +\
"Host \r\n".format(server) +\
"Ntrip-Version: Ntrip/2.0\r\n" +\
"User-Agent: NTRIP pyUblox/0.0\r\n" +\
"Connection: close\r\n" +\
"Authorization: Basic {}\r\n\r\n".format(pwd)
```
```python
static const char encodingTable [64] = {
  'A','B','C','D','E','F','G','H','I','J','K','L','M','N','O','P',
  'Q','R','S','T','U','V','W','X','Y','Z','a','b','c','d','e','f',
  'g','h','i','j','k','l','m','n','o','p','q','r','s','t','u','v',
  'w','x','y','z','0','1','2','3','4','5','6','7','8','9','+','/'
};
```
<br>GNSS/GP 모듈은 uBlox F9P M8P, Sententrio Mosaic X5, MBC MRP, 등에 적용하여 테스트.

<center><img src='./assets/img/posts/20210318/hw_block.jpg' width="540">
<small>RL Connect Hardware Function block</small></center>

After **24 hours!**, my computer 
<a name='Model3'></a>
### Model 3 - new network topology

고정 지점에서 정밀도 분석을 할 경우를 참고하여 ref x1,x2,x3 원을 그래프에 표시하게 하여 현재 데이타의 상태나 품질을 확인 할 수 있음.

**Fully support Any GNSS/GPS module and FKP,VRS mode** 다른 무료 Ntrip client 프로그램들이 제조사 판매제품만을 지원하거나 FKP/VRS 모드에 제한이 있는 것과는 차별화 해서 모두 가능하도록 지원.

추가 포함기능 :
- GPS 모듈 2개를 동시에 연동하여 NMEA 데이타 표시 가능
- 위와 같은 모드로 2 지점이 있을 경우, 두 지점간의 거리와 각도를 표시
- Raw RTCM 메세지를 직접 확인가능.
- 로그파일을 기본으로 남기도록 하여 후에 데이타 확인 가능

<a name='Communication'></a>
### Communication - TCP/IP, Serial

- Google map api 를 활용하여 실시간 위성지도 연동
- Hardware를 포함한 Network 상태 모니터링 / USB Serial, TCP, RTCM 메세지

기본 Base 프로그램은 LabVIEW 언어를 활용

With LabVIEW implemented, **the issue**
<a name='LabVIEW'></a>
### LabVIEW - National Instrument programming language

Mode 를 지속적으로 카운팅 하여 정밀도 상태 표시:
- 지정된 시간마다 모드의 상태를 카운팅 (N/A, Standalone, RTK float, RTK fixed)
- 카운팅 된 회수를 바탕으로 백분율로 계산하여 % 스케일로도 표시 

![tcp_block](./assets/img/posts/20210318/statistics.jpg)
<small>[tcp_block] LabVIEW TCP Function Block Diagram code.</small>

현재 지원하는 윈도우 버전 뿐만 아니라, [I converting RC Connect to Linux / Ubuntu version](https://github.com/yunbum/NtripClient), Linux Ubuntu 버전 변화작업도 진행예정. 
