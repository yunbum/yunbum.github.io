---
layout: post
read_time: true
show_date: true
title:  경로추종 알고리즘 / Path planning, tracking
date:   2021-01-25 13:32:20 -0600
description: 경로처리 관련 처리관련 알고리즘 / Local path
img: posts/20210125/dwa-small.png 
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

<center><img src='./assets/img/posts/20210125/dwa-small.png'></center>

The neuron has 3 inputs and weights to calculate its output:
    
    input 1 is the X coordinate of the point,
    Input 2 is the y coordinate of the point,
    Input 3 is the bias and it is always 1

    Input 3 or the bias is required for lines that do not cross the origin (0,0)

The Perceptron starts with weights all set to zero and learns by using 1,000 random points per each iteration.

<center><img src='./assets/img/posts/20210125/Learning_1000_points_per_iteration.jpg'></center>

In the end, the perceptron always converges into a solution and finds with great precision the line we are looking for.
