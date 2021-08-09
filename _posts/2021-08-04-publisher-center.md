---
layout: post
title:  "publisher center"
excerpt: "reviews"


categories:
  - Blog
tags:
  - [Blog, jekyll, Github, Git]

 
date: 2021-08-04
last_modified_at: 2021-08-04
---


새로운 개념들을 학습하면서 새로운 방식으로 구현하기 시작해야 한다.
그 중 하나가 여러 타입들을 만들고 (모듈들을 만들고) 
그 모듈끼리 어떤 식으로 호출하고 데이터를 받을 것인가 고민을 해야한다.

그럴 떄 많이 쓰는 게 옵저버패턴, pub-sub 패턴이다.

직접 구현해보는 미션이었다.


<img width="861" alt="image" src="https://user-images.githubusercontent.com/74404132/128078233-0038e78a-3556-4724-9233-f0d509149844.png">

옵저버 패턴은 subject 와 observer 라 하는 두 개의 객체, 타입, 모듈 끼리의 관계이다

오른쪽의 sequence diagram 을 보면, 
observer1, observer1 가 attach 해놓고 subject가 어떤 상태가 바꼈을 때 notify를 받으면,
그 notified를 다른 옵저버들한테 알려주는 흐름으로 되어있다.


<img width="439" alt="image" src="https://user-images.githubusercontent.com/74404132/128078679-4abd75d6-438e-4c7b-b4c0-921b14b9af17.png">

This pattern is the cornerstone of event driven programming, including JavaScript. The Observer pattern facilitates good object-oriented design and promotes loose coupling.

Event handlers are functions that will be notified when a certain event fires. These notifications optionally receive an event argument with details about the event (for example the x and y position of the mouse at a click event).

The event and event-handler paradigm in JavaScript is the manifestation of the Observer design pattern. Another name for the Observer pattern is Pub/Sub

    function Click() {
        this.handlers = [];  // observers
    }

    Click.prototype = {

        subscribe: function (fn) {
            this.handlers.push(fn);
        },

        unsubscribe: function (fn) {
            this.handlers = this.handlers.filter(
                function (item) {
                    if (item !== fn) {
                        return item;
                    }
                }
            );
        },

        fire: function (o, thisObj) {
            var scope = thisObj || window;
            this.handlers.forEach(function (item) {
                item.call(scope, o);
            });
        }
    }

    function run() {

        var clickHandler = function (item) {
            console.log("fired: " + item);
        };

        var click = new Click();

        click.subscribe(clickHandler);
        click.fire('event #1');
        click.unsubscribe(clickHandler);
        click.fire('event #2');
        click.subscribe(clickHandler);
        click.fire('event #3');
    }


    <!-- fired: event #1 
    fired: event #3  -->

옵저버 패턴은 구현은 쉬운데 객체나 타입들이 직접적으로 갖고 있다 보니 그 관계를 좀 떨어트려 놓고 싶어서
pub sub 같은 패턴을 사용하게 된다.

* 직접적인 참조 관계를 떨어트리고자 사용한다


싱글톤: 꼭 써야 하는지, 언제 좋은 지 찾아보기


### Publisher - Subscriber 패턴

<img width="723" alt="image" src="https://user-images.githubusercontent.com/74404132/128081644-490b3a85-4af8-4329-85ba-e2171dc161f5.png">

등록된 배열들을 따라 .

다른점은, publisher 와 옵저버거 떨어져 있다는 것

중간에 역할을 대행해주는 간접적인 구조가 들어간다

얘가 관계를 끊어주기 때문에, 어떤 퍼블리셔가 어떤 이벤트를 보냈는 지는 subscriber들이 잘 모르게 할 수 있다.

퍼블리셔도 어떤 subscriber들에게 정보가 전달이 되는 지 모른다.


subscriber 가 있던없던 받을 수 있는 구조를 만들 수 있기 때문에 더 선호된다. ??

publisherCenter 역할을 하는 애를 네트워크까지도 지원을 할거냐, 
주고 받는 메세지를 큐잉에서 어떤 단위로 보관을 할 거냐의 구조에 따라 여러가지로 나뉘기도 한다.
메모리 캐싱 구조나 다양한 형태의 메세지 패턴이. nktt?

이게 어떤 지식들과 연관이 되는지 찾아보기.



<img width="727" alt="image" src="https://user-images.githubusercontent.com/74404132/128082850-f4fba8f1-3be8-4092-b3aa-617c207b0cce.png">


구독자들을 먼저 등록하고, publisher가 이벤트를 발행했을 때
해당하는 이벤트. 내가 누구고 어떤 이벤트를 발생했을 때 어떤 데이터가 등록된 sub 들에게 전달이 되느냐를 만들어 보면 되는 거였다.


<img width="762" alt="image" src="https://user-images.githubusercontent.com/74404132/128083116-f8b8da01-2769-4e72-9d76-510e95fb1d56.png">

sub들은 Sender 를 알고도 보낼 수 있지만 모르고도 얼마든지 처리할 수 있다.

null, undefined, nill 이런 값들을 넣으면 됐다.

이 두가지를 조합해서 이벤트가 발생하고 전달이 되고 콜백이 되는 구조를 만들면 된다.

각각 subscriber가 어떤 조건으로 subscribe를 했는지
sub 4명인데 다섯개를 호출하면 어떤식으로 되는 지



let getData2 = async (i) => {
    try {
        await promiseTime(i)
    } catch (error) {
        console.error(error.message);
    }
};

const promiseTime = (i) => {
  return new Promise((resolve, reject) => {
    try {
      setTimeout(() => {
        resolve(console.log(i, "번째로 실행된 함수"));
      }, (parseInt(Math.random() * 30) + 1) * 1000); // 30초 랜덤
    } catch (error) {
        reject(error.message);
    }
  });
};

for (let i = 0; i < 100; i++) {
  getData2(i);
}


event emmiter ??


DelayReceiveEvent() {
    this.emit("delay");
  }

  setDelay(str) {
    this.on("delay", async () => {
      setTimeout(() => {
        console.log(str);
        console.log("🠑 딜레이 출력 완료 시각", new Date());
      }, 10000);
    });
  }