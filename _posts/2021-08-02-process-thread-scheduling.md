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

시스템 성능 지표들
평균 응답 시간 (mean response time)
사용자 지향적, 예) interactive systems
처리량 (throughput)
시스템 지향적, 예) batch systems
자원 활용도 (resource utilization)
공평성(fairness), 예) FIFO
실행 대기 방지
무기한 대기 방지
예측 가능성(predictability)
적절한 시간안에 응답을 보장하는가
자원 할당의 공정성 보장
단위시간당 처리량 최대화
적절한 반환시간 보장
예측 가능성 보장
오버헤드 최소화
자원 사용의 균형 유지
반환시간과 자원의 활용 간에 균형 유지
실행 대기 방지
우선순위
서비스 사용 기회 확대
서비스 수 감소 방지



스케줄링 기준 (Criteria)
스케줄링 기법이 고려하는 항목들
프로세스(process)의 특성
I/O-bounded process : I/O burst > CPU burst
Compute-bounded process : CPU burst > I/O burst
시스템 특성
Batch system or interactive system
프로세스의 긴급성(urgency)
Hard- or soft- real time, non-real time systems
프로세스 우선순위 (priority)
프로세스 총 실행 시간 (total service time)


Long-term Scheduling
Job scheduling
시스템에 제출 할 (Kernel에 등록 할) 작업(Job) 결정
발생 빈도는 적다.
Admission scheduling, High-level scheduling
다중프로그래밍 정도(degree) 조절
시스템 내에 프로세스 수 조절
I/O-bounded 와 compute-bounded 프로세스들을 잘 섞어서 선택해야 함
시분할 시스템에서는 모든 작업을 시스템에 등록
Long-term scheduling이 상대적으로 덜 중요하다
 
Mid-term Scheduling
메모리 할당 결정 (memory allocation)
Intermediate-level scheduling
Swapping (swap-in/swap-out)
 
Short-term Scheduling
Process scheduling
Low-level scheduling
프로세서(processor)를 할당할 프로세스(process)를 결정
Processor scheduler, dispatcher
가장 빈번하게 발생
Interrupt, block (I/O), time-out, Etc.
매우 빨라야 함
average CPU burst = 100ms 
scheduling decision = 10ms
10 x (100+10) = 9% 
of the CPU is being used simply for scheduling





스케줄링 정책 (Policy)
선점 vs 비선점
Preemptive scheduling, Non-preemptive scheduling
우선순위
Priority





Priority
프로세스의 중요도
Static priority (정적 우선순위)
프로세스 생성시 결정된 priority가 유지 됨
구현이 쉽고, overhead가 적음
시스템 환경 변화에 대한 대응이 어려움
Dynamic priority (동적 우선순위)
프로세스의 상태 변화에 따라 priority 변경
구현이 복잡, priority 재계산 overhead가 큼
시스템 환경 변화에 유연한 대응 가능





MLQ -> MLFQ

MLQ 단점

Q1
Q2
Q3

위 큐 무조건 먼저

Q2 ~ 배치받은애들은 Q1 항상 다른 애들이 있으면 얘네는 실행되지 않는다
Starvation 

MLFQ



MLFQ?
큐간의 프로세스 이동이 가능하다!

기준: 위나 아래로 이동하는 기준
2. 프로세스가 들어갈 큐를 결정하는 기준 등

Ex) 



SJF  

설명기준: 같은시간에 들어올때

0     100

1      2, 2


SJF 비선점/ 선점 PSJF (STCF)

비선점 기준 : 어떤일이?
Convey effect 

장점: 평균 반환시간이 단축된다 !!!!



https://www.netinbag.com/ko/internet/what-is-cpu-virtualization.html



    cpu 가상화 : 하드웨어의 도움을 받아 운영체제가 시스템에 매우 많은 수의 가상 cpu가 존재하는 듯한 환상을 만들어 낸 것.
    CPU 가상화를 멀티 태스킹 또는 하이퍼 스레딩과 혼동해서는 안됩니다. ??


