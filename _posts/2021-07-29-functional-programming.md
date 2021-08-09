---
layout: post
title:  "functional programming"
excerpt: "reviews"


categories:
  - Blog
tags:
  - [Blog, jekyll, Github, Git]

 
date: 2021-07-29
last_modified_at: 2021-07-29
---


<br/>

<li> 최근언어들은 함수형 프로그래밍, 절차형 프로그래밍의 모습을 둘다 갖고있다
+ 객체지향 프로그래밍

"멀티 패러다임" 이라 불린다

<img width="658" alt="image" src="https://user-images.githubusercontent.com/74404132/127379311-8abcd451-7e08-40aa-a72d-aa1d34148e55.png">

<br/> 


절차적 표현: 실행 순서가 중요한 것, 계속 바뀌는 변수를 사용한 것과 달리
함수형 프로그래밍에서는 값이 변하지 않고 const 나 let value 같은 형태로 
" 값이 계속 바뀌지 않으면서 함수형으로 선언적으로 표현할 수 있는 방식" 이다.

  함수적 표현 : 안 바뀌는 값들로 함수 이용해서 값 알아내는 방식 

<img width="657" alt="image" src="https://user-images.githubusercontent.com/74404132/127380650-bf364918-3af8-443e-aa0b-eae5fd249d86.png">

closure나 lambda 문법을 얼마나 잘 활용해서 고차함수 형태로 표현하는지 연습하자.

<br>

<li> 함수형으로 표현하는 게 어떤 의미, 차이가 있을까?

함수형 접근방식은 명령형(절차적) 과 다르게 "데이터를 어떤식으로 변환하는지",
그걸 "함수적으로 어떻게" 표현하는지가 중요하다.

명령형 접근방식에서는 작업을 수행하는 알고리즘 로직이 상태값을 어떻게 바꾸는지가 중요하다
변수를 하나 놓고 그 변수가 어떻게 바뀌는 지 계속 살피는 것이다.

함수형 접근방식세어는
1부터 n까지 다 production 하면 n이 된다라고 선언하는 게 더 중요하다
fact n = product [1..n]

그걸 evaluation 하는건 조금 다른 관점에서 보게 되는 것이다.

함수형 프로그래밍은 상태값을 참조하는 게 아니라 "다른 함수로 넘어갈 때 전달" 되고 "복사"되는 형태로 값을 사용하게 된다

    값이 변경되지 않고 "불변값으로" 사용하게 된다. 
    그렇게 해야 순수함수를 만들 수 있다.

함수가 계속해서 실행하려면 절차가 있어야 하지만 절차가 덜 중요한 것이다.

순수한 함수형 언어에서는 제어 흐름이 for, 조건 그런 게 없다 (파스칼, 스킴)
"재귀호출" 로 표현한다. 변화하는 값 자체를 다루지 않기 때문이다.

구현 단위도 일급 객체라고 부르는 게 함수이고, 데이터 콜렉션(리스트 등) 을 많이 쓰는다
걔네들도 계속 값이 복사되서 새롭게 생길뿐이지 구조체나 클래스 만들어 놓고 계속해서 값을 바꾸는 객체 지향적 모습과는 차이가 있다.

<img width="1524" alt="image" src="https://user-images.githubusercontent.com/74404132/127382112-ada30df8-da6b-4c55-a1d3-bfd8c612991a.png">


<br/>

<br>
<li> functional programming: 수학적인 표현이 가능하냐 이다
수학적인 함수가 뭐고 그게 우리가 다루는 프로그래밍에서의 함수와 뭐가 다른 지 알아보자.

functional : 함수도 다른 타입들처럼 함수 자체를
    1. 타입으로 지정하거나
    2. 인자값으로 넘기거나
    3. 리턴값으로 받을 수 있는 것

(*) 그래서 "함수도 first class citizen 이다" 라는 표현을 한다

