---
layout: post
title:  "http request analysis"
excerpt: "reviews"


categories:
  - Blog
tags:
  - [Blog, jekyll, Github, Git]

 
date: 2021-08-10
last_modified_at: 2021-08-10
---
왜 필요한가?

웹 브라우저에서 특정 홈페이지에 접속하는 과정을 이해하는 것은 중요하다. HTTP 요청이 하나만 전송되는 것이 아니라 HTML 페이지 내용에 따라서 연결되는 HTTP 요청과 리소스 다운로드 흐름을 이해해야 한다.

이런 과정을 학습하는 데 도움이 되는 웹 브라우저 개발자 도구에서 네트워크 탭의 동작을 따라서 구현해보면서 HTTP 요청과 응답 흐름을 이해할 수 있다.


학습 목표

웹 브라우저 개발자 도구에서 네트워크 탭의 동작을 따라서 구현해보면서 HTTP 요청과 응답 흐름 살펴보는 것을 목표로한다.

로컬 메모리 캐싱 방식으로 페이지 로딩이 빨라지는 지 확인한다.




1. HTML 페이지 내용에 따라서 연결되는 HTTP 요청과 리소스 다운로드 흐름

http로 받은 페이지에는 글 만 있는 게 아니라 사진, url등 리소스가 같이 담겨 있다.
이들을 제대로 가져오기 위해서는 리소스 마다의 http 요청이 추가로 필요하다.

리소스 다운로드의 흐름? 링크가 있다면 위에서부터 차례대로 알아보지 않을까
메타데이터는 어떻게 바라보면 될까?


2.  웹 브라우저 개발자 도구에서 네트워크 탭의 동작을 따라서 구현해보면서 HTTP 요청과 응답 흐름을 이해할 수 있다.

웹 브라우저 개발자 도구

퍼블리싱된 웹을 검수할 때 어떤 기준으로 검수해야 할지 막막
개발자도구를 사용하게 되면 개발자와의 원활한 소통은 물론, 때에 따라 손쉽게 디자인 테스트를 해보며 바뀌는 화면을 라이브로 볼 수 있다는 장점이 있습니다.
눈여겨본 웹사이트가 어떤 구조로 이루어져 있고, 어떤 스타일이 들어갔는지 참고하기에도 매우 유용한 도구입니다.


1.. 크롬 개발자 도구란?

구글에서 만든 웹 브라우저인 크롬에는 개발을 도와주는 다양한 도구가 기본적으로 제공됩니다. 이를 개발자 도구라고 합니다.
개발자 도구를 이용하면 HTML, CSS, JavaScript의 생산성을 극대화할 수 있습니다. 언뜻 보면 개발자를 위한 도구인 것 같지만, 글자 크기, 색, 간격 등 정확한 값을 확인해야 하는 디자이너에게도 없어서는 안 될 매우 중요한 도구입니다.

맥은 <command+option+I>

https://blog.rightbrain.co.kr/?p=11693

<img width="648" alt="image" src="https://user-images.githubusercontent.com/74404132/128674293-d64704d9-ec5f-4b12-a508-3fab83a57320.png">


개발자 도구 파악하기 어렵다. 수강 시작.

https://www.youtube.com/watch?v=x4q86IjJFag

google chrome dev tools.

for web dev, using chrome dev tools is highly recommended 



https://stangricki.github.io/Website-Mizuxe/https://stangricki.github.io/Website-Mizuxe/

<img width="813" alt="image" src="https://user-images.githubusercontent.com/74404132/128677206-2ca73183-647d-4327-9394-a26e0977770b.png"> 

there are even more tools.

memory management 에 캐시 관련 있지 않을까?


