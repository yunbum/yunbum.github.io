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

## Background
GPS 의 정밀도를 높이기 위한 RTK mode 중 Network RTK 기능 설정을 위해 필요한 Ntrip client 툴을 직접 개발하여 사용하고, 별로도 독립 툴로 개발하여 배포합니다..

![RL_Connect](./assets/img/posts/20210318/RL_Connect.jpg)
<small>[RL_Connect] Netwrok RTK 모드 설정을 위한 Ntrip client..</small>

<center><img style="float: left;margin-right: 1em;" src='./assets/img/posts/20210318/tm_circle.png' width="310" height="320"></center>

TM 좌표계로 변환 -> 점들을 포함하는 최소원을 계산하여 원의 반경 계산하여 표시

<ul><li>마운트 위치 테이블 정보 수신.</li><li>FKP, VRS mount 기준국 접속 가능.</li><li>접속계정 데이타 DB로 관리</li><li>GPS NMEA 데이타 로거로도 적용 (위성지도 연동) </li></ul>

I started out with two hidden layers of 36 neurons each.

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
@staticmethod
def cyclic_learning_rate(learning_rate, epoch):
    max_lr = learning_rate*c.MAX_LR_FACTOR
    cycle = np.floor(1+(epoch/(2*c.LR_STEP_SIZE)))
    x = np.abs((epoch/c.LR_STEP_SIZE)-(2*cycle)+1)
    return learning_rate+(max_lr-learning_rate)*np.maximum(0,(1-x))
```

<br>With these many changes, I decided to restart with a fresh set of random weights and biases and try training more (much more) games.

<center><img src='./assets/img/posts/20210318/Loss_function_and_Illegal_moves6.png' width="540">
<small>1,000,000 episodes, 7.5 million epochs with batches of 64 moves each<br>
Wins: 52.66% Losses: 36.02% Ties: 11.32%</small></center>

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

<a name='Model4'></a>
### Model 4 - implementing momentum

I [reached out to the reddit community](https://www.reddit.com/r/MachineLearning/comments/lzvrwp/p_help_with_a_reinforcement_learning_project/) and a kind soul pointed out that maybe what I need is to apply momentum to the optimization algorithm. 

- Stochastic Gradient Descent with Momentum
- RMSProp: Root Mean Square Plain Momentum

As you can see I am reusing all of my old code, and just replacing my Neural Net library with Tensorflow/Keras, keeping even my hyper-parameter constants.

With Tensorflow implemented, **the loss function was still stagnating! My code was not the issue.**
<a name='Model7'></a>
### Model 7 - changing the training schedule
Next I tried to change the way the network was training as per [u/elBarto015](https://www.reddit.com/user/elBarto015) [advised me on reddit](https://www.reddit.com/r/reinforcementlearning/comments/lzzjar/i_created_an_ai_for_super_hexagon_based_on/gqc8ka6?utm_source=share&utm_medium=web2x&context=3).

The way I was training initially was:
- Games begin being simulated and the outcome recorded in the replay memory
- Once a sufficient ammount of experiences are recorded (at least equal to the batch 

![tcp_block](./assets/img/posts/20210318/statistics.jpg)
<small>[tcp_block] LabVIEW TCP Function Block Diagram code.</small>

As of today, [I converting RC Connect to Linux / Ubuntu version](https://github.com/yunbum/NtripClient), and it looks like a viable option to test and a fun coding challenge. 
