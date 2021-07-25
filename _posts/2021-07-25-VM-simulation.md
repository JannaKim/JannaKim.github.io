---
layout: post
title:  "vm simulation"
excerpt: "reviews"


categories:
  - Blog
tags:
  - [Blog, jekyll, Github, Git]

 
date: 2021-07-25
last_modified_at: 2021-07-25
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


<li> 스택의 함수별로 base address 가 있다.
    포인터 주소들은 이 함수에서 리턴하는 기본 주소에서 얼마나 떨어진지 상대 주소로 표현된다. 

<br/>



<li> 메모리 사이즈가 4byte 라면? 
    32bit로 주소를 표현할 수 있다는 뜻이다
    2^32 = 2^2*2*30 = 메모리 용량은 4GB

    명령어마다 실제 사이즈와 관련없이 8byte를 할당받는다면, 

    명령어 한줄이
    int a = 10이라면
    0x000000000000000A 가 메모리 주소 안에 들어가야하고, 그래서 8byte 를 쓴다는 것이다.

    그럼 메모리 안에 선언할 수 있는 변수의 개수는 2^29개가 된다.


<br/>



<li> 힙과 스택의 base address 는 어디서부터 놓으면 될까?

    운영체제마다 다르지만, 리눅스는 
    0x00000000 다음으로 데이터영역, 코드 영역등이 먼저 위치하고
    다음에 힙이 작은 주소부터 위로 올라간다

    스택은, 주소공간 끝주소에서 커널 데이터 와 동적 링크 라이브러리들 다음으로
    큰 주소에서 내려온다.


<img width="515" alt="image" src="https://user-images.githubusercontent.com/74404132/126906468-f0dd8d60-6021-4c42-9095-14ba09cc6f4c.png">


<br/>



<li> 스택은 LIFO구조이고, 아래 어셈블리어에서 보이듯 함수별 base address 기준으로 n칸씩 이동한다.
8byte 씩 이동하려면 어셈블리어 상에선 몇칸씩 점프하는 걸까?

<img width="418" alt="Screen Shot 2021-07-26 at 1 29 32 AM" src="https://user-images.githubusercontent.com/74404132/126906316-2021bac6-28ad-4401-9616-f33a37fd8a06.png">



힙 영역에 변수가 할당되면, 스택에 그 해당주소에 실제 값이 저장된다.

<br/>



<li> 모든 프로그램은 실행 이전에 컴파일러 프로그램이 먼저 실행되고,
컴파일러가 고수준 언어를 저수준 언어로 변환해준다.

모든 변수명은 주소로 변환된다!

<br/>



<li> 컴파일러는 변수들을 지정 주소들로 어떻게 변환될끼?

    이미 쓴 변수의 주소를 확인하기 위해 위에 변수들을 일일이 다 체크하는 것인가?
    아니다. 해싱기법을 사용하고, 힙 메모리에 만들어준 심볼테이블을 참고한다.

<br/>



<li> 심볼테이블이란?

    컴파일시 object files에 저장되고 디버깅 할때 "컴파일러 주소공간" 메모리의 "힙" 에 로드 된다. (코드가 당연히 string이라 힙에 로드되는거고 컴파일러도 프로그램이니 "컴파일러 프로그램"의 힙 공간에 심볼테이블이 로드되는것이고, 기계어로 바꿔주는 이 컴파일러가 쓰는 변수들을 미리 다 주소로 변환시켜놓는 것이다.)그니까 우리가 돌리는 프로그램에는 논리주소에 변수 관리 용으로 변수별 주소만을 명시한다! 코드데이터의 코드가 기계어로 저장돼있으니 주소로 써논 변수들을 갖다 쓰기만 하면 된다! 즉 프로그램 메모리에는 내가 사용할 변수의 메모리 위치를 알려주는 심볼테이블 같은게 필요 없다!

    운체 전공책 내용상 논리주소는 print 등 시스템 콜을 위한 운영체제 코드를 제외한 메모리들을 뜻하지만 (논리주소란 사용자 영역이 "시작되는" 번지를 0번지로 변경해 사용하는 주소방식이라고 한다) 이 부분도 매우 명확히 할 수는 없을 것 같다. 운체 책 기준의 리눅스는 0xC0000000 ~0xFFFFFFFF 논리주에 커널용도 있다. 그외 논리주소는 stack heap code data 외에 라이브러리 참조 메모리등 알파로 더 가지고 있으니, "스택, 힙 "메모리가 0x00000000 ~ 0xFFFFFFFF를 모두 쓰는 게 아니다. 즉 운영체제 세가지 이야기 전공책 기준 (32 bit 컴 기준)은 힙이전에 다른 영역들이 있으니 힙의 시작을 0x00000000로 표기하는건 맞지 않고, 또 한 프로세스의 논리 주소 공간을 그릴때 0xFFFFFFFF 쪽 부분에 커널 코드가 저장 돼 있는 걸 보니 스택 메모리의 시작을 0xFFFFFFFF으로 찍는 다는건 정확히하자면 아닌 것이다. 하지만 운영체제마다 논리주소 메모리를 어떻게 관리하는 지 다를 수 있기에 무조건 저렇다라고 말하는 건 위험한 발언이다 .