![image](https://user-images.githubusercontent.com/74404132/128677572-fbfed186-8071-4448-91b6-9d83cbefa646.png)

다른 기기 버전을 볼 수 있음


elements 로 모든 source code (프론트) 를 볼 수 있다.
클릭하는 것마다 해당되는 css 가 나타난다.

글자별로 색깔이 다름 - padding in margin

스트링 소스 코드를 패딩해서 보며준다!


1. 브라우저 누르고 html 돌아다니면 어디 가리키는지 표시해 준다.

2. 화살표 누르고 웹 돌아다니면 그에 해당하는 코드 보여준다

mt-5, pt-5 : bootstrap class ?? 

bootstrap css 어느줄 쓰는지 직접 들어가준다.

bootstrap 이란?
https://www.toptal.com/front-end/what-is-bootstrap-a-short-tutorial-on-the-what-why-and-how

powerful toolkit - a collection of HTML, CSS, and JavaScript tools 


it is responsive by design, it maintains wide browser compatibility, it offers consistent design by using re-usable components, and it is very easy to use and quick to learn

<img width="678" alt="image" src="https://user-images.githubusercontent.com/74404132/128683333-e3af98bd-a0de-4555-9bfc-f28005876ca4.png">

uncheck this class : 화면에서 사라진다. 스샷찍을때 광고 없앨떄 이 기능 이용하면 되겠다.
 : toggle classes

 pt-5 .cls 이런식으로 가면 된다.

  * <div class> 이런게 bootstrap의 클래스 였다!

 
3. html 내용물 바꾸기. 해당 요소 클릭하고 elements 더블클릭해서 글씨 바꿀 수 있다!
add workspace 해서 바꾼 내용물 저장해서 갖고 있을 수 있다. 


hide element : 공간은 그대로
delete element : 공간도 없앤다
![image](https://user-images.githubusercontent.com/74404132/128683969-5278fd3d-8370-43fe-801f-373dfe617378.png)


mov thing around 도 가능하다!
copy element 후 
paste, scroll into view 하면 바귄 거 볼 수 있다.

그냥 click and drag 도 가능하다

4. see different state in element:
right click hovor : hovor state 되고 active, visited,, 등 할 수 있다

5. 컬러 바꾸기
bg ~ 로 색깔 바꿀 수 있다.

![image](https://user-images.githubusercontent.com/74404132/128684637-c40240e5-935a-4e92-bab3-7bca64396d36.png)

색깔 고르기.
navbar has box shadow. 여기서 하기

6. computed 누르면 해당 요소의 상세 정보 스림으로 볼 수 있다


7. console 창 에서 js 실행할 수 있다.. 
alert(1)

8. document.querySelector('h1').style.color = 'red'
vanil js

$('h1').style.color = 'blue';
명령어로 색깔 바꾸기

내가 선택한 element 창

9. live server 다운하면 html 띄우는 즉시 갱신된다


10. Network!
shows all of the file that are loading!
![image](https://user-images.githubusercontent.com/74404132/128685935-112a572d-7297-4306-9bb0-4192632ada1b.png)

size, time to load 등 볼 수 있다
ajax request?
ws : live server that im using . auto load 기능이다.

headers 에 들어있는 몇 정보를 내가 구현하면 되겠다.

![image](https://user-images.githubusercontent.com/74404132/128686265-04601f42-8e7b-4293-a232-8f9dc3040b4f.png)

add ajax request?
<button>  </button>
document.querySelector('button').addEventListener('click', getUsers);

        fucntion getUsers(){
            // fetch data
            xhr = new XMLhttpRequest(); // asyn ajax call 이다.
            xhr.open('GET', 'https:// ~ ', true);

            xhr.onload = function(){
                var users = JSON.parse(this.responseText);

                consol.log('Users returned');
            }
            xhr.send();
            
            // response 쪽 가면 json 형식으로 요청해서 받은거 볼 수 있다.
        }

받는거 저장하는 작업이 time 걸리는 거 같은데?

11. about network tab
https://developer.chrome.com/docs/devtools/network/



use the Network panel when you need to make sure that resources are being downloaded or uploaded as expected.

Making sure that resources are actually being uploaded or downloaded at all.
Inspecting the properties of an individual resource, such as its HTTP headers, content, size, and so on.



미션

node 기반으로 콘솔에서 동작하는 프로그램을 작성한다.

웹 브라우저 개발자 도구 > 네트워크 탭에 나오는 것처럼 HTTP 요청을 보내고 받는 과정들을 분석한다.

 - > 요청받은 애들의 header 요소별로 정리해 ㅍ시하는 걸 직접 parse 해서 구현하는 것 같다.


 
분석 요구사항

웹 브라우저처럼 URL을 입력하면 해당 주소로 요청을 보낸다.

http/https 모듈을 활용해서 요청을 보내고 응답을 받는다.

 https.request 메서드를 이용해서 https 요청을 보낼때 포트 번호를 https일 경우 443으로 줘야 한다고 한다.

HTTP 또는 DOM Parser 모듈을 활용해서 응답에 포함된 HTML 을 분석한다.
HTML에 포함된 요소들 중에서 script 태그의 src 속성, img 태그의 src 속성에 있는 주소도 다시 요청을 보내서 받는다.

        fucntion getUsers(){
            // fetch data
            xhr = new XMLhttpRequest(); // asyn ajax call 이다.
            xhr.open('GET', 'https:// ~ ', true);

            xhr.onload = function(){
                var users = JSON.parse(this.responseText);

                consol.log('Users returned');
            }
            xhr.send();
            
            // response 쪽 가면 json 형식으로 요청해서 받은거 볼 수 있다.
        }


src, imp 등 주소 리다이렉션 
https://developer.mozilla.org/ko/docs/Web/HTTP/Redirections

URL 리다이렉션 혹은 URL 포워딩은 페이지 따위의 실제 리소스, 폼 혹은 전체 웹 애플리케이션이 다른 URL에 위치하고 있는 상태에서 링크를 존속시키는 기술입니다. 
??

모든 요청을 보낸 시각, 요청에 대한 응답을 받은 시각, 다운로드가 끝난 종료 시각을 모두 기록한다.

요청부터 응답까지 시간을 응답 대기 시간으로 표기한다.

대기시간과 다운로드 시간?
TTFB 와 관련 돼 있다.
https://developer.chrome.com/docs/devtools/network/reference/

자바스크립트 경우에는 perf_hooks 나 axios 쓰시면 axios.interceptors 라는게 있다


응답 시작부터 마지막까지 다 받은 시간을 다운로드 시간으로 표기한다.

https://blog.risingstack.com/measuring-http-timings-node-js/

TTFB 시간이란?


DNS (Domain Name Servers): DNS is a hierarchical decentralized naming system used to resolve human-readable hostnames like risingstack.com into machine-readable IP addresses.

IP 주소 사람이 읽을 수 있는 도메인



timeline of HTTP request

DNS Lookup: Time spent performing the DNS lookup. DNS lookup resolves domain names to IP addresses. Every new domain requires a full round trip to do the DNS lookup. There is no DNS lookup when the destination is already an IP address.

TCP Connection: Time it took to establish TCP connection between a source host and destination host. Connections must be properly established in a multi-step handshake process. TCP connection is managed by an operating system, if the underlying TCP connection cannot be established, the OS-wide TCP connection timeout will overrule the timeout config of our application.

TLS handshake: Time spent completing a TLS handshake. During the handshake process endpoints exchange authentication and keys to establish or resume secure sessions. There is no TLS handshake with a not HTTPS request.

Time to First Byte (TTFB): Time spent waiting for the initial response. This time captures the latency of a round trip to the server in addition to the time spent waiting for the server to process the request and deliver the response.

Content Transfer: Time spent receiving the response data. The size of the response data and the available network bandwidth determinates its duration.


<구현 계획>

<img width="724" alt="image" src="https://user-images.githubusercontent.com/74404132/128691523-52bef130-b194-47d1-8ea9-91b50e8af113.png">


처음에 url 인풋 한 번만 받는다.

크롤링 순 ( 리다이렉션 된 순) 으로 network처럼 헤더정보 출력한다.
대기시간, 다운로드 시간은 시간을 재는 것일까?

도메인 개수 : 12개

요청 개수 : 219개

이미지(png, gif, jpg) 개수 : 152개

코드(css, js) 개수 : 28개

전송 용량 : 6.93MB

리다이렉트 개수 : 1개

전체 로딩 시간 : 444ms



가장 큰 용량 : tpfxef.png 3.12MB

가장 오랜 대기 시간 : m.naver.com 43.3ms

가장 오랜 다운로드 시간 : tpfxef.png 1314.4ms



URL 입력 후 HTTP 요청 보내기 구현

HTML 파싱 - src 속성 탐색 구현

응답 대기 시간 측정 및 출력

다운로드 시간 측정 및 출력

요청 도메인 개수 측정 및 출력

전체 요청 개수 측정 및 출력

전체 이미지 개수 측정 및 출력

전체 코드 개수 측정 및 출력

전체 전송 용량 측정 및 출력

리다이렉트 개수 측정 및 출력

응답 - 리소스 메모리 캐싱 구현

캐싱 데이터 측정 및 출력

Httpanalysis '가' 캐시메모리 이용해야 할 것같아.
맵에 들어있는지보고 들어있으면 cache hit! 띄우고 

if url in map
map[url] 둘다 써야하나? 
그럼 저거 타임 둘다 받아야하는 거 아닌가

        function charOccurances(str) {
        var myMap = {};
        if(str.length!==0){
            for (let i = 0; i < str.length; i++) {
            myMap[str[i]] = (myMap[str[i]] || 0) + 1;
            }
        }
        return myMap;
        }

<img width="752" alt="image" src="https://user-images.githubusercontent.com/74404132/128704007-c1d38562-2916-4956-956f-577bcbd23072.png">


const str = "AbABaaaa";
console.log(charOccurances(str));

도메인 개수 : HeaderManager() 얘가 파서 받아서 하나씩 뭔지 파악하고 저장한다.

요청 개수 : 219개

이미지(png, gif, jpg) 개수 : 152개

코드(css, js) 개수 : 28개

 * 뭐가 css 이고 뭐가 js 인지 어떻게 알아? 일단 전송 받아보자
 HTTPS, HTTP 노드 코어 내장 모듈

전송 용량 : 6.93MB
글자 하나당 1byte로 가져가자
먼저 string 받고 용량 출력하고 HeaderManager에 보내야하나
?

리다이렉트 개수 : 1개
리다이렉트를 어떻게 하지?
300 status 들어오면 숫자 카운트 1만

전체 로딩 시간 : 444ms


TopFeatures

가장 큰 용량 : tpfxef.png 3.12MB
Lsrgest = max(Largest, this)

가장 오랜 대기 시간 : m.naver.com 43.3ms

가장 오랜 다운로드 시간 : tpfxef.png 1314.4ms