functional programming 에서는 수학적인 함수를 만들고 그 수학적인 함수들을 가지고
함수 자체를 데이터처럼 쓸 수 있는 것을 의미한다

<img width="336" alt="image" src="https://user-images.githubusercontent.com/74404132/127383186-af34be53-acdc-4194-b48c-2d7c20465076.png">

<br/>

<br>

<li> 수학적인 함수와 프로그래밍 함수와의 차이
수학적인 함수 : 입력과 출력의 관계가 명확한 것. 선언적으로 딱 나타낸다.
입력값이 있으면 "반드시 매핑되는 출력값이 존재해야" 한다.
수학적인 함수는 그 관계를 나타내는 것이다
그 관계를 나타낼 수 없는 게 있다면 그 함수의 바깥에서 다른 함수로 나타내야 한다.

프로그래밍 함수들은 입력과 출력의 관계를 나타낼 수 없는 함수들, 기능들이 있다
그런걸 다른 언어에서는 프로시저라 부른다
파스칼에서는 리턴타입이 없는 함수를 프로시저라 부른다

현대 프로그래밍 함수들은 수학함수와 거의 일치시켜 표현하고는 있다
실제로 명확히 따져보는 입력, 출력이 없는 console.log와 같은 함수들은 전형적인 '프로그래밍 함수' 라고 볼 수 있겠다.

console.log() 는 그냥 화면에 출력하는, 컴퓨터에게 일 하게 하는 것이지
이 함수 자체가 리턴해주진 않는다.

수학의 개념들을 프로그래밍 개념들로 만들 때 수학자들이 컴퓨터라는 걸 상상하고 만들 때 수학 용어들을 가져왔기 때문에 매핑이 되어 있지만 
"프로시저와 함수" 라고 구분해서 부르는 경우들이 있다. (대부분의 요새는 함수라 부른다)

수학에서 사용하는 카테고리란 개념이 있다. 정수론, 집합론등 수학의 부류들을 나타낼 때 카테고리라 부르는데 그런애들을 프로그래밍에서는 카테고리들을 타입이라는 분류로, 집합으로 나타내고 있다. (차용하고 있을 뿐이지 100% 매핑되는 것은 아니다.)

차이가 있기 때문에 functional programming 이라고 불렀던 것이다.

<img width="725" alt="image" src="https://user-images.githubusercontent.com/74404132/127384577-133ac428-589c-44c1-80d3-e5b55a8811ca.png">
 
<br/>

<br>
<li> Category Theory (범주론)
프로그래밍 관점에서 이 카테고리들을 타입으로 매핑한다고 했다.

<img width="580" alt="image" src="https://user-images.githubusercontent.com/74404132/127384864-3b2a8c5d-5afd-46f4-a268-36f3c5efe3c8.png">


X -> Y  
정수론을 집합개념으로 morphing할 수 있다 라고 얘기한다.

이걸 또 다른 카테고리로 morphing 하는 거면, 두 가지를 결합해서 사용할 수 있다.

그 두가지는 같은 것이다 를 증명한 게 Category Theory (범주론) 이다.


이게 프로그래밍에서도 int type -> string type -> double type 일때
그걸 합쳐서 변환하더라도 동일하게 한번에 변환할 수 있는거라고 생각하자.

   결합법칙(composition) 이 타입변환을  마치 함수를 가지고 변환하는 걸로 만들 수 있는데 
   다른 두 가지를 결합해서 한꺼번에 변환하는 걸로 만들 수 있다! 
이런게 가능하다로 수학의 범주론에 매핑해서 생각하자. 
<br/>


<br>

<li> 함수 중심 프로그래밍의 정의 <-> 객체 중심. 둘은 다르다.
함수 중심 프로그래밍에서는 함수의 계산으로 데이터 상태를 다 처리하려고 노력하는 것이다.

