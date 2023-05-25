---
layout: post
read_time: true
show_date: true
title: "Smart Factory robot!"
date: 2023-05-05
img: posts/2023/20230505/Screenshot from 2023-05-09 07-50-05.png # 
tags: [factory, robot, ros2, SLAM, Navigation, rviz]
category: ROS2
author: Ybbaek
description: "ROS2"
---
## SLAM, Navigation
ROS2 기반의 지도생성, 로봇제어, Nav2 파라미터 튜닝 

### 상세설명
ROS2 기반의 실내 자율주행 SLAM, Navigation 적용을 위한 모바일로봇 테스트.
TF를 비롯한 센서퓨전 검증, SLAM 지도 결과물 확인, 최적 Navigation 을 위한 파라미터 수정

![UGV](./assets/img/posts/2023/20230505/20230504_200538.jpg)
<small>[Tracer] 공장 물류 로봇.</small>
![Mount](./assets/img/posts/2023/20230505/20230504_200633.jpg)
<small>[Tracer] PC, Lidar, IMU, Camera 부착 .</small>

### Gmapping, Slam toolbox / SLAM 패키지 적용
![mapping](./assets/img/posts/2023/20230505/ROS2 SLAM Navigation 0-8 screenshot.png)
<small>[mapping] gmapping 패키지를 사용하여 지도생성.</small>
ROS2 환경에서 Slam 패키지로 많이 사용되는 slam toolbox 를 사용하여 지도생성

### 최종 맵 파일
![robot](./assets/img/posts/2023/20230505/B2011_2023-05-07-4.jpg)
<small>[pgm 파일] 최종 지도 파일 pgm yaml.</small>
지도를 생성하고 최종 지도파일을 저장하여 활용 pgm, yaml 파일

### rviz 확인
![로봇모델](./assets/img/posts/2023/20230505/Screenshot from 2023-05-09 07-49-21.png)
<small>[로봇모형] 3d 로봇 모형.</small>
urdf 파일 형태의 로봇 3D 형상파일 로딩

![rviz](./assets/img/posts/2023/20230505/Screenshot from 2023-05-09 07-50-05.png)
<small>[센서사진] Lidar, IMU TF, camera image visualization .</small>

### 기타
![로봇사용](./assets/img/posts/2023/20230505/20230505_225245.jpg)
<small>[충전] 전용 충전기를 사용하여 로봇 충전.</small>