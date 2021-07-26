---
layout: post
title:  "xml Parser"
excerpt: "reviews"


categories:
  - Blog
tags:
  - [Blog, jekyll, Github, Git]

 
date: 2021-07-26
last_modified_at: 2021-07-25
---


컴파일러 : 고급언어를 기계어로 매핑하는데,
고급언어로 넘어가면서 어셈블리어로 일대일 매칭하기 힘든 함수, 객체지향이 생겼다

컴파일러는 소스코드를 파싱해서 AST(Abstract Syntax Tree) 자료구조를 만들어낸다
이 트리를 검사하고 최적화하고 정해진 기계어로 대치해서 나온다.

AST 관점에서 연산자 우선순위를 적용하기. 



## 주제: XML를를 분석해서, 트리구조로 만들기

프로그래밍에서 사용하는 토큰의 종류
identifier : HTML, BODY
keyword : 미리 지정한 예약어
separator : <, >, [, ] 등 글자를 구분하기 위한 문자
operator 
literal : true, NULL, 3.14, "hello"
comment : <! 코멘트는 무시한다>


throw, try~catch 활용하기.
실행중 함수에서 throw 던지면 호출한 상위함수에서 에러 전달받을 수 있다.
에러 전달전달 받아서 메인함수에서 예외출력하면 되겠다

정규표현식: 특정한 언어로 표현하는 규칫이나 매치하는 용도
ex) 이메일패턴, 문자열패턴, 숫자패턴


XML은 여전히 정형화된 데이터를 표현하는 데 많이 사용하는 방식이다. 간단한 구조의 HTML5 문서를 분석해서 DOM 구조로 만드는 XML Parser를 직접 만들어보는 것은 효과적인 학습 방법이다.


regular expression: writing patterns to match char

<p>


<li> \d 문법: 0~9 찾기,  \w 문법: 단어 찾기
can be used in place of any digit from 0 to 9.

 pattern matches anywhere within the string, not just starting at the first character.

 <img width="751" alt="image" src="https://user-images.githubusercontent.com/74404132/126930838-84e202ac-f2da-4124-87b7-2e57411379ca.png">

<br/>

</p>


<li> . 문법: 다찾기

wildcard: use dot
you are often matching pieces of text that you don't know the exact contents of, other than the fact that they share a common pattern or structure 
you need to escape the dot by using a slash \. accordingly.

varying characters but the same length. Try to write a single pattern that can match the first three strings, but not the last (to be skipped).


길이같은거 다 찾기: .으로
신경안쓸건 \. 으로

you need to escape the dot by using a slash \. accordingly.


. 찾는지 와일드카드 쓰는지 모르므로
\. 를 진짜 점찾는 걸로 설정되었다.

. 한개짜리 다찾기
.. 두개짜리 다 찾기


앞에 세개는 다르고 뒤에 하나가 점이다: ...\.

<img width="759" alt="image" src="https://user-images.githubusercontent.com/74404132/126931181-5a18a0d6-485f-4c0d-9b88-e4a81bd27b03.png">


<br/>

<li> [abc] 문법: 브래킷 안에 있는 문자열중에서만 찾기
"(abc) def-ghij" 같이 다 찾는게아니고 번호만 찾으려면?
[abc] 하면 single a, b, c 중에서만 찾아준다.

<img width="744" alt="image" src="https://user-images.githubusercontent.com/74404132/126931659-66825c13-5056-41a9-be08-0a4fc68e19cc.png">

<br/> 

<p>

<li> [^a] 문법: 얘 빼고 다 찾기

<img width="768" alt="image" src="https://user-images.githubusercontent.com/74404132/126931847-6cff4a52-711c-4762-8de3-e91117952301.png">


</p>

<p>

<li> [0-6] dash 문법: ascii 순서 기준으로 범위 설정
범위 여러개 있으면 붙여서 쓴다

<img width="804" alt="image" src="https://user-images.githubusercontent.com/74404132/126932150-85932450-4f1c-4613-ad88-645b77e2143b.png">

</p>

<p>

<li> 같은 문자 {1,3} 문법

<img width="768" alt="image" src="https://user-images.githubusercontent.com/74404132/126932271-8b39b728-6c78-4bf4-bec6-4a38203d99df.png">

</p>


<p>
<li> 0개이상 * , 1개이상  + 문법

<img width="771" alt="image" src="https://user-images.githubusercontent.com/74404132/126932546-812d40c7-f976-4a15-be88-c74ac19ba0a0.png">

</p>


<p>
<li> 0개이상 * , 1개이상  + 문법

<img width="771" alt="image" src="https://user-images.githubusercontent.com/74404132/126932546-812d40c7-f976-4a15-be88-c74ac19ba0a0.png">