자료처리를 수학적인 함수의 계산으로 표현을 하고 상태나 가변 데이터 대신에 불편 데이터를 사용해서 표현하는 게 함수형 프로그래밍에서 지향하는 바이다.

cf) 요즘 framework 에서는 클래스들도 immutable, mutable 클래스를 분리해서 만들어 논 언어들이 있다.

함수 중심프로그래밍에서 얘기하는 다섯가지:
1. 순수 함수로 만들어야 한다
2. 값들은 불변타입을 사용한다
3. 일급 함수와 고차 함수를 사용한다
4. 자동으로 메모리 관리를 한다
5. 타입을 추론해주는 타입 시스템이 지원된다.

<img width="1116" alt="image" src="https://user-images.githubusercontent.com/74404132/127386240-fad6a7d6-cac9-498b-b962-a06c3e2c2b97.png">

<br/>

<br>
<li> 순수함수란? 



1. 부작용(side effect)이 없다 : 그 함수 안에서 처리하는 게 바깥에 있는 것에 영향을 주지 않는다 (부작용: 기대하고 있는 것 외의 부수적인 효과. 부가적인 내용을 얘기하는 것이다, 결과적으로 무조건 나쁜거라고 할 수는 없다.)

순수함수에는 이게 없는 게 좋다.

2. 내부 데이터를 immutable 하게 관리를 하는 것이다.
값이 한 번 저장이 되면 바뀌지 않게끔 계속 사용하는 것이다.
바뀌면 새로운 곳에다가 할당하는것이다

3. 부작용이 없다는 건 다른 말로 참조 투명성이라고 한다.
바깥 거를 참조하다보면 바깥에 영향을 미칠 수 있다.

4. 느긋하게 계산 (뒤에서 추가 설명)

<img width="452" alt="image" src="https://user-images.githubusercontent.com/74404132/127386912-752ed593-d2ca-4626-aeb2-cc100c63669d.png">

<br/>


<br>
<li> 순수한 함수?
입력값이 항상 같은 값이 들어갈 때마다 결과값이 동일함이 보장되기 때문에 테스트 하기가 수월하다.


<img width="759" alt="image" src="https://user-images.githubusercontent.com/74404132/127387150-f279e54b-8dc0-4a22-95b4-44d96ff01037.png">


random 같은 것들은 어떤 값이 나올 지 모른다.

이걸로 함수를 만들 때 어떤 식으로 만드는 지 생각해 보자.
locality라고 표현을 하기도 한다. 
    함수 내부에 로컬 영역에서만 무언가 일어나고 그거에서만 결과적으로 값이 처리가 되고 리턴이 되는것이다. 다른 값은 탐조하면 투명하지 않기 때문에 순수하지 않은 함수가 될 수 있는 것이다.





<br/>

<br>
<li> 익명 함수 vs 클로저

함수도 하나의 클로저일 뿐이다.
클로저는 더 상위 개념으로 함수뿐만아니라 다른 표현들도 클로저라고 부른다.

변수를 할당하거나 인자값으로 넘기거나 할때 클로저를 선언해서 바로 expression 으로 넘길 수 있는 것이다. 함수와 크게 다르지 않다.

이름없는 함수와 클로저는 구분하자.
함수를 만들 때 보통 함수 이름을 지정을 해주는데, 이름을 지정하지 않고도 함수를 선언할 수 있다.

    let closure =
    (function(n) {return n*n;})

함수지만 이름이 없는 상태도 클로저로 표현할 수 있다

클로저라는 의미는 그 클로저를 선언한 범위에 있는 코드가 해석될 때 클로저 바깥에 있는
바깥의 값응 그대로 캡쳐해서 닫아버린다. 이게 기본 컨셉이다

    JS의 클로저는 바깥의 변수들 중 객체들을 참조할 수 있어야 하다 보니까 대부분 reference. 변수로서 사용된다. 이게 함수형에서 얘기하는 바람직한 내용을 아니니 바깥을 참조하지 않고 순수하게 만들 수 있는 방법들을 활용해보자.

