---
layout: post
title:  "Linux Activities"
excerpt: "reviews"


categories:
  - Blog
tags:
  - [Blog, jekyll, Github, Git]

 
date: 2021-07-21
last_modified_at: 2021-07-21
---


<br/>

### 운영체제 OS 설계시 시스템의 목표가 잘 정의돼 있어야 한다.

<br/>

목표에 따라 다양한 알고리즘과 전략을 체택하기 때문이다.

리눅스 OS를 까는 것은, 프로그램들이 실행할 수 있는 다른 환경을 만들어 주는 것이다.


OS는 몇가지 주요한 관점에서 바라볼 수 있다.

    1. 어떤 서비스를 제공하는 지
    2. 유저, 프로그래머를 위한 어떤 인터페이스가 제공되는 지
      어떻게 제공되고 어떤 디버깅 방법이 있는지
    3. 구성요소, 상호연결

<img width="526" alt="view of OS" src="https://user-images.githubusercontent.com/74404132/126280676-1946da67-7216-41d2-b91f-7bbf9e0c8866.png">


<br/>
<br/>
<br/>


## 인터페이스란?
  a shared boundary across which two or more separate components of a computer systems exchange information.

<br/>

1. 소프트웨터 인퍼페이스
  운영체제 <-> 응용프로그램(App), App <-> App, App를 구성하는 객체, 클래스, 메소드등이 "서로 커뮤니케이션할 수 있도록 메세지를 주고 받는 방법" 등을 미리 정해 놓은 것.

  API: 응용프로그램 간에 호환이 가능하도록 상호작용을 하는 방법을 정해놓은 것. 즉, API(Application Programming Interface)는 App 간에 데이터를 주고 받는 방법이다.

<br/>


2. 유저 인퍼테이스
  유저들이 컴퓨터와 상호 작용하는 시스템
  interpreters 는 shells 로 알려져 있다.

  CLI(Command Line Interface = command interpreter)
  어떤 OS는 command interpreter 자체에 command를 실행하는 코드가 있다.
  * 유닉스는, implements most commands through system commands!
  즉, 유닉스의 command interpreter는 command를 이해하지 못한다.

  유닉스의 command interpreter 실행 과정:
  rm file.txt
    1. 메모리에 로드시켜 실행할 실행파일 rm 을 찾는다.
    2. 파라미터 file.txt를 가지고 실행한다.

  그러면 command는 file rm code에 그대로 따라서 정의되는 것이다.

  그래서 프로그래머사 파일 만들어서 새 커맨드를 쉽게 만들 수 있다!


## 쉘 

### 1. 쉘 이란? 인터프리터. OS와 대화하는 프로그램


      LINUX standard: bash
      
      Mac : zsh 도 좋다


    Shell(쉘)은 운영체제상에서 사용자가 입력하는 명령을 읽고 해석하여 대신 실행해주는 프로그램이다. 즉 다시말해서, 운영체제의 커널과 사용자 사이를 이어주는 역할을 하며 사용자의 명령어를 해석하고 운영체제가 알아들을 수 있도록 도와주는 명령어 해석기이다. Linux에서 사용하는 Shell의 종류로는 다음과 같은 것들이 있다.
