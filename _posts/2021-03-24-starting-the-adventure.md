---
layout: post
read_time: true
show_date: true
title: "ASV 자율운항 보트 / Autonomous Surface Vehicle"
date: 2021-03-24
img: posts/20210324/usv-a1.jpg
tags: [general blogging, thoughts, life]
author: Ybbaek
description: "무인 자율운항 보트/선박 ASV"
---
## 무인 자율운항 선박 
지상이나 뿐만 아니라 물 위에서 무인보트 개발을 위한 ASV, 자율운항 선박(보트) 등의 주행알고리즘 개발이나 선박주행의 센서퓨전, 기타 제어로직 연구에 적합하도록 개발되었습니다.

사양:
- 수중모터(Thruster) 2개의 속도제어를 이용하여 방향제어
- GPS, Lidar 를 활용하여 주행경로, 충돌회피 등에 적용

추가옵션:
- 방향제어를 위한 키 추가 장착가능
- 사양에 맞게 배터리 옵션, 제어기 설정등 맞춤형 제작 가능
  
<iframe width="560" height="315" src="https://www.youtube.com/embed/PfX4jajMRxE" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

SRC 와 같은 자율주행 차량보다 좀더 자유로운 제어나 운항을 테스트 해 볼 수 있으나 물 위에서 움직이는 만큼 이동궤적에 차이가 있습니다.

### 수중모터, 방향키 등을 쉽게 추가/ 변경이 가능
기본 2개의 수중모터를 사용하고 있으나 추가나 좀더 높은 사양으로 쉽게 업그레이드가 가능함

#### ESC Calibration instruction
초기에 제공되는 ESC 는 기본적으로 초기 Calibration 이 필요하며 Arduino 를 활용하여 모터의 Min/Max speed 설정을 하여 사용을 해야 합니다..

인터넷상에 많은 Aruduino 기반의 ESC Calibration 소스코드를 활용 할 수 있습니다.:
- [lobodol](https://github.com/lobodol/ESC-calibration/)
- [jeonds1127](https://jdselectron.tistory.com/89/)

<center><img src='./assets/img/posts/20210324/esc-cal.png' width="540">
<small>Arduino를 활용한 ESC Calibation 연결 결선도</small></center>

<iframe width="560" height="315" src="https://www.youtube.com/embed/gZ6vESt1V6Q" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Finally it came self sailing boat
1. 수중모터 테스트와 칼리브레이션은 무부하 상태보다 수중에서 진행하는게 바람직 합니다.
2. 칼리브레이션 진행시 '삐'하는 동작음이 들리고 스케일에 따라 몇 번의 조정이 필요할 수 있습니다.

주의사항(경험):
- 배터리 파워가 부족하면 ESC가 자동으로 동작을 중지하게 하는 경우가 있습니다.
- Calibration은 매번 할 필요없이 처음 1회만 하면 됩니다. 
- Calibration 완료후 관련 Arduino 코드에는 테스트 코드도 같이 제공되니 바로 확인 가능합니다.

<center><img src='./assets/img/posts/20210324/thruster.png' width="540">
<small>다양한 종류의 수중모터(Thruster) 테스트</small></center>

그리고 ASV는 다양한 보트, 요트, 선박등의 디자일들을 고려하여 개량하고 모델을 추가할 예정입니다.

#### 자율운항 보드 대회
테스트 진행이 어느 정도 되고 개발이 마무리 되면 대한조선학회에서 주최하는 '자율운항보드 경진대회' 참석하는 것도 추천 드립니다.


