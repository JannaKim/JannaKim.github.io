---
layout: post
title:  "vm implementation"
excerpt: "reviews"


categories:
  - Blog
tags:
  - [Blog, jekyll, Github, Git]

 
date: 2021-07-21
last_modified_at: 2021-07-21
---


<p>
사용자 영역이 운영체제 영역으로 침범하는 것을 막으려면 하드웨어의 도움이 필요하다.
CPU 내에 있는 경계 레지스터가 담당한다.
경계 레지스터는 운영체제 영역과 사용자 영역 경계 지점의 주소를 가진 레지스터이다.
메모리 관리자는 사용자가 작업을 요청할 때마다 경계 레지스터의 값을 벗어나는 지 검사하고, 만약 경계 레지스터를 벗어나는 프로세스를 요청하는 프로세스가 있으면 그 프로세스를 종료한다.
</p>
<p>
메모리 관리자는 절대 주소를 사용하지만 사용자 입장에서 절대 주소는 불편하고 위험하다.
절대 주소를 사용하면 매번 운영체제 영역을 왁인해야 하기 때문이다.
</p>

상대 주소는 사용자 영역이 시작되는 번지를 0번지로 변경해 사용하는 주소 지정 방식이다.


<p>
메모리 최적화?
프로그램의 동작 속도를 높이거나 프로그램의 사이즈를 줄이는 것
</p>

<p>
gcc 컴파일러

    -o , -o1 : 코드의 사이즈와 실행 시간을 줄인다.
    -o2 : 몇개 알고 제외하고 푀적화 수행
    -o3 : -o2 보다 더 많은 알고리즘사용, 컴파일 시간 느려짐
    -o0 : 최적화를 수행하지 않아 컴파일 시간이 빠르며 기본 옵션으로 사용된다
    -os : -o2에서 사용하는 알고리즘을 사용하되 코드의 사이즈를 최소화시키는 것에 중점을 둠
</p>

<p>
메모리 영역 4가지

프로그램 코드는 크게 변수와 함수 그리고 연산 기호들로 이루어져 있다.
폰 노이만 구조에서는 이러한 데이터 명령어들이 하나의 메모리에 분리된 영역을 가지고 있다고 했다.

프로그램 코드 중에서,
<li> +, -, = 등의 연산 기호와 명령어 : Code Area </li>
<li> 전역 변수 및 데이터 : Data Area </li>
<li> 지역 변수 및 함수 실행 : Stack Area </li>
<li> 메모리 할당 : Heap Area</li>


Data Area : 변경이 가능한 데이터를 사용할 목적.
static 은 Code Area

 </p>


<img width="552" alt="Screen Shot 2021-07-22 at 1 24 32 PM" src="https://user-images.githubusercontent.com/74404132/126589821-2a51196c-22d1-4c04-ab6d-ef3613c7952d.png">

Stack LIFO 어떻게 구현? 순차적으로 쓰고 순차적으로 읽어내는 방식

Heap : 일부 영역을 원하는 만큼 할당 받아 사용하고, 사용한 후에 반납하는 형태

    The STACK area is characterized by the order of each data.
    The characteristics of the HEAP area are randomly stored for each data.

힙 영역을 OS 가 관리한다.


## JS engine

    The main function

    Compile: Translate the JS code as the bytecode or machine code that the machine can execute

    Optimization: Rewinding the code, making it more efficient

    Execute: Perform the above-mentioned bytecode or machine code

    Garbage Recycling: Recycling the memory of JS to use, and use it again

  </p>

  Execute JS code

    Ready to work

    Provide API: Window / Document / SetTimeout

    These features are the features provided by the browser, not the functionality they have.

    These features are called Runtime Environment

    JS code will run in memory

</p>



</p>

    Data is divided into two: non-objects and objects (only numbers, strings, Boole is not object)

    Non-object presence STACK district
    Object exists HEAP area
    = I always copy the right thing to the left (there is no pass value and address)

  
</p>

      Object

    Var person = {} is equivalent to var pers = new object ()

    Array

    VAR A = [1, 2, 3] is equivalent to VAR A = New Array (1, 2, 3)

    function

    Function f () {} equivalent to var f = new function ()

    The latter is formal writing, but it is not easy to use


구현:
<img width="564" alt="Screen Shot 2021-07-22 at 2 53 40 PM" src="https://user-images.githubusercontent.com/74404132/126595276-50b7043c-8d8f-4575-9313-0441ee3e7d3e.png">

과 코드 한줄 씩 추가.


<img width="411" alt="Screen Shot 2021-07-22 at 4 40 16 PM" src="https://user-images.githubusercontent.com/74404132/126604768-9f691560-71d8-42f3-92e5-8981b93366e2.png">



![KakaoTalk_Photo_2021-07-22-16-56-01](https://user-images.githubusercontent.com/74404132/126606492-bf5f19ca-ccd1-493f-9432-2290a2b262a8.jpeg)

line 계속 받아서 채워 넣는다.

heaptop pointer
stack pointer



가비지 컬렉션의 작동 원리(Mark-Sweep)

사실 Heap 내부에는 세 개 이상의 가비지 컬렉션이 존재하고, 각각 다른 내부 알고리즘을 사용하여 메모리를 최적화시킨다.

여기에서는 가장 흔히 알려진 Mark-Sweep 알고리즘을 통해 가비지 컬렉션의 작동 원리에 대해 간단히 알아본다.

Mark-Sweep 알고리즘은 우선 roots라는 root 객체의 집합을 만들어 낸다. JS에서 roots는 전역 변수들이다. 그리고 주기적으로 roots로부터 접근 가능한 모든 객체들을 돌아다니며 Marking한다. Marking이 끝나고 메모리 내에 Marking이 되지 않은 데이터들은 사용하지 않는 데이터로 판단해 지워버린다.(Sweeping)

이것이 Mark-Sweep 가비지 컬렉션의 기본적인 동작 원리이다.



하드웨어 인터럽트
소프트웨어 인터럽트 (Trap)
Exception
프로그램이 허용되지 않은 연산을 수행하려 할 때
System Call
사용자 프로세스가 특권 명령을 수행하려 할 때

스택 오버플로우는?


VM 의 목표 세가지:
투명성
효율성
보호


인터럽트의 동작 원리도 함수와 유사하다.

A프로그램이 CPU를 할당받아 수행 중 인터럽트 발생
A는 현재 수행중인 명령의 위치를 저장
OS 내부 인터럽트 처리 루틴으로 들어가 처리
A의 작업 지점부터 다시 수행
일반적으로 프로그램 내에서 함수 호출에 필요한 복귀 주소는 각 프로그램에 스택 영역에 보관한다.

반면, 인터럽트 때문에 CPU를 선점당해 저장하는 복귀 주소는 OS kernel 영역에 존재한다.

이 주소를 저장하는 자료구조를 PCB(Process Control Block)이라 한다.


프로그램이 CPU에서 명령을 수행하려면 수행하려는 주소 영역이 메모리에 올라가 있어야 한다.



64bit 운영체제, 32bit 운영체제, 64bit CPU, 32bit CPU 과 같은 개념들이있다.


64bit CPU란 기본 데이터 처리 단위가 64bit, 즉 8byte 란 뜻


명령어 한줄이 8byte? 64bit CPU 상으로 생각해서.

8개의 이진수 : 0~127 숫자 표현