<br/>


    bash : Bourne-Again Shell(프롬프트 : #, 경로 : /bin/bash). 가장 대표적으로 사용.
    sh : Bourne Shell(프롬프트 : $, 경로 : /bin/sh)
    csh : C Shell(프롬프트 : %, 경로 : /bin/csh)
    ksh : Kron Shell(프롬프트 : $, 경로 : /bin/ksh)
    tcsh : TENEX C Shell(프롬프트 : >, 경로 : /bin/tcsh)



        ls -l

        ls -al

        tree/ -L 1 // tree [디렉토리 이름] [-L 깊이]

        mkdir

        cd


        cat
        shell이 fork로 또다른 shell을 만들고, 거기서 exec를 실행한다음 cat을 load하는 것이다.


        less 파일명 // 긴 파일의 내용르 끊어서 표시한다

        q: 종료
        g: 처음으로
        G: 끝으로
        /단어: 문서에서 '단어'를 검색
        space, enter, 화살표, hjkl: 페이지 이동


        history !명령어번호 // 명령어 이력 표시

        cp, mv, rm

        find 디렉토리 -name "파일명"


        touch foo.txt // 0 바이트 파일 생성
  
<br/>

### 2. 쉘 스크립트 
<img width="866" alt="shell scrpit" src="https://user-images.githubusercontent.com/74404132/126279838-1b19e1ec-58ed-4897-842d-1f6ed778de8d.png">


  Shell Script(쉘 스크립트)란 Shell(쉘)에서 사용할 수 있는 명령어들의 조합을 모아서 만든 배치(batch)파일이다. 
  batch interface: there commands and directives to control those commands are entered into files
  즉, 운영체제의 Shell을 이용하여 한줄씩 순차적으로 읽으면서 명령어들을 실행시켜주는 인터프리터 방식의 프로그램이다. Shell Script를 활용하여 원하는 간추린 명령을 만들고 쓸 수 있다.

  환경 변수 설정은 현재의 세션에만 유효합gkek. 모든 세션에 적용하기 위해서는 .bashrc나 .profile 같은 설정 파일에 선언해야 한다.

  #!/bin/bash를 적어주었는데 이것은 Unix 계열 Shell Script 파일의 필수적인 구문이다. 

<br/>
<br/>

###  3. 쉘 스크립트 문법

리눅스에서 사용되는 명령어는 모두 대소문자를 구분한다.
* * *

    1. echo: 출력 read: 입력

    기본적으로 echo명령이실행되고 나면 줄바꿈이 되어 진다. 줄바꿈을 하지않고 출력하려면 

      echo -n 변수 

      echo "~" $SUER

<br/>

    2. sh *.sh // 스크립트파일 만들기
    echo some-text > filename.txt
    vi tst.txt :wq

<br/>

    3. 변수 
    처음 할당시 자동으로 변수가 생성된다.
    숫자를 넣어도 문자로 취급한다
    변수를 대입할 때는 = 좌우공백이 없어야한다
    test=7+5

    변수는 $를 앞에 붙여서 나타내는데, $문자가 들어간 글자를 출력하귀 위해서는 ""로 묶는다


    var=Hi
    echo $var
    echo "$"

    <img width="392" alt="쉘환경변수연습" src="https://user-images.githubusercontent.com/74404132/126287469-a8b1bc03-74d4-4045-9253-a79deb4bc4ca.png">
<br/>


          sh variable.sh
<br/>

<br/>

        % var=$#       
        % echo "num=$#"
        num=0
            % echo "parameter: $0 $1 $2 $3"
        parameter: zsh   
            % echo "parameters: $@"         
        parameters: 
            % echo "var=$var"
        var=0
            % echo 'var=$var'
        var=$var
            % echo var='ls'
<br/>

          sh variable.sh 1 a "b"

<br/>

<br/>



    4. 리다이렉션 redirection

    쉘어서 입력과 출력의 방향을 바꾸는 명령어
    표준입력 0: 키보드
    표준입력 1: 터미널
    표준에러 2: 터미널 화면

    // > : 표준입력을 지정파일로
    // < : 키보드 대신 파일로부터 입력받음
    // 2> : 표준 에러를 지정 파일로
    // 2>&1 :표준 에러를 표준 출력으로
    // 1>&2 : 표준 출력을 표준 에러로

    ./my.sh > log.txt 2>&1

<br/>

    5. 파이프: fork exec 함수의 분리가 이걸 가능하게 해준다.
    ps -A | grep ssh

    ps -ef // 프로세스 목록 조회
    ps -ef|grep hugo|awk '{print $1, $2, $3, $8}'


    쉘 스크립트에서 백틱 사이의 명령은 실행되고 그 결과가 앞에 명령에 입력된다.
    kill -9 `ps -ef|grep hugo|awk '{print $2}'` // pid는 kill에 전달되어 종료된다

    pgrep -f hugo // ps, grep 명령어 결합
    // hugo는 Go 언어로 만들어진 정적 사이트 생성기이다. 빌드시간이 빠르고 안정적인 특징을 갖고 있다.
<br/>

    6. 키보드 입력을 만든 변수에 담기 : read
    read input
    echo $input
<br/>

    7. for loop
        num=0
        for i in $@
        do
          echo "$num : $i"
          num=$($num+1)
        done

        for i in $n
        do
            echo "$num : $i"
            num=$(($num+1))
        done

    맥에서 안됨. 해보기
<br/>

    8. if
    if [ expr ] then
      ...
    fi



    if [ expr ] 
    then
      ...
    elif [ expr ] then
      ...
    else
      ...
    fi



    case "$1" in
      dog)
        ;;
      cat|tiger)
        ;;
    esac


<br/>

    9. 문자열 비교, 패턴
    [[ $a == $b]]

    [[ $a == hello* ]]

    [[ $a != $b ]]


    ls -ld //  마지막 작업 시간?


