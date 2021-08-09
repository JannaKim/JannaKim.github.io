---
layout: post
title:  "flutter download"
excerpt: "reviews"


categories:
  - Blog
tags:
  - [Blog, jekyll, Github, Git]

 
date: 2021-08-01
last_modified_at: 2021-08-01
---


운영체제
 
OS는 시스템 운영에 있어서 중계자의 역할을 한다. OS는 중계자의 위치에서 리소스를 안정적이면서 효율적으로
사용할 수 있게 관리하고, 응용 프로그램이 리소스를 쉽게 사용할 수 있도록 서비스도 제공한다.
응용 프로그램이 리소스 사용을 원할 때는 우선 OS 에게 리소스 사용에 관한 권한을 요청한다.
그러면 OS 는 현재 시스템의 상태를 파악한 후에 권한을 넘겨줄 지 결정하는데, 그 권한은 언제든지 OS 가 되찾아 올 수 있다. 그 이유는 다른 응용프로그램도 같은 리소스의 사용에 관한 권한을 요구할 수 있기 때문이다. 
응용 프로그램이 OS로부터 권한을 요청할 수 있는 구조로 만들려면 OS와 소통할 수 있게 해야한다. 
이런 구조를 만들기 위해 OS에서 제공하는 함수 API가 만들어 졌다. 
 
 
사용자가 하나 이상의 프로그램을 동시에 실행시키길 원하는 요구사항에 맞춰야 했다. 운영체제는 CPU를 가상화해서 이런 환상을 만들어 낸다. 이에 맞춰 시분할의 개념이 등장하였고
시분할 기법은 CPU를 공유하기 때문에, 각 프로세스의 성능은 낮아진다. 


멀티태스킹은 다수의 프로그램들이 메모리에 로드되고 동시에 실행하는 것이다.
이는 더 강한 조종장치와 분할 기법이 필요해졌다. 그래서 프로세스의 개념이 나왔다. 
## CPU 가상화의 효율적 구현을 위해서는, 도구(mechanism, 예: 문맥교환)와 지능(policy)이 필요하다

다수의 운영체제들이 공통적으로 체택하고 있는 설계 패러다임은 정책과 메커니즘의 분리이다.
메커니즘: 어떻게 (어떻게 문맥 교환을 하는가)
정책: 어느것을 (지금 당장 어느 프로세스를 실행시켜야 하는가)

        운영 체제의 스케쥴링 정책은
        1. 과거 정보(1분 동안 어떤 프로그램이 자주 실행되었는지)
        2. 워크로드에 관한 정보(어떤 유형의 프로그램들이 실행되었는지)
        3. 성능 측정 결과(단이 시간당 처리량, 응답시간)

멀티 프로그래밍: 시스템 자원(CPU, memory, peripheral devices)이 효율적으로 이용되는 환경을 제공한다.
CPU가 idle 한 시점이 존재하지 않게 jobs 들을 organize 하는 것이다.
"program과 user interation 을 위한 환경 자체를 제공하진 않는다"
 = 실시간 소통

시분할이 멀티프로그래밍을 실행 가능하도록 도입된 개념이다. 
time sharing( = muli tasking) 이 CPU가 여러개의 job 들을 아주 빠른 시간단위로 스위칭해서 
user interact 가 일어나도록 하는 것이다.
 
job scheduling?

the jobs are kept initially on the disk in the job pool.
This pool consists of all processes residing on disk awaiting allocation of main memory


<img width="1046" alt="image" src="https://user-images.githubusercontent.com/74404132/127819454-26f6c528-9db5-4976-821c-770593729dee.png">

선택된 프로세스에서 메모리 많이 사용하면 mid-term scheduler 가 해당 프로세스 용 메모레를 swap in, swap out 시킨다. 

프로세스
 
프로세스(Process)는 CPU가 처리하는 작업(Task)라고도 불리며, 실행중인 프로그램을 의미한다. 좀 더 구체적으로 디스크에 저장되어 있던 실행 가능한 프로그램이 메모리에 적재되어 운영체제가 관리하는 상태를 의미한다.

프로그램은 디스크 상에 존재하며 실행을 위한 명령어와 정적 데이터의 묶음이다.

프로세스 API: 운영체제가 반드시 API로 제공해야 하는 몇몇 기본기능

