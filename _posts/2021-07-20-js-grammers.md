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



<br/>

### fork 한 걸 가져와야함

포크한 걸 푸시하면 내가 갖고온거에 반영되고 
풀리퀘를 보내면 원본에 변경사항 요청 보내는 것


Create
Add
commit message


node js 는 인터프리터

import PCB from './PCB.js'
export default class PCB {}

var state = Object.freeze({ready : 'ready', running : 'running', waiting : 'waiting', terminated : 'terminated'})

constructor (...args) { }

# 붙이면 private


  for(const burstTime in this.jobQueue){
      this.jobQueue[burstTime].procState = state.waiting
      this.readyQueue.allocateProcess(this.jobQueue[burstTime])   
  }

idx 받고 A[idx]

    jobQueueLoader(burstTimes) { 
        burstTimes.forEach(burstTime => {
            let newPCB = new PCB(parseInt(burstTime))
        });

    }


링크드 리스트: head tail 구조체 이용



rl.on('line', (input) => {
  const times = input.split(' ') // input format: '1 2 3'
  linux.createProcess(times.map((time) => parseInt(time)));
  rl.close();
}).on('close', function() { // 동기화가?
  //const scheduled = Promise.linux.schedule()
  while(true){ 
    linux.schedule().then() // ???????????????????????{}
    linux.processQueue.readyQueue.isReadyQueueEmpty().then()
    console.log(linux.processQueue.kernel.getPCBs());
    let hello = async function() { return "Hello" };
    hello();
    sleep(1000)
    if(linux.processQueue.readyQueue.isReadyQueueEmpty() == true){
      console.log("모든 프로세스가 종료되었습니다.")
      

    }
    //process.exit(); // 지저분..

  }
  
}); // hello hi an nyeong hi ?  !힘내세요!🦮


        let outs = []
        const res = this.PCBs.reduce( (acc, cur) => { // ex) A(terminated), 3 / 3sec
            let state = cur.procState
            let time;
            time = cur.accountingInfo.getUsedTime()
            outs.push(`${String.fromCharCode(65 + cur.pid)}(${state}), ${time} / ${cur.getBurstTime()}sec`) 
        }, [] );
        
        return outs;


const { log } = require("console");




export const state~
import PCB, {state} from './PCB.js'


객체 가져 가는법

const {K1, K2} = require("./fact_sheet")
class Kichen{}

let K1 = new Kichen(1)
let K2 = new Kichen(2)

module.exports = {K1, K2}

indexOf 말고 include 로 어딨는지 찾자.