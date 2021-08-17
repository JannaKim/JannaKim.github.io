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

두 프로세스의 각 CS를 방이라고 생각하면, 한 사람이 어떤 방이든 들어간 시점에는 어떤 사람도 다른 방에 들어가면 안된다.

watchman이 token을 하나 가지고 있는데, 방에 들어가려하는 사람에게 그 token을 준다. 다른 사람이 방에 들어가려하면, watchman이 줄 token이 없으므로 기다리라고 한다.

임계영역에 들어가 있는 다른 프로세스가 있을때, 우리는 다른 프로세스들의 임계영역 코드부분이 CPU에게 fetch 되지 않게 해야 한다.

CS 앞에 entry section 을 놓고, 뒤에 exit section 을 놓는다.

CPU 가 임계 영역 코드를 fetch 하기 전에 entry section code 를 fetch 하게 한다.

entry code section 은 임계영역에 다른 프로세스가 들어가 있는지 token을 가지고 알려주는 코드이다.

만약 다른 프로세스가 안에 들어가 있음이 확인되면, CPU가 march further 할 수 없게 entry section code이 막는다.

한 프로세스가 임계영역에서 나오면, exit section code 가 watchman이 token 다시 가져가도록 해준다.

Synchronization Mechanism : CS 앞뒤로 entry section, exit 넣는 것이다.

이 두 섹션의 코드를 어떻게 작성하느냐에 따라 synchronization mechanism 방법이 다른 것이고, 각자 장단점이 있다.

어떤 mechanism이 나은지 평가하는 방법은 세 기준에 의거한다.

1. mutual exclusion
2. progress
3. bounded waiting

1. mutual exclusion 의 정의는 하나 이상의 프로세스가 동시에 임계영역에 들어가지 않는 것이다.

문맥교환은 어느 시점에서든 일어날 수 있다.

어떤 문맥교환으로 실행되든, 하나 이상의 프로세스가 동시에 임계영역에 들어가지 않으면 상호배제가 만족된 것이다.

2. non-critical section에 있는 P가 다른 P들을 CS에 들어가지 못하도록 막는 일이 없어야 한다.

3. 전체가 while로 둘러싸여 있을 때, P 마다 CS 에 접근하는 횟수를 제한시켜야 starvation 이 일어나지 않는다.

limit 은 항상 거는 게 아니라, 다른 P가 CS에 진입하고자 하는 desire 을 표현했을때 거는 것이다. = entry section 에 들어갔을 때.

entry section 은 다른 P 가 CS에 들어있는지 검사해줄 뿐만아니라, CS 에 들어가고자 하는 P가 있는지도 확인해줘야 한다.


### Synchronization with lock variable and its advantage

![image](https://user-images.githubusercontent.com/74404132/129772583-d0f04d8a-580d-4171-9f57-bcf7cb27df3e.png)

Place while (lock != 0); lock = 1;

in all entry section above each P's CS.

![image](https://user-images.githubusercontent.com/74404132/129772772-819c86f2-56aa-47b4-816a-ecde8c71f119.png)

Place lock = 0; a single line of code beneath each P's CS.

Considter all 3 Ps are going inside the CS.

We will have variable called lock, and it is nothing but a loolean variable.

    Lock variable indicates the number of Ps inside CS, at any point of time.