생성(Create) : 운영체제는 새로운 프로세스를 생성할 수 있는 방법을 제공해야 한다.
쉘에 명령어를 입력하거나, 응용 프로그램의 아이콘을 더블-클릭하여 프록램을 실행시키면, 운영체제는 새로운 프로세스를 생성한다.




        프로세스를 관리하는 자료구조에 대해 학습한다.

    프로세스의 구성 요소를 이해하기 위해서 하트웨어 상태를 이해해야 한다. 프로그램이 실행되는 동안 하드웨어의 상태를 읽거나 갱신할 수 있다. ex) 메모리, 레지스터
    명령어, 읽고 쓰는 데이터 등이 메모리에 저장된다.

    프로세스가 접근할 수 있는 메모리를 주소공간(address space) 이라 부른다. 


    프로세스 하드웨어 상태를 구성하는 레지스터 중에는
    1. PC(IP): 다음에 실행할 명령어 주소

    2. IR: 현재 수행중인 명령어

    3. 스택 포인터, 프레임 포인터: 함수의 변수와 리턴 주소를 저장하는 스택을 관리할 때 사용하는 레지스터


    프로그램은 영구 저장장치에 접그하기도 한다. 이 입출력 정보는 프로세스가 현재 열어 놓은 파일 목록을 갖고 있다. 



        프로세스와 스레드의 관계에 대해 학습한다.
        운영체제에서 사용하는 작업 스케줄링 알고리즘에 대해 학습한다.


메모리 역할
 
메모리는 실행할 프로그램을 저장하고 있고, 읽고 쓰는 데이터를 쓰기도 한다.
 
 
학습거리) 폰 노이만 구조와 하버드 구조에 대해 학습한다.
 
 
프로세스 메모리 구조
 
프로세스가 메모리에 locate될 때 구조는 다음과 같다. 각 영역별로 어떤 의미가 있고 어떻게 구분되는지 확인한다.


프로세스 스케줄링

프로세스 상태

생성 -> 준비 -> 실행 <-> 대기 -> 종료까지 크게 5가지 상태가 있다.

프로세스를 생성해서 계속해서 실행하지 않고, 다른 프로세스를 실행하는 동안 대기했다가 다시 실행하는 순서를 반복하게 된다.



이미지 출처 : 프로세스 관리 참조 https://wiki.kldp.org/wiki.php/ProcessManagement


스레드

경량 프로세스 Light Weight Process라고 프로세스에서 실행 제어만 분리해서 처리하는 단위를 만들었다. 스레드는 같은 그룹의 스레드와 코드, 메모리 주소 공간, 운영체제 리소스를 공유한다. 프로세스는 하나 이상의 스레드를 가지고 각 스레드는 다음 같은 동작을 담당한다.

스레드 실행에 대한 상태 관리

실행을 위한 별도 스택

지역 변수와 스레드 특정 데이터를 저장하는 데이터 저장소

프로세스의 메모리와 자원에 대한 접근을 기록하는 컨텍스트 정보


Multi-threading will typically improve speed when/if it allows concurrent use of resources, some of which would otherwise be sitting idle at least part of the time.

For example, if you have a process that reads some data from disk, does a lot of processing on it, then writes results back to disk, you may well be able to gain something from doing disk I/O and computation (more or less) concurrently--even on a single core system.

Even in cases like these, you're typically suffering at least a little slow-down in each part of the program individually. Let's assume, however, that you're doing enough processing that it takes about the same length of time as the total of reading and writing.

Disk I/O uses one set of resources almost exclusively, and computation uses a different set of resources, also almost exclusively. Using two threads might add, say, 1% of time of its own, but by doing the Disk I/O and computation concurrently, you get double the speed, minus 1% overhead, so your program takes about 51% as long to run multi-threaded as it would single-threaded.

In your case, however, you're talking about two threads that do exactly the same things, so they compete for use of the exact same resources. This means you've done nothing to speed up the computation itself, and you've added at least some overhead to switch between execution of the two threads. Ergo, the multi-threaded code will almost certainly run slower than the single-threaded code (usually not drastically closer, but a little slower anyway).


이미지 출처 : https://en.wikipedia.org/wiki/Thread_(computing)

특징

스레드를 사용하면 사용자에 대한 응답성을 증가시킬 수 있다.

프로세스 자원과 메모리를 공유할 수 있다.

자원을 공유하기 때문에 경제적이다.

다중 프로세서와 다중 스레드를 혼합해서 병렬 실행이 가능하다.

현대 CPU들은 다중 스레드를 처리하는 하드웨어 로직을 가지고 있다.


학습거리

프로세스나 스레드가 만들어지고 종료될 때까지 스케줄러에 따라서 어떤 상태로 변화하는지 학습한다.

노드 환경에서는 웹 워커(Web Worker)나 워커 스레드(Worker Thread)을 학습한다.


MLFQ : 짧은 작업을 먼저 실행시켜 반환시간을 최적화 한다.
응답시간을 최적화한다. RR로

MLFQ 는 여러 개의 큐로 구성되며, 각각 다른 우선 순위가 배정된다.
실행 준비가 된 프로세스는 이 중 하나의 큐에 존재한다.

큐를 실제로 안놓고 PDB에 저장한다?!

