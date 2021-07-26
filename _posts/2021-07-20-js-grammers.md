---
layout: post
title:  "JS grammers"
excerpt: "reviews"


categories:
  - Blog
tags:
  - [Blog, jekyll, Github, Git]

 
date: 2021-07-20
last_modified_at: 2021-07-20
---


<br/>


머지 소트는 절반씩 정렬하고 합치는 것.
왼쪽 정렬, 오른쪽 정렬, 병합 세 구성.
새 배열에 투포인터로 정렬한거 저장하고 받은 lo hi 에 맞춰서 원본에 전달한다.

function A(Array)
arr.push();
arr.length

개행문자 없이: 
process.stdout.write();
let arrayB = new Array(1, 6, 7)
let arrayA = [2, 3, 4, 3, 5]
; 없어도 되는듯

문자열 포맷팅
console.log(`hi ${name} `);

const f2 = (a, b) => {
  if(a>b) return 1;
}

console.log([1,2,3].sort(f2));

함수형 인터프리터에 대해 공부하기.

<img width="825" alt="git study" src="https://user-images.githubusercontent.com/74404132/126221934-5a883a79-248d-4b68-b299-0905db01b999.png">

MDN, stackoverflow 활용하기
가급적 영어로 검색해보기
API 보기

Es2015: 최근 문법활용이다

함수는 명확한 하나의 역할에 집중한다.

하위 함수 나누기

일관성

고차함수의 활용
와일, 포문 아닌 고차원 함수

함수형 프로그래밍


cmd + b : hide vscode sidebar


JSON.stringify(solution(inputA, inputB)) // 문자열로 만들기

콘솔 실행 바로?

함수안에 함수 쓰지말고 습관적으로 분리해서 쓰는 것이 좋다.

filter, map에 익숙해지자 bind?

spread operator, rest parameter

function solution(...args) // solution에 배열들 합쳐서 받는다.
other.inludes

디자인을 하는 게 중요하다.
수도코드, 종이 등 나만의 설계방법을 찾아야한다.

DDD: Debugging Driven Development
DDL: Debugging Driven Learning

브랜치: 특정 시점을 기준으로 분기하는 저장소의 작은 단위

module.exports()
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

arr.slice()
값 합치기?
includes? 값이 포함돼 있는지 알 수 있다.
findIndex 몇번째 값인지 찾아서

여러명이 마스터브랜치에서 작업하면 충돌이 일어날 수 있다.
병렬적으로 동시작업이 처리

얉은 복사 깊은 복사?

concat 으로 합칠수 있다 배열

print.js 따로 만들어서 불러올 수 있다. 
map. 

gitflow?

github flow

gitlab flow 
master <- production branch <- pre-production

깃헙의 기능을 제공하는 방식
커밋

[...base] 깊은 복사
.sort() 하면 문자열식으로 바꿔서 정렬이 된다.

깃 애드 커밋 푸시 관리해서 
.slice()

2차원배열 얉은 복사는 밖에만 새로 바꾸고 안에는 기존을 참조하고 있어서 안도 바뀌면 같이 바뀜
깊은 복사: 새로운 데이터로.
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