<br/>

    10. 파일, 디렉토리, 문자열 테스트

    [ -d file ] // 파일이 있고 디렉토리인지
    [ -f file ] // 파일이 있고 일반 파일인지
    [ -r file ] // 파일이 있고 읽기 권한이 있는지
    [ -x file ] // 파일이 있고 실행 권한이 있는지
    [ -z string] // 길이 0 이상 문자열이 있는지

  <img width="438" alt="파일디렉문자열테스트" src="https://user-images.githubusercontent.com/74404132/126293114-d79ab6c8-cefe-423f-91b0-50bf1c48b23c.png">


<br/>

    11. 숫자 비교 테스트
    [ 3 -eq 5 ] // equal to

    -ne // not equal to
    -gt // greater than
    -ge // greater than of equal to
    -le // less than or equal to
    -lt // less than


    [ 3 -eq 3 ] && echo "Y" || echo "N"


  * * *



  <br/>
<br/>


## 커널이란?
  the core, privileged executive that manages "all system resources" and interacts directly with "hardware".

<br/>

***

# Linux 이해하기. 
  1. 리눅스는 컴퓨터 운영체제의 한 종류이자, 커널 자체를 의미하기도 한다. 리눅스의 가장 큰 특징은 두 가지인데,
      1. 소스 코드가 공개되어 있는 '자유 소프트웨어' 와 '오픈소스 개발' 의 가장 유명한 표본이라는 점이다.
      2. 다중 사용자, 다중 작업(멀티 테스킹), 스중 스레드를 지원하는 네크워크 운영체제로, 여러 사람이 하나의 리눅스 시스템에 접속하여 다수의 프로그램을 동시에 실행할 수 있다.
      Q) 두 컴퓨터에서 같은 가상환경 리눅스 사용할 수 있나?

      안드로이드 계열 스마트폰, 냉장고, TV 등과 같은 가전 제품에서도 리눅스 계열의 운영체제를 사용하고 있어 우리 삶에 깊숙이 들어와 있는 운영체제이다.

   <br/>

    Linux's main system libraries of Linux were originated by the GNU project.
    gcc(GNU C compiler) 를 리눅스에서 바로 이용할 수 있다.
      cf) 윈도우는 gcc가 깔려있지 않기 때문에 직접 gcc를 설치해야 한다.
<br/>
   

  2. 리눅스의 구성요소들은 Internet FTPC(file - transfer - protocol) archive sites 에 있다.

    File System Hiearchy Standard: the overall layout of a standard Linux file system
    
    리눅스는 configuration files, libraries, system libraries, run-time data 어디에 저장 돼 있는지를 이 규격에 따른다.


  3. Linux Licensing
    리눅스 제배포시 source code를 무조건 포함해야하는 license가 있다.
    GPL(General Public License)내에서 release 된 소프트웨어는
    binary-only product 만으로는 제배포 될 수 없다.

  4. Design Principles of Linux
    디자인 목표에는 속도, 능률, 기준의거가 있다.
    리눅스는 최근에 속도, 능률보다 "standardization" 에 집중한다.

    POSIX standards 란 서로 다른 OS 양상에 set of specifications를 구성한 기준이다.

    Linux는 
    1. POSIX document
    2. POSIX standard
    3. POSIX threading(Pthreads)
    4. POSIX extensions
    에 따른다. 

    5. user utilities
      UNIX standard: shell
      LINUX standard: bash

    6. Process Management: fork() and exec()

    7. Scheduling
      Linux 는 다른 모든 Unix 시스템과 같이 비선점 방식이다.

    8. linux scheduling 의 두 관점
      1. 유저 프로세스의 실행, 인터럽트
      2. the running of various kernel tasks
        실행 프로세스와 커널 작업(ex I/O)을 둘다 하는 것


2. 리눅스 디렉토리들

        /

        /home

        /boot

        /home/ubuntu

        /bin

        /etc
