---
layout: post
title:  "Network Packet Simulator"
excerpt: "reviews"


categories:
  - Blog
tags:
  - [Blog, jekyll, Github, Git]

 
date: 2021-08-16
last_modified_at: 2021-08-16
---

![image](https://user-images.githubusercontent.com/74404132/129577619-664f7263-ec0e-4631-8bd0-6d4ac7231c4b.png)

TCP/IP : 4계층이라고 많이 한다.

TCP/IP 4계층, OSI 7 계층에서 이메일 프로토콜이 실제로 어떻게 전송되는 지를

가상으로 시뮬레이션 하는 미션이었다.

HTTP / HTTPS 는 분야 관계 없이 잘 알아야 한다.

HTTP 완전 정복 읽기

백엔드에서 구성하는 네트워크 topology 구성도, 등

기초 네트워크가 나와있는 지식들. 학부에서 배우는 네트워크, 정보처리기사 네트워크 지식 + 하드웨어 지식은 꼭 있어야 한다.

HTTP 는 필수적이다.

![image](https://user-images.githubusercontent.com/74404132/129578932-804a6c59-2896-49d6-b203-3420b85d85f5.png)

각 계층의 역할이 왜 이렇게 있는지, 각 계층별로 식별하는 수단

2계층은 MAC address 를 가지고 식별할 수 있고, 1계층은 식별 수단이 따로 존재하지 않는다.

3계층은 IP 계층이기 떄문에 IP로 식별할 수 있다.

5 6 7 계층은 application layer이라 볼 수 있는데, 포트를 가지고 식별할 수 있다.

각 계층별로 데이터를 식별할 수 있는 방법을 생각해봐야 한다.

계층별로 전송되는 데이터의 형식을 공부하자.

우리는 늘 packet 이라 부르지만,

트랜트 포츠 계층에서는 segment, 인터넷 계층에서는 데이타그램이라고 부르고

MAC address로 전송하는 계층은 prime 이라고 부른다.

각 계층에는 하드웨어 장비들이 무엇이 있는가도 생각해보자.

앞 시간에 얘기했던 network topology와 연관지어 

훈이의 시스코 네트워킹 읽기

1계층에는 이더넷 케이블이 1계층 장비다. 네트워크 장비로는 허브.

허브는 네트워크 데이터를 식별할 수 있는 수단이 없다.

2계층에는 스위치 장비가 있다.

3계층에는 라우터가 있다. 라우터는 ip를 가지고 data gram의 수신지 송신지를 식별할 수 있다.

브로드캐스팅은 몇 계층에서 이루어 지는 걸까?

암기보다는 이해를 하자.

![image](https://user-images.githubusercontent.com/74404132/129579767-d5076bd7-5228-441d-a50e-492a4dadfc29.png)

각각의 계층은 다른 계층에 대해서 독립적이다.

제일 위계층, 어플리케이션은 같은 어플레이션들끼리, 각각의 레이어는 보통 자기 레이어끼리 통신한다고 생각한다.

그런데 실제로는, 데이터에 각 레이어에 맞게 패키징을 하고 헤더나 트레일 등, ㅔㄷ이터가 쪼개지기도 한다.

도착하면 포장을 벗겨내다가 원하는 데이터가 나오는 것이다.

각 계층끼리만 살펴보면 마치 자기들끼리만 통신을 하고 있는 느낌이다.

(L1 (L2 (L3 (L4 (L5 (data) ) ) ) ) ) 로 싸서 하나씩 벗기는 것

![image](https://user-images.githubusercontent.com/74404132/129580426-d3dc73b0-7ebe-481e-be5d-c3ae3c26ecfa.png)

