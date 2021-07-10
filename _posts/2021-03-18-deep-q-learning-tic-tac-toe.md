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

<center><img style="float: left;margin-right: 1em;" src='./assets/img/posts/20210318/tm_circle.png' width="310" height="300"></center>

위도/경도 를 TM 좌표계로 변환한 위치에 Array 지점들을 표시하여 모든 점들을 포함하는 최소원을 그래프에 나타내고 원의 반경을 계산하여 결과 표시

<ul><li>마운트 위치 테이블 정보 수신.</li><li>FKP, VRS mount 기준국 접속 가능.</li><li>접속계정 데이타 DB로 관리</li><li>GPS NMEA 데이타 로거로도 적용 (위성지도 연동) </li></ul>

## Designing TCP network codes
<center><img src='./assets/img/posts/20210318/tcp_block-code.png' width="540"></center><br>
<small>[Block diagram] TCP fgv logic code</small>

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

After all the failures I figured I had to rethink the topology of the network and play around with combinations of different networks and learning rates.

**Finally tested FKP,VRS** This is quite an achievement, it seems that the change in network topology is working, although it also looks like the loss function is stagnating at around 0.15.

It is quite interesting :
- the rewards policy
- the epsilon greedy strategy
- whether to train vs. a random player or an "intelligent" AI.

And so far the most effective change

<a name='Model4'></a>
### Model 4 - implementing momentum

I [reached out to the reddit community](https://www.reddit.com/r/MachineLearning/comments/lzvrwp/p_help_with_a_reinforcement_learning_project/) and a kind soul pointed out that maybe what I need is to apply momentum to the optimization algorithm. 

- Stochastic Gradient Descent with Momentum
- RMSProp: Root Mean Square Plain Momentum


```python
self.PolicyNetwork = Sequential()
for layer in hidden_layers:
    self.PolicyNetwork.add(Dense(
                           units=layer,
                           activation='relu',
                           input_dim=inputs,
                           kernel_initializer='random_uniform',
                           bias_initializer='zeros'))
self.PolicyNetwork.add(Dense(
                        outputs,
                        kernel_initializer='random_uniform',
                        bias_initializer='zeros'))
opt = Adam(learning_rate=c.LEARNING_RATE,
           beta_1=c.GAMMA_OPT,
           beta_2=c.BETA,
           epsilon=c.EPSILON,
           amsgrad=False)
self.PolicyNetwork.compile(optimizer='adam',
                           loss='mean_squared_error',
                           metrics=['accuracy'])
```
As you can see I am reusing all of my old code, and just replacing my Neural Net library with Tensorflow/Keras, keeping even my hyper-parameter constants.

With Tensorflow implemented, **the loss function was still stagnating! My code was not the issue.**
<a name='Model7'></a>
### Model 7 - changing the training schedule
Next I tried to change the way the network was training as per [u/elBarto015](https://www.reddit.com/user/elBarto015) [advised me on reddit](https://www.reddit.com/r/reinforcementlearning/comments/lzzjar/i_created_an_ai_for_super_hexagon_based_on/gqc8ka6?utm_source=share&utm_medium=web2x&context=3).

The way I was training initially was:
- Games begin being simulated and the outcome recorded in the replay memory
- Once a sufficient ammount of experiences are recorded (at least equal to the batch 

<center><img src='./assets/img/posts/20210318/ReplayMemoryBefore.png' width="540"></center>

As of today, [self play](https://medium.com/applied-data-science/how-to-train-ai-agents-to-play-multiplayer-games-using-self-play-deep-reinforcement-learning-247d0b440717), and it looks like a viable option to test and a fun coding challenge. 
