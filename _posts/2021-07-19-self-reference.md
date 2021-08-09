---
layout: post
title:  "commands"
excerpt: "reviews"


categories:
  - Blog
tags:
  - [Blog, jekyll, Github, Git]

 
date: 2021-07-19
last_modified_at: 2021-07-19
---

     start
<br/>


     LTS stands for long term support(on update, patch and maintain the software)
<br/>

     merit: here is a shorter development cycle, where engineers and contributors add to the body of the release. And a longer beta testing cycle, where more testing and bug fixing takes place to focus on a release’s performance and stability. 
<br/>

     LTS 는 추후 업데이트 될 때도 잘 적용되도록 
     일반적인 경우보다 장기간에 걸쳐 지원하도록 특별히 고안된 소프트웨어의 버전 또는 에디션이다.
<br/>

     Without long term support, software can become a security risk

<br/>



# js 는 브라우저가 아닌 터미널 등에서 실행될 수 있다.
<br/>

     = CLI(Command Line Interface) 에서 실행할 수 있다.
<br/>

     node run.js
<br/>

     mv 1_day.js 1day.js  // file name change

<br/>
     mv file

     mv w4/MinJaeKim/17.cpp w5/MinJaeKim 
<br/>

     mkdir challenges new folder
<br/>

     rm 삭제
<br/>

     cp file1 file2 
<br/>

     cp file1 file2 dir1/ 파일 해당 폴더 안에 복사
<br/>

     cp -r dir1/ dir2 // 여디렉토리 전체를 복사
<br/>

     pwd // 경로

<br/>

     touch test.txt // create file

<br/>

     clear // 터미널 깨긋하게


<br/>
     원격으로 파일 또는 폴더 복사하기
     scp 는 ssh 와 동일한 프토토콜을 사용한다.

  % scp -E ~/ImportantPapers.tgz username@remoteserver.com:/Users/username/Desktop/ImportantPapers.tgz
해당 사용자의 암호를 입력하라고 요청 받습니다.
-E 플래그는 확장된 속성, 리소스 포크 및 ACL 정보를 유지합니다.
이 예제에서 사용되지 않은 -r 플래그를 scp 명령어와 함께 사용하면 폴더와 폴더의 콘텐츠를 복사합니다.   



***
## git commands

https://git-scm.com/docs/giteveryday

<br/>

     git add hello.txt // 해당 파일 add

     git status
<br/>

     git commit -am "message" (파일이 commit 된 후, ) 다시 새 버전을 만들 경우, 'add', 'vim에서 msg작성하는 작업'을 명령창에서 바로 할 수 있다. ??

<br/> 

     git branch // 현재 위치한 브랜치
<br/>

     git remote add upstream https://github.com/ORIGIN_OWNER/ORIGIN_REPO.git

    remote 설정.

    내가 PR을 보낼 곳을 추가해 준다.
    원격 저장소의 이름은 upstream 으로 지정한 것.
<br/>



     git branch apple // 새 브랜치 만들기
<br/>
     git checkout -b 브랜치 // 이런 브랜치 있나 보고 없으면 만든다.

<br/>

     git checkout apple // 이 브랜치로 이동하기
<br/>

     git checkout apple // 이 브랜치로 이동하기
<br/>

     git log master..develop1 // dev에만 있는 커밋 알려준다
<br/>

     git log develop1..master // dev에만 있는 커밋 알려준다
<br/>

      git push origin test // 이 브랜치에 푸시하기


<br>

  git request-pull v1.0 https://git.ko.xz/project master // on my master branch

<br/>

## 깃 병합하는 법

1. master branch로 checkout
2. git merge develop1

<br/>

     git restore file // modified 내용 삭제한다. 즉, 수정한 내용을 삭제해버리고 기존 상태로 되돌린다.

***
***
<br/>


     GUI: 사용자 인터페이스와 통신하게 해주는 shell

<br/> 

     요즘 컴퓨터 환경은 거의 다 GUI입니다. GUI가 아닌 프로그램은 거의 없습니다. 윈도우를 부팅하여 바탕화면이 나오면 그 자체가 전부 다 GUI입니다.

<br/>

      CLI(Command-Line Interface)입니다. 이것은 키보드로 명령어를 일일이 타이핑하여 프로그램을 사용하는 원시적인 방식입니다. GUI와 달리 CLI는 명령어를 모두 외워야 하기에 상당히 불편합니다. 다만 전문가에게는 CLI가 더 편리할 수도 있습니다. 