<br/>

    4. 리눅스 파일 권한

    리눅스 파일 권한 확인: ls -l

    rwe : read, write, execute
    4 2 1


    chmod: 변경하고자 하는 권한과 파일명을 명시하여 실행한다
    chmod 755 test.txt
    rwe re re 로 바꾸기.
    <br/>


  <img width="372" alt="리눅스 파일 권한" src="https://user-images.githubusercontent.com/74404132/126284697-ab70c0d3-b5ab-4c3e-b75e-99fc7443738a.png">

    -: 파일
    d: 디렉토리

    3개씩 끊어서 본다.
    앞 3개: 소유자의 권한
    중간 3개: group에 대한 권한
    뒤 3개: others에 대한 권한


    440: user, group에 대해서만 read 권한을 부여

    700: user의 모든 권한을 부여하고 group과 others는 모든권한을 제외

    +x: 실행권한 추가 부여
    g+w: group에 write권한 부여
    o-rwx: others의 모든 권한 박탈


  <img width="335" alt="리눅스권한" src="https://user-images.githubusercontent.com/74404132/126286571-61b42e9f-cc98-47a5-9f03-0494076f2985.png">




    



<br/>

## 리눅스 설치가 필요한 이유

  ### 리눅스/유닉스 개발 환경은 백엔드 개발자들에게 익숙한 개발 환경이다.
  터미널로 서버 환경에 원격으로 접속해서 원하는 작업을 할 수 있도록 친숙해져야 한다.

  리눅스 / 유닉스의 역사부터 쉘 환경에 익숙해지고 스크립트로 원하는 동작을 자동화할 수 있어야 한다.

근격인듯. 

<br/>
<br/>



  1. 리눅스 설치: ubuntu 20.04


  Mac에는 Native Ubuntu를 설치시 하드웨어 범용성 등의 제한이 있어서 가상머신을 사용해 설치를 해야한다. 

  윈도우와 달리 맥은 VMWare가 유료, 유명한 가상머신인 패러렐즈도 유료이다.
  무료로 사용할 수 있는 가상머신은 VirtualBox를 설치한다.

  1.1 virtual box 설치


  https://www.virtualbox.org/wiki/Downloads 에서 MAC (OS X) 다운로드. 

  <img width="740" alt="virtualbox" src="https://user-images.githubusercontent.com/74404132/126311559-7ef63545-4a6e-4551-8034-0ae8e0f42a30.png">

  <img width="813" alt="KakaoTalk_Photo_2021-07-20-20-07-27" src="https://user-images.githubusercontent.com/74404132/126314132-6b63e811-9470-4c1c-a6ce-1920db27bbbe.png">

  <img width="1275" alt="Screen Shot 2021-07-20 at 8 05 23 PM" src="https://user-images.githubusercontent.com/74404132/126313871-ef92ef7b-36da-4852-aee9-fd38b6e96b3f.png">

  desktop ver 다운로드.

  https://ubuntu.com/download/desktop

  <img width="1218" alt="l1" src="https://user-images.githubusercontent.com/74404132/126297085-3550c2f8-6ee9-4c27-90c0-eb5a007c934c.png">

    이런게 뜬다
  <img width="367" alt="Screen Shot 2021-07-20 at 8 38 54 PM" src="https://user-images.githubusercontent.com/74404132/126317864-e99f0815-b6c3-49f6-95ef-6a01d29ff2dc.png">

<br/>


  <img width="683" alt="Screen Shot 2021-07-20 at 8 41 14 PM" src="https://user-images.githubusercontent.com/74404132/126318020-f1a10c7f-5ed4-4a64-8500-f93e18006b5a.png">
  
  
  원인: 설치하는 도중에 인터넷이 한 번이라도 끊기면 파일이 받아지지 않는다..
  나중에 해결하고 이미 깔려있는 리눅스를 사용하겠다.ㅜㅜ

<br/>
<br/>

  1.2 Ubuntu 세팅

    리눅스는 일반적으로 RDP 프로토콜을 지원하지 않아 그래픽 데스크톱 환경에서 띄우기 위해 VNC, XRDP, XDMCP와 같은 프로토콜을 사용해야 하며 연결이 가능해지도록 일련의 설정을 해주어야 한다.

    GUI (Graphical User Interface) 사용을 위해 Ubuntu Desktop을 다운받는다.

<br/>

### 2. "가상 환경"에 "원격"으로 접속할 수 있도록 ssh을 설정, root 계정 이외에 본인 접속할 계정을 추가.

<br/>

<br/>

### SSH란?
  Secure Shell Protocol의 줄임말로서 네트워크 프로토콜 중 하나이다.

  HTTP 프로토콜이 컴퓨터와 컴퓨터가 통신하기 위한 규약인것처럼 SSH도 그 중 하나이다.

  SSH의 특별한 점은, 보안을 강조한 안전한 프로토콜이다.

  기존의 telnet, RSH, rlogin 등의 보안문제를 개선하기 위해서 나왔으며 통신이 노출된다 하더라도 이미 암호화 되어 있기 때문에 문제가 되지 않는다.

  (Telnet은 서버와 클라이언트 사이에 오가는 데이터를 암호화하지 않는다는 심각한 보안 결함이 있다.)