멀티태스킹은 운영체제가 CPU에 작업을 줄 때 시간을 잘게 나누어 배분하는 기법이다. 
멀티 태스킹은 한 번에 둘 이상의 응용 프로그램을 실행하는 작업입니다. 모든 최신 운영 체제에서는 단일 CPU에서이 작업을 수행 할 수 있지만 기술적으로 특정 시점에 하나의 응용 프로그램 만 처리됩니다. 하이퍼 스레딩은 호환되는 CPU가 동시에 두 가지 작업을 수행하는 방식으로 특수하게 작성된 응용 프로그램을 실행할 수있는 곳입니다.





     현대의 운영체제는 시분할 방식을 기본으로 사용하기 때문에 프로세스가 여러 상태를 오가며 실행된다.
    준비 상태에 있는 여러 프로세스 중 다음에 실행할 프로세스를 선정하는 일은 CPU 스케쥴러가 담당한다. 

    문맥: 메모리의 코드, 데이터, 스택, 범용 레지스터 내용, PC, 환경변수, 열려있는 파일의 식별자

    운영체제 커널은 문맥전환을 사용해서 멀티태스킹을 구현하고 있다.

    문맥은 선점된 프로세스를 다시 시작하기 위해서 필요로 하는 상태이다. 

    스케쥴했다: 커널이 실행할 새 프로세스를 선택했다. 

    문맥전환: 저장, 복원, 제어전달

    문맥전환은 커널이 사용자를 대신해서 시스템콜을 실행하고 있을 때, 인터럽트의 결과로 발생할 수 있다.
    타이머 인터럽타 1ms~ 10ms


        엑세스 속도와 용량의 관계
      1. (CPU)레지스터 - 가장 빠름
      2. (CPU)캐시 메모리
      3. (내부)메인 메모리
      4. (외부)하드디스크 - 가장 느림, 가장 용량이 큼

         CPU는 입출력 관리자에게 작업 지시를 내리고 다른일을 하다가 완료신호를 받으면 하던 일을 중단하고 옮겨진 데이터를 처리한다.
    이때 입출력 관리자가 CPU에 보내는 완료 신호를 인터럽트라고 한다



        17. 스케쥴링:
    CPU 스케쥴러응 프로세스가 생성된 후 종료될 때까지 모든 상태 변화를 조정하는 일을 하며, CPU 스케쥴링은 CPU 스케쥴러가 하는 모든 작업을 가리킨다.

    스케쥴링 목적:
    공평성, 효율성, 안정성(즁요프로세스 먼저, 보호), 확장성(프로세스 증가), 반응시간 보장, 무한 연기 방지



    concurrency 동시성: time sharing

    폰 노이만 구조'의 특징은 CPU가 어느 한 순간에 딱 하나의 연산(계산)만 수행할 수 있다는 점이다. 전자공학이 눈부시게 발전해옴에 따라 CPU의 용량과 처리속도가 늘어나고, 사람이 인식할 수 없을 정도로 빠르게 계산을 할 수 있게 되면서, 사람을 살짝 속이는 시분할 방식의 멀티태스킹을 사용하게 되면서 컴퓨터가 동시에 여러가지 일을 하는 것 같은 착시가 생긴 것 뿐이다. 이 멀티태스킹은 한편으로 컨텍스트 스위치(Context Switch)라는 성능 저하를 가져오지만, 너무 빨라진  CPU 덕분에 무시할 수 있을 정도가 되었다.



    선점형 비선점형

    선점형: 프로세스가 CPU를 독점할 수 없어 시분할 시스템에 적합하지만 문맥교환 : 시분할 방식 스케쥴러
    비선점형: 기다리는 프로세스가 많아 처리율이 떨어진다 : 일괄 처리 방식 스케쥴러

    HRN 스케쥴링: 우선순위 = (대기 시간 + CPU 사용시간) / CPU 사용시간

    아사현상 해결

    [스케쥴링들 평가]

    1. FCFS : convoy effect 일어난다.(뒤의 작업이 자연됨), 비선점형이라 CPU idle 시분할 시스템에서 프로세스의 상태를 따지는 거다
        공정o 반환 good 응답 x

    2. SJF : 사용자와 상호작용이 없는 옛날엔 전체 연산 개수 안았는데, 현대 프로세스는 프로그램 종료 시간 파악하기 어렵다. 추청못함
        공정x : starvation
        한계가 있지만 aging으로: 예시로 세살만 먹으면 비키도록
        SRT(STCF) 선점형 SJF : 남은 시간 주기적으로 계산, 여전히 아사


    3 HRN: '여전히' 공정성 위배 ** (대기 시간 + CPU 사용시간) / CPU 사용시간

    * 4. RR: 우선순위가 적용되지 않은 가장 단순한 선점형 스케쥴링 타임슬라이스 정하는 게 중요하다
      convoy, starv 없음
      응답시간이 좋다
      반환시간 기준에서는 성능이 나쁘다
      유형의 절충

  멀티 스레드 환경에서의 필요성

  멀티 스레드 환경에서 하나의 스레드가 CPU를 독점하는 상황과 다른 스레드가 실행되지 못하고 무한정 기다리는 '기아' 현상을 막기 위해 각 스레드에 적절한 CPU 사용 시간을 부여하여 모든 스레드가 순환적으로 실행되도록 하는 것


    유닉스 운체는 10~200 밀리초 사이에 조정할 수 있도록 한다 MLFQ 사용하기 때문

    5. 우선순위 스케쥴링: 선점 비선점 모두 적용가능, 고정, 변동이 있다
      공정성 위배: 아사현상

    6. MLQ: 아사현상

    * 7. MLFQ: 아사현상 해결: 큐간이 프로세스 이동이 가능한 것, 오늘날의 CPU 스케쥴링을 위해 일반적으로 사용하는 방식

    규칙 5가지:
    우선순위별로
    같으면 rr
    처음 들어가면 1번큐
    배정 시간 소진하면 우선순위 감소시킴
    일정 주기 지나면 최상위큐로 옮김


    8. lottery scheduling: 더 자주 수행돼야하는 애한테 당첨 기회를 많이주는 것
    추첨권 양도: 클라이언트 서버 환경에서 특히 유용하다!
    사진

    구현이 단순하다

    9. 보폭 stride 스케쥴링
    얼마나 CPU 사용했는지 추적

    10. 리눅스 CFS 장점: 효율성과 확장성

    스케쥴러이 효율성이 전체 시스템의 성능에 매우 중요한 성능을 갖는다
    스케쥴러가 전체 데이터 센어 CPU 사용량의 5%, 스케쥴링의 오버헤드를 최대한 줄이는 게 스케쥴러의 목표이다

    vruntime : 보폭스케쥴링
    최소 타임 슬라이스. 


