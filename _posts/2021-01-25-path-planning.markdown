---
layout: post
read_time: true
show_date: true
title:  경로추종 알고리즘 / Path planning, tracking
date:   2021-01-25 13:32:20 -0600
description: 경로처리 관련 처리관련 알고리즘 / Local path
img: posts/2021/20210125/dwa-small.png 
tags: [local path, avoidance, dynamic window approach]
author: Ybbaek
github:  yunbum
mathjax: yes
---
## Testing Path planning algorithms
다양한 Path planning 알고리즘들을 테스트 하고 적용하고 있습니다.
소스는 Python robotics 의 소스코드를 바탕으로 하였습니다.

### Dynamic Window Approach
A Dynamic Window Approach 는 실시간으로 정해진 윈도우 영역의 cost 를 계산하여 경로를 계산하고 판단하는 알고리즘.

<center><img src='./assets/img/posts/2021/20210125/dwa-small.png'></center>

The neuron has 3 inputs and weights to calculate its output:
    
    cost 1 is the goal distance of the agv,
    cost 2 is the speed of the agv,
    cost 3 is the obstacles distance

The 현재 AGV의 속도, Goal 까지의 거리, 장애물들 과의 거리 등을 실시간으로 설정 영역안의 궤적들로 계산하여 최적 경로를 판단하여 이동.

<center><img src='./assets/img/posts/2021/20210125/dwa-trajectory.png'></center>

해당로직은 Python Robotics 의 파이썬 로직을 약간 수정하여 시뮬레이션 한 예제입니다. 현재는 로봇에 적용하여 여러다른 로봇들에 적용하여 튜닝작업 진행 중에 있습니다.

<iframe width="560" height="315" src="https://www.youtube.com/embed/Gp4lUpIy7Jc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