</p> a?z a z 사이에 문자 있어도, 없어도 된다. \?와 구분한다.

<img width="792" alt="image" src="https://user-images.githubusercontent.com/74404132/126932718-bfcaed07-8da9-4f03-b104-5f3a52251c51.png">


<p>

<li> \t \n \s 공백처리문법

<img width="781" alt="image" src="https://user-images.githubusercontent.com/74404132/126932898-e1ad79c7-12cc-4dbb-83b3-ffa46ce12394.png">


</p>


<p>

<li> 무조건 이걸시작, 앞에 아무것도 없이 돼있는거맞 찾는 ^succesful$ 문법

<img width="742" alt="image" src="https://user-images.githubusercontent.com/74404132/126933167-82e168c8-0f93-45df-bfbf-081caacfc130.png">


</p> 

<p>

<li> 정확히 일치는 \b \b 경계를 쓴다

    front.match(/\b(P|p)\b/)

</p>

<p>
<li> +, * 범위를 제한하는 () 문법. 

<img width="780" alt="image" src="https://user-images.githubusercontent.com/74404132/126935589-aeeb5215-674e-4e16-8123-0ed4e69c72c4.png">

<br/>


( () )겹쳐서 쓸 수 있다
<img width="752" alt="image" src="https://user-images.githubusercontent.com/74404132/126935960-fc4e0db4-1b9f-40b9-b359-91df573d0384.png">

</p>


<p>
<li> | 문법: 이중안에 있으면 가져온다

<img width="762" alt="image" src="https://user-images.githubusercontent.com/74404132/126936258-71ace7e8-cc1b-4020-95a7-e48f71045eb3.png">
<br/> 


</p> 


<p>
<li> \D \W \S 얘네 뺀 아무거나 다른거 가져오기

<img width="762" alt="image" src="https://user-images.githubusercontent.com/74404132/126936258-71ace7e8-cc1b-4020-95a7-e48f71045eb3.png">
<br/> 


</p> 



<p>
<li> \2-\1 가져올 떄 순서 바꾸기

<img width="762" alt="image" src="https://user-images.githubusercontent.com/74404132/126936258-71ace7e8-cc1b-4020-95a7-e48f71045eb3.png">
<br/> 

    import re
    s = 'How are you guys today'
    print(re.sub(r'(\w+)(\W+)(\w+)', r'\3\2\1', s))
    # => are How guys you today


</p> 


추가 문법 참조: https://beomy.tistory.com/21



js에서 정규표현식 이용하는법:
1. 쓸 정규표현식 문법은 변수에 저장한다. 그 문자열을 / ~ / 안에 넣는다.

    정규표현식: <(!.+) (.+)><HTML
    const pattern = /<(!.+) (.+)><HTML+/

2. 정규표현식.exec(쓸문장)

  const ans = pattern.exec(str)

<br/>
예시



    const str = "<!DOCTYPE html><HTML lang=\"ko\"><BODY><P>BOOST<IMG SRC=\"codesquad.kr\"><BR/></IMG></P><P>CAMP</P></BODY></HTML>";

    const pattern = /(<.+>{1})<(BODY.+)/
    const ans = pattern.exec(str)
    console.log(ans)

<img width="675" alt="image" src="https://user-images.githubusercontent.com/74404132/126938279-3ffdafa6-d2f5-459d-8f35-a6b596fe541c.png">
잘 찾아진다!

<br/>
<br/>
<br/>


## 문자 처리를 tokenizer, lexer, parser 세 단계로 나눈다.

Tokenizer, Lexer 의 역할을 합하여 Lexical anlyze라고 한다. Lexical Analyze란 의미 있는 조각을 검출하여 토큰을 생성하는 것을 말한다.

<img width="816" alt="image" src="https://user-images.githubusercontent.com/74404132/126938670-d895eb7a-c2af-4b00-a626-31b078ff1881.png">

참조: https://velog.io/@mu1616/컴파일러-이론에서-토크나이저Tokenizer-렉서Lexer-파서Parse-의-역할



## 태그들이 내부 중첩인지 아닌지, 그 사이 문자열이 뭐인지 어떻게 알까?
<p>

### 맨앞 <> 만 뽑는법:


    const el = />.+/
    const tmp = el.exec(str)
    console.log(tmp)
    const ans2 = str.replace(el, "")
    console.log(ans2)

<img width="768" alt="image" src="https://user-images.githubusercontent.com/74404132/126941808-726fb2ed-884d-4a9d-8a55-2a6d6c97bffd.png">

    ans2 는 뽑힌 <>, 뽑힌애 앞뒤 매치하지않으면 execption 처리한다.
    tmp 는 나머지 애들

    console.log(ans2[0]) 하면 결과 문자열만 받는다



    마지막 <> 이면 null인 걸 이용하자.