멀티쓰레딩 혹은 멀티프로세스를 할 때 스케쥴링 기법에 대해 설명하시오

Windows계열을 게임서버로 쓰는 이유로는.. 클라이언트가 거의 대부분 Windows기반으로 개발하니 같은 조건이라면 서버도 Windows로 하는 게 일관성도 있고 편하겠지요.
주로. 윈도우 nt 기반

왼도우는 우선순위 + RR 적절히 혼용


게임 서버와 게임 클라이언트는 그 목적과 역할이 정 반대이다.

게임 클라이언트는 화려한 그래픽과 무거운 용량을 자랑한다. 게임 클라이언트는 사용자에게 극대화된 수준의 그래픽 연출을 보여주기 위해 컴퓨터 하드웨어의 성능을 극한으로 남김 없이 사용해야 한다. 그렇기 때문에, 제아무리 좋은 컴퓨터를 사용해도 쿨링팬이 굉음을 내며 돌아갈 수밖에 없다.

게임 클라이언트는 최대한 화려한 것을 사용자에게 보여줘야 한다. 하지만 게임 서버는 아무리 보여줘 봤자 '랙' 아니면 '서버 다운'뿐이다. 즉 잘 만들어진 게임 서버일수록 그 존재를 드러내지 않아야 한다. 아마도 궁극적인 경지에 오른 게임 서버는 그 자체를 아무도 느끼지 못하는 수준이 아닐까?

앞 편에서 언급했듯이, 게임 서버는 화면에 보여주는 것 없이 뇌 역할을 한다. 그러다 보니 게임 서버의 실행 모습은 클라이언트와 달리 무척 밋밋하게 생겼다. 프리 서버를 써본 독자들은 알겠지만 (웬만하면 그 프리섭이라는 것은 즉시 갖다 버리길 권장한다. 매우 위험한 물건이다.) 프리서버는 화면에 보여주는 것이 무척 밋밋한 프로그램이다.


게임 서버는 'Daemon'이라고 불리는 상태로 작동한다. 

게임 서버가 구동되는 운영체제는 우리가 일반적으로 쓰고 있는 윈도(Windows)가 아니다. 윈도 서버(Windows Server)나 리눅스(Linux)라고 불리는 특수 목적의 서버 운영체제에서 게임 서버를 실행하는 경우가 일반적이다.




스케쥴했다: 커널이 실행할 새 프로세스를 선택했다. 


문맥: 메모리의 코드, 데이터, 스택, 범용 레지스터 내용, PC, 환경변수, 열려있는 파일의 식별자

   문맥전환: 저장, 복원, 제어전달



