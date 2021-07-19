---
layout: post
title:  "Fullstack start"
excerpt: "reviews"


categories:
  - Blog
tags:
  - [Blog, jekyll, Github, Git]

 
date: 2021-07-19
last_modified_at: 2021-07-19
---

### start
<br/>


### LTS stands for long term support(on update, patch and maintain the software)
<br/>

### merit: here is a shorter development cycle, where engineers and contributors add to the body of the release. And a longer beta testing cycle, where more testing and bug fixing takes place to focus on a release’s performance and stability. 
<br/>

### LTS 는 추후 업데이트 될 때도 잘 적용되도록 
### 일반적인 경우보다 장기간에 걸쳐 지원하도록 특별히 고안된 소프트웨어의 버전 또는 에디션이다.
<br/>

### Without long term support, software can become a security risk

<br/>



# js 는 브라우저가 아닌 터미널 등에서 실행될 수 있다.
<br/>

### = CLI(Command Line Interface) 에서 실행할 수 있다.
<br/>

### node run.js
<br/>

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


<br/>

### fork 한 걸 가져와야함

포크한 걸 푸시하면 내가 갖고온거에 반영되고 
풀리퀘를 보내면 원본에 변경사항 요청 보내는 것


Create
Add
commit message


node js 는 인터프리터