<br/>

### SSH client 와 server
  SHH 에서도 client 와 server 개념이 적용된다.

  집에서 데스크 탑으로 리눅스 운영체제를 사용하는 경우는 거의 없다. 같은 유닉스 기반인 macOS 가 있지만 이도 유닉스는 아니다.

  리눅스가 굉장히 각광 받고 있는 이유는 서버 시장에서 독보적인 점유율을 보이고 있기 때문이다.


  서버는"리눅스 기반" 으로 인터넷으로 제어되는 컴퓨터를 말한다.

  왜 서버시장에서는 리늑스를 쓸까?
    윈도우와 달리 리눅스는 오픈소스라서 커널 수정이 가능하기에 문제가 생겼을 때 커널을 수정해서 사용할 수 있다.

    참고: https://www.tecmint.com/why-linux-is-better-than-windows-for-servers/

  반대 개념인 클라이언트는 개발자, 사용하자 현재 사용 중인 데스크탑이나 노트북을 말한다.

  클라이언트는 서버를 원격 제어 해야하는데, 이 때 사용하는 것이 SSH이다.

    ssh client는 ssh server 에게 명령을, ssh server는 서버 컴퓨터에게 명령을 내리면 서버 컴퓨터는 명령의 결과를 ssh server 에게, 다시 ssh server는 결과를 ssh client 에게 보여주는 것이다.

  <br/>

  SSH를 통해 제어하기 위해서는 SSH server, SSH client 가 필요하다. 이는 별도의 설치가 필요하다.

  우분투 리눅스엔 SSH 클라이언트는 기본으로 설치되어있지만, SSH 서버는 설치해야 한다. 

  클라이언트가 설치된 컴퓨터로 서버가 설치된 컴퓨터에 원격 접속하는 것이다.

  사용자가 ssh client에서 명령어를 입력하면 클라이언트 컴퓨터를 제어하는 것이 아닌 서버 컴퓨터를 제어하게 된다.

  SSH 서버 실행 파일은 /usr/sbin/sshd이고, SSH 클라이언트 실행 파일은 /usr/bin/ssh이다. 

  <br/>

