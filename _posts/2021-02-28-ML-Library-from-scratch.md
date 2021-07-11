---
layout: post
read_time: true
show_date: true
title:  Other accessory
date:   2021-02-28 12:32:20 -0600
description: 다양한 모바일 로봇 악세사리.
img: posts/20210228/trailer-1-c.png 
tags: [accessory, trailer, speaker, led]
author: Ybbaek
github: amaynez/GenericNeuralNetwork/ # amaynez/GenericNeuralNetwork/
---
## Robot 악세사리 옵션 / Accessory
### 트레일러 / Trailer
모바일 로봇에 장착하거나 연결해서 사용할 수 있는 다양한 악세사리를 제공하고 있습니다.
<center><img src="./assets/img/posts/20210228/trailer-4.png" width="480px"><small>SRC 관련 트레일러 (Trailer)</small></center>

### Dot matrix 는 R,G,B 3종류의 색이 있습니다.

<center><img src="./assets/img/posts/20210228/dot_matrix.png"><small>8x32 led dot matrix 아두이노와 연결됨</small></center>

SRC 로봇 기본 프로그램에는 기본적을 아래와 같은 정보들을 dot matirx 를 통해 표시하게 할 수 있습니다:
선택은 조이스틱 키를 통해서 선택
- **GNSS/GPS** :
    - waypoint 와 현재 차량과의 거리 오차 (+- xx meter)
    - 현재 위도 경도 값
- **시간** 현재 로봇 운행시간
- **IMU** heading 방향 값

### ASV 조타 방향키
ASV 보트의 방향키는 크기, 색에 따라 3가지 종류가 있습니다.:

<center><img src="./assets/img/posts/20210228/keying.png"><small>고속일때 효과가 있을 것ㄱ</small></center>

Then we reshape the z array as a one dimensional array to use it to color the scatter plot:

### Log analyzer

<center><img src="./assets/img/posts/20210228/log-replay.jpg"></center>

Log replay 는 실행파일로 제공되는 툴이며 기능은 아래와 같습니다.:

- 다중 경로파일 선택 가능 / waypoint files (TM, gpx)
- GPS/GNSS 모듈제조사 완 상관없이 사용 (단, NMEA format 이어야 함)
- 구글맵 연동하여 replay / Google map synch
- save and load log file