<img width="1792" alt="image" src="https://user-images.githubusercontent.com/74404132/127388540-a9c906bc-19af-4ed0-be03-840f6e8660d6.png">


<br/> 

<br> 

<li> 함수형 프로그래밍은 재귀 호출을 쓴다.
반복문을 쓰지 않고 함수로만 흐름 제어를 다 구현할 수도 있다.

    function factorial(n){
      function factorialInner(n, acc){
        if(n == 0){
          return acc;
        }
        return factorialInner(n-1, acc * n);
      }
      return factorialInner(n, 1);
    }

리스비, 스킴 함수로만 처리하다보니 포문과 결국 비슷한것.

<br/>

<br>

<li> lazy evaluation

보통은 우리가 적극적인 계산 방식으로 처리를 많이 한다.
 = eager evaluation
 컴파일 하면서 계산 해야하는거면 이미 계산해서 미리 메모리에다 사용하던 안하던 저장해논다
 함수형에서는 메모리 최적화를 위해 바로 계산하는 게 아니라
 0, 1, 2, 3 element로 접근하지 않는이상은 미리 계산을 안해놓는 것이다.
 JS 는 lazy property, 함수 제공이 된다.

접근 되기 전까지 계산이 되지 않는다

왜? 함수는 새로운 걸 복사해서 활용하는 건데
복사하는게 실제로는 그 메모리에 lazy op 가 적용이 돼서
복사하더라도 그대로 메모리를 참조하고 있다가
그 메모리를 접근할때. 실제로 필요해서 사용할 때 뒤늦게 사용할때 복사된다.
이게 최적화 기법으로 많이 사용된다.

<img width="766" alt="image" src="https://user-images.githubusercontent.com/74404132/127393001-fdfc1df6-9540-401f-b7c4-f31d6d09fdb6.png">

<br/>


<br>

<li> 함수형 프로그래밍 타입

타입을 수학적 category theory 에서 가져왔는데,
그러다보니 functor 나 monad 용어들이 나온다.
순수 함수형 언어들에선 이걸 부르고 강조하는 경우들이 있다

우리가 다루는 언어들에는 이게 명시적이진 않지만 그 개념을 알아둘 필요는 있다

monad 란 카테고리들 중에 변환했을 때 자기자신의 카테고리로 돌아오는 것.
카테고리가 변환이 됐는데, 자기와 똑같은 카테고리로 변환이 된 것.

functor: 다른 카테고리로 변환되는 경우


<img width="633" alt="image" src="https://user-images.githubusercontent.com/74404132/127393374-8cc84f1a-6e86-446f-8eea-fb60bffb5310.png">


타입 중에선 어떤 타입의 부류들이 있는데 타입끼리 변환이 있다

그중에서도 모나딕한 타입들은 자기 자신으로 변환.
변환하면 자기자신으로 변환이 되는것
대표적인 게 매핑
array to string
int 배열에서 string 배열로 바뀌는 것.
안에 있는 애들이 매핑이 가능한 구조가 되기 때문에
 배열은 모나딕 하지 않는 대표적인 예긴한데

 optional 같은 애들은 매핑하면 optional 이 된다. ************

 파스칼에서는 모나드 타입을 굉장히 중요하게 생각한다.
immutable 하게 처리하는 걸 중요하게 생각하기 때문 




<br/>

<br>

<li> 배열은 모나딕하지 않지만 매핑하는 데 있어서 중요한 개념이 된다
반복하면서 transform 하는 closure 로 변환해 주는 것.

func myMap<T> (_ transform : (Element) -> T) -> [T] {
  var result: [T] = []
  for item in self{
    result.append(transform(item))
  }
  return result
}

맵 함수: 변환


<img width="650" alt="image" src="https://user-images.githubusercontent.com/74404132/127394125-c6946f01-035c-498d-afec-201bd5ad4d97.png">