￼





1. FCFS : 오는 시간 순서대로 비선점형 큐

단점 : convoy effect. (응답시간)
장점: “””””””” 공정 “”””””””””      반환성 좋음

* convoy effect : 뒤의 작업이 자연됨


앞 에께 1년짜리면 뒤에 애들이 당하는 게 convoy :  (( 영원히 안되는 게 아님 )) 

대기 시간이 길어져  < CPU 사용 효율 > 이 감소하는 현상 ??
대기 반환 시간 계산할때
AWT가 길어지니까 얘를 기준으로 CPU 사용 효율을 따지 때문

지금도 쓰인다 어디에? 큐 

시간도 nlogn 차이나니까

공정함을 보장해야하는 프로그램은 얘를 쓸 수밖에 없겠다.





2. SJF : 빨리끝나는 순서별로 (비선점)

사용자와 상호작용x

이 당시에는 전체 연산 개수 알 수 있었음


현대 프로세스 : 사용자와 상호작용 o

프로그램 종료 시간 파악하기 어렵다. 추청못함


* 단점 : “”””””””””” 공정 x “”””””””””””  : 기아현상 이 있음
* < CPU 사용 효율 > 이 감소하지는 않는다!


기아현상의 정의: 너무오랜 세월?   (( 영원히 안 될 수 있음 ))
우선순위가 밀림

		

공정 <-> 기아현상 starvation

Convoy 해결하기 위해 SJF 등장했는데 starvation이 생겼다


STCF 선점형 SJF: 시작시간 다를때



3. HRN : (대기 시간 + CPU 사용시간) / CPU 사용시간 : 선점 새치기 안됨
Highest Response ratio Next)


‘여전히' 공정성 위배.    “ 공정성 “ ??? !










반환시간 : 모든작업을 완료하는 시간 아래에서부턴 반환시간 ‘만’ 느림
반환시간 기준에서는 성능이 나쁘다





4. RR: 대표적인 선점형 스케튤린 타임슬라이스 

convoy, starv 없음
응답시간이 좋다


유형의 절충

얘는 “원형큐”다! 타임 슬라이스 잘라노면 맨 뒤로 가니까





멀티스레드에서 유용하니까. 타임슬라이스 이용해서 기아 막아주니까 time quantum
RR 을 쓰는 이유 : 오는 순서대로, 타임 슬라이스를 사용

  멀티 스레드 환경에서의 필요성 멀티 스레드와 직결되는 첫 스케쥴링

  멀티 스레드 환경에서 하나의 스레드가 CPU를 독점하는 상황과 다른 스레드가 실행되지 못하고 무한정 기다리는 '기아' 현상을 막기 위해 각 스레드에 적절한 CPU 사용 시간을 부여하여 모든 스레드가 순환적으로 실행되도록 하는 것




5. 우선순위 스케쥴링: 선점 비선점 모두 적용가능, 고정, 변동이 있다
      공정성 위배: starvation 타임슬라이스가 없다!


  6. MLQ: starvation 여러 큐 사용하는 방식

위에 있는 큐 순서대로 니까


위에는 순서를 바꾸는 규칙이




7. MLFQ 규칙 5가지


  0. 처음 들어가면 1번큐
 0.5   배정 시간 소진하면 우선순위 감소시킴



1. 우선순위별로 위에 있는 큐 순서대로 니까
2. 우선순위가 큐가 같다면 ?  같으면 rr
3. 일정 주기 지나면 최상위큐로 옮김 


그래픽스, 게임 에이스타 길찾기 :







8. Lottery 100 더 자주 수행돼야하는 애한테 당첨 기회를 많이주는 것

두개의 프로세스 1~70 / 71~100

7: 3

45 

추첨 스케쥴링은 타임 슬라이스가 끝날 때마다 확률 기반으로 달성한다


구현단순



9 보폭 stride 스케쥴링
얼마나 CPU 사용했는지 추적

￼






10. 리눅스 CFS vruntime 80% 


 장점: 효율성과 확장성




11. 윈도우는 우선순위 + RR 적절히 혼용

윈도 서버(Windows Server)









HRN


RR

MLFQ

Lotter

Stride

리눅스 CFS


윈도 의 스케쥴링



* MLQ, MLFQ 는 RR 기반이다 ! 
낮은 큐는 FCFS
각 큐는 독립된 스케쥴링 법칙을 갖고 있다

기본적으로 얘네 둘의 디폴트는 RR이다