![Screenshot from 2021-07-21 03-56-19](https://user-images.githubusercontent.com/74404132/126407565-b142ef18-63b0-411d-845a-1b23d37c8df3.png)


  (d가 붙은 건 상주하는 프로그램, 데몬이란 뜻)



<br/>

### SSH server 설치

    sudo apt-get install openssh-server


open 이 붙은 이유는 상용 SSH와 달리 오픈소스로 제공된 부분으로 만든 오픈소스 SSH이기 때문이다.

server, client 동시 설치

    sudo apt-get install ssh

  
![Screenshot from 2021-07-21 03-59-02](https://user-images.githubusercontent.com/74404132/126407640-63a326c1-9de5-4676-9365-8e1d955f5375.png)

<br/>

### SSH server 설정파일(일부)

/etc/ssh/sshd_config 가 설정 파일이다.

    sudo vim /etc/ssh/sshd_config

vim = vi 대신 더욱 편하게 사용할 수 있다.

### vim 설치

<br/>

    $ sudo apt-get update
    $ sudo apt-get install vim

![Screenshot from 2021-07-21 03-59-45](https://user-images.githubusercontent.com/74404132/126407668-2c6677e8-9704-41d6-b6ec-a81cd3723b1b.png)

vim 기능 추가

    $ vi ~/.vimrc
vi 편집기로 ~(홈 디렉토리를 의미)에 .vimrc 파일을 생성하겠다는 명령어이다.

i 입력 후 쓰기모드에서 아래 복사

    set number    " line 표시
    set ai    " auto indent
    set si " smart indent
    set cindent    " c style indent
    set shiftwidth=4    " 자동 공백 채움 시 4칸
    set tabstop=4    " tab을 4칸 공백으로
    set ignorecase    " 검색 시 대소문자 무시
    set hlsearch    " 검색 시 하이라이트
    set nocompatible    " 방향키로 이동 가능
    set fileencodings=utf-8,euc-kr    " 파일 저장 인코딩 : utf-8, euc-kr
    set fencs=ucs-bom,utf-8,euc-kr    " 한글 파일은 euc-kr, 유니코드는 유니코드
    set bs=indent,eol,start    " backspace 사용가능
    set ruler    " 상태 표시줄에 커서 위치 표시
    set title    " 제목 표시
    set showmatch    " 다른 코딩 프로그램처럼 매칭되는 괄호 보여줌
    set wmnu    " tab 을 눌렀을 때 자동완성 가능한 목록
    syntax on    " 문법 하이라이트 on
    filetype indent on    " 파일 종류에 따른 구문 강조
    set mouse=a    " 커서 이동을 마우스로 가능하도록

여기서 " 표시는 c 언어에서 // 처럼 한 줄 주석을 의미

    esc
    :wq


<br/>

    sudo vim /etc/ssh/sshd_config
/etc/ssh/sshd_config가 설정 파일

<br/>

![Screenshot from 2021-07-21 04-09-27](https://user-images.githubusercontent.com/74404132/126407709-ddba7479-5ce1-4380-b315-a065d7a2d39c.png)

<br/>

    Port 22

ssh의 기본 포트는 22번이다. 변경하면 접속할 때 명시적으로 지정해야 한다.

    #ListenAddress 0.0.0.0

ListenAddress의 주석을 지우고 특정 IP 주소를 넣으면 해당 주소에서만 접속할 수 있다. 기본값은 모두 허용.


SSH 프로토콜 1의 개정판인 2를 사용하고, 1과는 호환되지 않는다.

보안 문제가 있어 1을 사용하지 않지만 둘 다 쓰려면 1, 2처럼 쓰면 된다. (config에서 안보임)


  HostKey /etc/ssh/ssh_host_rsa_key
  HostKey /etc/ssh/ssh_host_ecdsa_key
  HostKey /etc/ssh/ssh_host_ed25519_key

SSH 접속에 사용하는 서버의 키의 위치로, 클라이언트가 접속 시 아래 네 가지 방식으로 암호화된 호스트 키 중 기본값인 ECDSA 방식으로 암호화된 호스트 공개키가 클라이언트의 홈 디렉터리/.ssh/known_hosts 파일에 저장된다.

호스트 공개키는 위 파일명 끝에 .pub이 붙어있다. (예-ssh_host_ecdsa_key.pub)

따라서 서버에서 이 호스트 키가 변경되면 접속한 적이 있는 클라이언트에선 원격 호스트의 인증서가 변경되었다는 오류가 뜬다.

이럴 땐 아래 명령으로 클라이언트에 남아있는 호스트 키를 삭제하고 재접속하면 된다.
    ssh-keygen -R 아이디@서버주소

관리자 계정인 root로 로그인을 허용하면 yes, 아니면 no, 기본값은 공개키 인증 방식이 아닌 아이디와 비밀번호로 로그인할 때만 금지.
    PermitRootLogin prohibit-password

공개키 인증 방식을 사용하려면 기본값을, 아이디와 비밀번호로만 로그인하려면 주석 처리.
    PubkeyAuthentication yes

공개키 인증 방식으로 접속하려는 클라이언트는 먼저 서버의 AuthorizedKeyFile 속성 경로에 공개키를 저장해야 한다. 기본 경로는 주석과 같으며 %h는 사용자 홈 디렉터리.
    #AuthorizedKeysFile %h/.ssh/authorized_keys


### 원격 접속은 중요하고 필수적인 작업이다.
<br/>

  리눅스 서버를 구축한다면 터미널이나 GUI 환경을 통해 여러가지 작업을 진행할 수 있다.
  대부분의 리눅스 서버는 회사에서 사내 서버로서 한 장소에 묶어두거나, 호스팅 업체 및 클라우드 호스팅 등의 다양한 구성으로 이루어 졌기에 멀리 떨어져있다.

  서버작업 처리를 위해 매번 갈 수 없고, 서버가 점차 많아지게 되면
  각각의 서버로 이동하여 일일이 모니터를 연결할 수가 없다. 

    다양한 원격 접속 프로그램을 사용하여 원격지에 있는 서버에 굳이 찾아가지 않고 해당 서버의 주소(IP 등)만 알고 있다면 다른 PC를 통해 바로 접속할 수 있다.

  리룩스도 마찬가지다.

    이러한 원격 접속을 이용하여 터미널 환경을 사용할 수 있도록 고안된 프로토콜이 
    Rlogin, Telnet, SSH 이다. 

  우리가 흔히 접하는 프로그램인 Xshell, PuTTY, iTerm, SecureCRT는 

  " 윈도우에서 원격 리눅스 서버로 터미널 접속 프로토콜을 사용하여 연결할 수 있도록 도와주는 " 
  터미널 에뮬레이터 클라이언트인데, 리눅스 내에서 실행되는 터미널 또한 마찬가지로 터미널 에뮬레이터로 불린다.


  " 실존하는 것이 아닌 가상으로 구현된 복제품 "이기 때문이다. 

    기존의 터미널과 다른점: 기존 터미널은 포괄적으로 볼 수 있는 컴퓨터와 사용자 간의 소통을 위한 인터페이스이다. 


<br/>

### ssh 서버로 접속하는 법

그동안 접속했던 ip는 아래 명령어를 사용해 확인할 수 있다.
    ~# cat /var/log/auth* | grep Accepted | awk '{print $9"\t"$11"\t"$14}' | sort | uniq

ssh로 접속하는 방법은 여러가지가 있다. 왜 여러가지가 있는지 이해해야한다.

    포트포워딩이란? 네트워크 인터페이스를 하나 더 추가하는 것
    포트포워딩을 이용하면 root 계정이 아닌 user 계정으로 서버를 실행하여
    보안 이슈를 회피하고 port 가용성을 확보할 수 있다.

포트포워딩을 하기 위해서는 현재 사용하고 있는 공유기의 설정 사이트를 가야한다. 

네이버 내 ip 확인: 121.131.108.204
주소창에 쓰면 공유기 설정 웹으로 갈 수 있다.
    ssh username@hostname

    ifconfig | grep inet // mac ip 172.30.1.55

    ip addr | grep "inet " // ubuntu ip

<br/>

![Screenshot from 2021-07-21 04-40-32](https://user-images.githubusercontent.com/74404132/126407730-9ff8ad36-c482-4ba3-99ab-2d591c486293.png)

<br/>
username에는 사용자의 계정을, hostname에는 ip 주소를 혹은 도메인을 기재해주면 된다. 

이럴 경우 기본적으로 22번 포트를 사용하게 된다.

* 이 ip로 접속 시도했더니 가상 환경의 포트번호가 20에서 22로 바꼈다.


원하는 포트가 있을 경우에는 -p로서 포트 번호를 지정해줄 수 있다.

    ssh -p portnumber username@hostname


호스트 기반 인증 방식을 사용하려면 yes로 합니다. 보안 문제로 권장하지 않습니다.

SSH 인증 방식은 아이디, 비밀번호로 하는 패스워드 인증, 공개키 인증, 호스트 인증 방식이 있습니다.

    HostbasedAuthentication no

<br/>




3. 본인 계정 패스워드 설정
자동으로 비번 설정하라고 뜸.


<br/>

4. 로컬 컴퓨터에서 가상환경 리모트 컴퓨터에 ssh로 접속해서 본인계정으로 로그인

우분투 가상환경에서도 계속 로그인 상태를 유지시켜줘야 했다. 

    netstat -ntl

    apt install net-tools // 위에꺼 안되면

<br/>
<img width="478" alt="Screen Shot 2021-07-21 at 7 20 30 AM" src="https://user-images.githubusercontent.com/74404132/126406929-31f8f29c-d931-4538-b40b-cd3d455a8dd1.png">
패스워드 이용해 가상환경 접속 완료.

<br/>

![Screenshot from 2021-07-21 06-00-22](https://user-images.githubusercontent.com/74404132/126408011-ae17b415-9249-470d-8d9d-2286e524e3a5.png)

<br/>

compare: logged in at Ubuntu

<br/>
5. 본인 계정에서 /backup 디렉토리를 생성하고 764 모드로 접근권한 바꿔서,
본인 계정으로 /backup 경로 아래에 파일을 생성할 수 있도록 설정한다.

sshd 서비스를 시작하여 다른 PC에서 접속할 수 있도록 한다.

  service sshd start

  ps -aef|grep sshd

mac 은 ssh 클라이언트가 기본으로 탑재되어 있다.

공유기 사이트를 들어가지 못하는 관계로 ip 허용, 특정 사용자만 허용을 사용했다.


    sudo nano /etc/hosts.allow

    sshd: (ip 2자리까지만 기록)


    sudo nano /etc/ssh/sshd_config

    AllowUsers janna

<br/>

![Screenshot from 2021-07-21 07-19-02](https://user-images.githubusercontent.com/74404132/126408184-eb14b26a-dbfa-4f84-8838-1b9d819700f7.png)


<br/>

images.githubusercontent.com/74404132/126408097-40036dce-b4a0-436b-beae-a2a5bc8f4211.png)

<br/>



<br/>

참고: https://happist.com/573817/리눅스-서버-접속-ip-허용-사용자-접속-허용하기

chmod 764 test.txt
  : user group others 권한을  rwe rw r 로 바꾼다.


chmod: 변경하고자 하는 권한과 파일명을 명시하여 실행한다
리눅스 파일 권한 확인: ls -l

rwe : read, write, execute
4 2 1


<img width="574" alt="Screen Shot 2021-07-21 at 7 23 48 AM" src="https://user-images.githubusercontent.com/74404132/126406372-4eb6831a-e93e-4da2-9cb0-dcc708d6ea7b.png">

ls -l 명령어로 권한 수정됐음이 확인됐다.

<br/>


<img width="632" alt="Screen Shot 2021-07-21 at 7 21 50 AM" src="https://user-images.githubusercontent.com/74404132/126406722-9652de12-e225-47b2-9da8-9fffecd33be4.png">

파란 janna가 가상 서버. ls 명령어로 backup 파일 생성됐음을 확인.


<br/>

6. 가상 환경에 오늘 날짜 + 서울로 지정해서 로컬과 가상 환경이 동일하도록 맞춘다.

    sudo dpkg-reconfigure tzdata

  The timezone info is saved in /etc/timezone - which can be edited or used belo

![Screenshot from 2021-07-21 05-57-29](https://user-images.githubusercontent.com/74404132/126407903-064de408-870a-44bf-9539-f75a9522b946.png)

<br/>  

7. 가상 환경에서 터미널을 열고 date 명령으로 오늘 날짜를 출력한 상태로, 화면을 캡쳐한다.

<br/>  

![Screenshot from 2021-07-21 06-00-22](https://user-images.githubusercontent.com/74404132/126407937-bace6a65-a67e-4d33-be9c-a86789af2903.png)

<br/>  

8. 가상 환경에 node.js v14.x 를 설치하고 버전을 확인한다.

리눅스에서 사용 가능한 개발 언어와 DB 종류

  리눅스 운영체제 환경에서 사용 가능한 개발언어는 다양합니다. 커널을 포함하여 리눅스 자체가 어셈블리와 C로 개발되어 있어, 이후에 만들어진 C++, Java, Perl, PHP, Python, Ruby, Lua, Go 언어 등을 모두 호환한다.

  DB의 종류 또한 MS에서 개발된 MSSQL을 제외한 대부분의 DB를 지원한다고 할 수 있습니다. 일반적으로 알려진 DBMS인 Oracle, MySQL, MariaDB, PostgresSQL, CUBRID, Firebird를 포함하여 DB2, INFORMIX, Altibase 및 파일DB인 SQLite를 호환하고 있으며 최근 빅데이터에 대한 이슈로 인해 각광 받고 있는 NoSQL계열인 HBase, Cassandra, MongoDB, Couchbase, Redis, Riak 등의 데이터베이스 또한 설치/운영이 가능하다.


    apt-get install curl

  1,115KB of disk space used.

    nvm 설치

    $ curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.25.3/install.sh | bash

    ssh를 재시작. logout 후에 다시 ssh로 접속

    $ source ~/.bashrc

  bashrc를 새로 적용시켜 준다.

    nvm install node
    nvm install v0.14.17.3 

    node -v

  설치 완료. 근데 깨졌다?


NVM으로 Node.js를 설치 할 경우 그냥 설치한 것과 설치 위치가 달라지기 때문에 sudo 명령어와 함께 npm이나 node명령어가 적용이 되지 않을 경우가 있습니다.
그래서 sudo에 대한 PATH 환경변수를 수정해야 하는데 이 설정은 sudoers 파일을 수정해야 하며 visudo 명령어로 아래와 같이 변경 할 수 있습니다.

    $ sudo visudo


    ####################################### ## env_reset를 무효화 처리 ###################################### # Defaults env_reset Defaults !env_reset ###################################### ## HOME을 사용할 수 있게 주석 제거 처리 ###################################### # Defaults env_keep += "HOME" Defaults env_keep += "HOME" ####################################### ## PATH가 덮어쓰지 않도록 주석처리 ####################################### # Defaults secure_path = /sbin:/bin:/usr/sbin:/usr/bin

참고: https://stories.tistory.com/225


9. set.js 파일을 복사해서 실행한다.
apt-get install curl



![Screenshot from 07-21 07-53-39](https://user-images.githubusercontent.com/74404132/126408127-7234d398-1562-456f-8aa5-5a17fca5381b.png)

<br/>




<br/>
