---
layout: post
title:  "Process synchronization summary (KOR)"
excerpt: "reviews"


categories:
  - Blog
tags:
  - [Blog, jekyll, Github, Git]

 
date: 2021-08-14
last_modified_at: 2021-08-14
---

RAM의 모든 프로세스들은, 어떤 segment(stack, heap, code 등) 서로 '직접적으로' 접근할 수 없다.

두 프로세스의 code segement 에 집중해보면, P1의 어떤 값을 P2가 받으려면 
P1이 먼저 실행 됐어야하고 (실행 됐다 = CPU를 할당받아 코드를 실행했다)
protection 개념 때문에 P2는 P1에 직접적으로 접근할 수 없다.

그래서 P1, P2 는 RAM의 다른 곳 (예를 들어 주소 1000) 에 Shared Memory 공간을 생성한다.
이 두 프로세스는 주소 1000에서 소통한다.

주소 1000은 shared memory 이고, 이 공간은 PCB가 아니므로 프로세스들이 '직접' 메모리에 접근할 수 있다.

shared memory 인 주소 1000은 직접 메모리를 로드하는 여러개의 프로세스들이 잇으므로 동기화에 문제가 생긴다.

이 문제들은 Process Synchronization 에 의해 해결된다.

이런 상황에 생기는 문제가 뭔지, 그걸 해결하는 다양한 해결법들이 각각 어떤 장단점을 갖고 있는지 확인한다.

P1 완료 -> P2 시작 이 순차적으로 되면 문제가 없다.


그런데 우리는 pre-emptive scheduling algorithm 을 쓴다.


왜 값 저장에 묹게ㅏ 생겼을까?
공유메모리 때문이다.

선점형 스케쥴링을 쓰고, 동기화 알고리즘을 쓰면 inconsistency 해결할 수 있다.

cnt ++ 는 사실 어셈블리어 상으로 세줄이고, CPU가 명령어를 세번 실행하는 셈이다.

우리는 선점형 스케쥴러를 쓰기 떄문에 CPU 매 단위로 선점당할 수 있다. 

LOAD, INCR, STORE 세 명령어를 cs 라고 부른다. 이외는 remainder section.

cs : shared memory 를 접근 하는 구간이며, 

두 프로세스가 이 구간에서 중간에 선점당하면서 실행되면 맞은 결과가 나오지 않는다.

이렇게 섞여서 실행되는 게 race condition이며, 우리는 이 경쟁조건을 항상 피해야 한다.

임계영역은 잘려서 실행되면 안된다.

임계 영역이란? 실제로 공유 메모리에 접근하는 코드 섹션이다.