</p>


<p>

### 맨뒤 <> 만 뽑는법:
    const el = /^.+<+/
    const tmp = el.exec(str)
    console.log(tmp)
    const ans2 = str.replace(el, "")
    console.log(ans2)

<img width="709" alt="image" src="https://user-images.githubusercontent.com/74404132/126942475-aae3def2-04d0-42ca-ba2c-49ad882a37a9.png">

</p>



<p>

### p 들의 사이는 병렬적이다! 재귀로 받으면 안된다


    <!DOCTYPE html>
      <HTML lang=\"ko\">
          <BODY>
              <P>BOOST<IMG SRC=\"codesquad.kr\"><BR/></IMG></P>
              <P>CAMP</P>
          </BODY>
      </HTML>


<p> </p> 를 수직처리하니까 파싱에 문제가 생겼다

<img width="544" alt="image" src="https://user-images.githubusercontent.com/74404132/126945517-3c6604dc-5232-4ab6-98c6-e1621b4a9670.png">


### JS stack 구현하는 법

    class Stack {
      constructor() {
        this._arr = [];
      }
      push(item) {
        this._arr.push(item);
      }
      pop() {
        return this._arr.pop();
      }
      peek() {
        return this._arr[this._arr.length - 1];
      }
    }

    const stack = new Stack();
    stack.push(1);
    stack.push(2);
    stack.push(3);
    stack.pop(); // 3


</p>
### 파싱기 설계도
<> 안에 <> 계속 있으면
string 으로 먼저 받고 
재귀함수를 콜한다



<p>

<li> try catch

    function getMonthName (mo) {
      mo = mo-1; // Adjust month number for array index (1=Jan, 12=Dec)
      var months = ["Jan","Feb","Mar","Apr","May","Jun","Jul",
                    "Aug","Sep","Oct","Nov","Dec"];
      if (months[mo] != null) {
        return months[mo];
      } else {
        throw "InvalidMonthNo"; //throw keyword is used here
      }
    }

    try { // statements to try
      monthName = getMonthName(myMonth); // function could throw exception
    }
    catch (e) {
      monthName = "unknown";
      logMyErrors(e); // pass exception object to error handler
    }


</p>



#### how to check if a variable in an array in JS
    The Array.isArray() method checks whether the passed variable is an Array object.
    Array.isArray([1,2,3]) 이런식으로 써야한다. 



### 중첩스택을 어떻게 출력할까?
스택의 배열 자체는 생성자에서 this._arr 으로 선언 돼 있다

    constructor() {
      this._arr = [];
    }

그래서 Array.isArray(stack) 이 아닌  

Array.isArray(stack._arr) 이런식으로 중첩 스택인지 확인해야 한다.

P P 세트인데 paraphrased 이면 그대로 재귀
아니면 파싱
앞뒤 태그 엇갈리면 에러

재귀할때 슬라이스해서 가져가지 함수내에서
받은 줄을 조정하지는 않는다.


### exception loc 보는 법
node --trace-uncaught reg_ex.js 


### reg expression replcement
    rightOperand.replace(/\"/g,"")}

  다 지우려면 /다음에 g


  // attributes 갖고있으면 안에서, 아니면 밖에서



### 왜안되냐


the <br> tag is used for line break. 


v1: 단일스택

<img width="477" alt="image" src="https://user-images.githubusercontent.com/74404132/127027910-2d08b69e-006c-4d3c-bcfa-651f29dc8571.png">



There is no "pass by reference" available in JavaScript.


if you are changing a property value of an object or array then it is Pass by Reference.

object1.prop = "car";
array1[0] = 9;

중첩스택 해결이 안된다

<> <>쌍 앞부터
rhef 같은거 많음


예 1) 문단 하나

<img width="543" alt="image" src="https://user-images.githubusercontent.com/74404132/127062768-3e800e50-5733-4b3c-9068-afdf49eed7e5.png">


예 2) 문단 두개 이상

<img width="605" alt="image" src="https://user-images.githubusercontent.com/74404132/127062621-7d18b02f-bcef-41b7-9921-8d091c1de60d.png">


예 3) 잘못된 HTML5 형식 XML을 분석한 경우

<img width="468" alt="image" src="https://user-images.githubusercontent.com/74404132/127062801-ba25d987-079f-4034-937e-0c8c6b489f75.png">


https://lahuman.github.io/nodejs_global/

해야할거

모듈화
<> <> 쌍
스택안에 스택 
개행 깔끔하게
태그안에 설명문 처리?