<br/>

     PR: Pull Request를 통해서 fork를 했던 원래의 저장소에 소스코드를 보낼 수가 있다.


<br/>

     fork 한 걸 가져와야함

포크한 걸 푸시하면 내가 갖고온거에 반영되고 
풀리퀘를 보내면 원본에 변경사항 요청 보내는 것


Create
Add
commit message


node js 는 인터프리터


<br/>

### vscode commands

<br/>

<ol>

<li> ctrl + shift + x : market space

<li> opt + b : open html in default web browser


<li> cmd + \ : 편집창 분할


<li> cmd + op 위아래: 커서 키우기 / 왼오: 창이동

<li> ctrl + g : go to line

<li> fn + f12 : go to def

<li> shft + fn + f12 : 해당 func 사용하고 있는 부분 표시




### 탭 창 단축키

cmd + shift +l 즐찾탭 제거 

cmd + n 새 창

cmd + t 새창 열어 이동

cmd + 화살표 : 앞, 뒤로 가기

cmd + op + i: 개발자 도구 열기

cmd + l : 검색 주소창으로 이동

cmd + w : 현재 창 지움



###
vim .zshrc
path drag 하면 알아서 받아온다
source .zshrc // 새로쓴 거 적용해준다
flutter --version


op + shift <- 한 단어 선택


git clone -b 

single--branch
동일한 이름 브랜치가 있을때 
arr.toArray();

fork 부터 pr 보내기

add 하면 오브젝트 파일을 생성
인덱스를 

중앙화된 workflow
feature branch?

상황별로 마스터 디벨롭 피쳐 릴리즈 핫픽스: 긴급상황 수정

목적에 따라 적절한 워크플로우를 선책해야 한다!

gitflow?

github flow

gitlab flow 
master <- production branch <- pre-production

깃헙의 기능을 제공하는 방식
커밋

### mv 1_day.js 1day.js  // file name change
<br/>

### mkdir challenges new folder
<br/>

### rm 삭제
<br/>

### cp file1 file2 
<br/>

### cp file1 file2 dir1/ 파일 해당 폴더 안에 복사
<br/>

### cp -r dir1/ dir2 // 여디렉토리 전체를 복사
<br/>

### pwd // 경로

<br/>

### clear // 터미널 깨긋하게



***
## git commands
<br/>

### git add hello.txt // 해당 파일 add

### git status
<br/>

### git commit -am "message" (파일이 commit 된 후, ) 다시 새 버전을 만들 경우, 'add', 'vim에서 msg작성하는 작업'을 명령창에서 바로 할 수 있다. ??

<br/> 

### git branch // 현재 위치한 브랜치
<br/>

### git branch apple // 새 브랜치 만들기
<br/>

### git checkout apple // 이 브랜치로 이동하기
<br/>

### git checkout apple // 이 브랜치로 이동하기
<br/>

### git log master..develop1 // dev에만 있는 커밋 알려준다
<br/>

### git log develop1..master // dev에만 있는 커밋 알려준다
<br/>

## 깃 병합하는 법

1. master branch로 checkout
2. git merge develop1

<br/>

### git restore file // modified 내용 삭제한다. 즉, 수정한 내용을 삭제해버리고 기존 상태로 되돌린다.

***
***
<br/>


### GUI: 사용자 인터페이스와 통신하게 해주는 shell

<br/> 

### 요즘 컴퓨터 환경은 거의 다 GUI입니다. GUI가 아닌 프로그램은 거의 없습니다. 윈도우를 부팅하여 바탕화면이 나오면 그 자체가 전부 다 GUI입니다.

<br/>

###  CLI(Command-Line Interface)입니다. 이것은 키보드로 명령어를 일일이 타이핑하여 프로그램을 사용하는 원시적인 방식입니다. GUI와 달리 CLI는 명령어를 모두 외워야 하기에 상당히 불편합니다. 다만 전문가에게는 CLI가 더 편리할 수도 있습니다. 

<br/>

### PR: Pull Request를 통해서 fork를 했던 원래의 저장소에 소스코드를 보낼 수가 있다.

op + shift <-
한 단어만 선탣


cycle
dfs tree
union find u, v 합치는데 이미 같ㅇ면 싸이클이다