<br/>


<br>

<li> 고차함수: filter, map, reduce
이런 애들 사용해서 closure 을 넘겨서 주면 그 클로저가 그 요소들에게 다 반영이 돼서
표현식으로 사용이 되는 것이다.

    let nums = [1, 2, 3, 4, 5, 10, 11, 12];
    let filtered = nums.filter(
          value => {return value > 10; } ) // 참 이런하는 거만 가져온다.

    let reduced = numbers.reduce( (prv, cur) => prv + cur);

    let nilNumbers = [1, 2, undefined, 4, 5];
    let mapNumber = nilNumbers.map(val => [value]);
    // [[1], [2], [undefined], [4], [5]]

    let mapnumberOnly = 
      nilNumbers.flatMap(val => [value]);
    // [1, 2, undefined, 4, 5] ?????? null 이 있는지 확인하는 기능이 제공됐다

맵 리듀스 필터를 어떤식으로 쓸까?
리듀스를 문자를 연산할때 사용할 수가 있다.
리듀스를 어떤식으로 줄여나가는 과정들을 살펴보자


<br/>


<br>

<li>  커링과 함수합성

    category theory 얘기할 때 composition 이 되게 중요하다고 말했다.
    커링과 함수 합성을 사용하면 다양한 표현을 풍성하게 만들 수 있다.

    const plus = ( (a, b) => {return a + b})
    cons multi = ( (a, b) => {return a * b}) // 클로저 만들고

    function calculate(method){ // 재귀 만든다음에
      return function(v1){
        return function(v2){
          return method(v1, v2)
        }
      }
    }

    calculate(plus)(10)(3) // 이 함수 내에 중첩 함수 두 개 있으니 파라미터 순서대로 붙여줘야 실행이 된다.

    let adder = calculate(plus) // 이 계산기를 더하는 용으로만 쓰겠다는 뜻
    calculate(plus) 이 앞 부분만 변수로 저장한다

    let adder100 = adder(100) // 더하는 계산긴데 무조건 100 + a 해주겠단 뜻


<img width="688" alt="image" src="https://user-images.githubusercontent.com/74404132/127400471-d0f25fb4-c1ee-4369-ba8e-f889041c36eb.png">


<br/>


<br> 

<li> 요약 FP vs OOP
이 두 개념이 완전히 대비되는 게 아니다
OOP 클래스를 만들면서도 순수한 함수를 만들 수 있다.
OOP 타입 자체도 immutable 한 타입으로 만들 수 있다. (권장하고도 있다)
OOP 에서 작은 단위로 뭔가를 만들 때 1급함수, 고차함수들을 활용해서 풍성하게 만들 수 있다
세부적인 동작을 추상화할수 있는 방식을 제공하기 때문에 훨씬 좋은 표현식을 만들 수가 있다.

* 메모리 관리 측면에서도 immutable한 타입을 어떻게 하면 선언적으로 잘 해볼 수 있을 것인가, 

* OOP 객체도 variable 을 많이 만들기 보다는 메모리 관리를 static 하게 다룰 수 있는 걸 heap 쓰지않고 stack에서 사용할 수 있는 게 얼마나 많이 있는 지 살펴보자.

* 함수형 프로그래밍에서도 solid 원칙이 얼마나 섞일 수가 있는지 같이 고민해보자




<br/>


  const isSquared = (num) =>
    Number.isInteger(Math.sqrt(num)) ? "squared" : "";
  return isAbundant(num) + isPerfect(num) + isPrime(num) + isSquared(num);
};

const isSquared = (number) => {
    return [...factors(number)].filter(factor => factor * factor === number)[0];
}

module.exports.isPerfect = isPerfect;

const mission = require('./mission1');

    Array.from(Array(100).keys())
        .map((x, i) => i + 1)
        .map(data)
        .reduce((cumulative, currnetValue) => { console.log(currnetValue)} );