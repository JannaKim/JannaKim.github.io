---
layout: post
title:  "C++ grammers"
excerpt: "reviews"


categories:
  - Blog
tags:
  - [Blog, jekyll, Github, Git]

 
date: 2021-07-29
last_modified_at: 2021-07-29
---


<br/>

<li> add chars to string

    string s = ""
    s += 'a';
    s += ('a' + 1);
    s += 65;

char to string from head first
    string(1, 'a' + 1)

<br/> 

<br>

<li> string is char vector
string tmp;
tmp.push_back("a");
tmp.pop_back();

<br/>

<li> std::function

기존 함수포인터의 개념을 확장한 것이다. c++11이후부터는 callable target이 아래와 같이 다양해졌다.

따라서 기존 함수포인터만으로는 이를 cover할 수 없고, 보다 일반화된 개념이 필요해지면서

std::function이 새롭게 나온 것이다.



std::function이 처리할 수 있는 callable target은 아래와 같다.

    function (일반함수)
    lambda expression
    bind expression
    function object (함수 객체)
    class 내의 맴버함수 및 맴버 변수




function<void(int)> go;
        go = [&](int n) { // 밖의 변수들을 인식하겠다는 뜻
        };
      go[0]

        function<void(int, string)> dfs;
            dfs = [&](int idx, string made){
            if(idx == n) {
                if(made.length()) ans.push_back(made);
                return;}

            //int m = Phone[digits[idx] - '2'].size();
            for(auto el: Phone[digits[idx] - '2']){
            //for(int i = 0; i < m; ++i){
                //cout << made + string(1,Phone[digits[idx] - '2'][i]);
                dfs(idx + 1, made + el);
                }
        };


<br>

<li> string vector

            vector<string> a = {
        "",
        "",
        "abc",
        "def",
        "ghi",
        "jkl",
        "mno",
        "pqrs",
        "tuv",
        "wxyz",
    };

<br/>

> 읽어볼만한 글 : https://www.cloudflare.com/ko-kr/learning/bots/what-is-a-web-crawler/

<br/>

    웹 크롤링: 수집한 데이터에 검색 알고리즘을 적용하는 것

<br/>

2. 웹 크롤러 봇

웹 크롤러 봇은 "종자", 즉 알려진 URL 목록에서 시작한다. 

    1. 먼저 해당 URL에서 웹페이지를 크롤링한다.
    2. 이 과정에서 다른 URL에 대한 하이퍼 링크를 찾게 되면, 다음으로 크롤링할 페이지 목록에 추가합니다.

<br/>


3. 메타 데이터 

메타데이터는 데이터를 설명하는 데이터이다

사이트가 무엇에 대한 것인지 알려주는 데이터. 용자가 볼 수있는 웹 페이지의 콘텐츠와 달리 검색 엔진 결과 페이지에 표시되는 경우가 많다. 

<br/>

4. 검색 색인화란?
정보를 필요로 하는 사람에게 인터넷의 "어디에서" 그 정보를 찾을 수 있는지 알려주기 위해 검색 엔진이 만드는 것. "페이지에 대한 메타데이터에" 중점을 둔다.

<br/>

5. 웹 크롤러 작동 방식


웹 크롤러는 크롤링할 페이지, 크롤링 순서, 콘텐츠 업데이트를 확인하기 위해 다시 크롤링하는 빈도에 대해 보다 선택적인 정책을 따른다.


해당 페이지에 중요한 정보가 포함될 가능성을 나타내는 요소인 해당 페이지를 링크하고 있는 다른 페이지 수, 페이지 방문자 수 등의 요소를 기준으로 먼저 크롤링할 페이지를 결정한다.

<br/>

<br/>

6. 웹 크롤링 특징 - 웹 페이지 재방문:

웹 콘텐츠는 지속적으로 변경되거나 삭제되고 새로운 위치로 이동한다. 

그러므로 웹 크롤러는 정기적으로 페이지를 다시 방문하여 최신 버전의 콘텐츠를 색인화해야 한다.

<br/>

<br/>

7. 웹 크롤러 봇이 액세스 허용된 웹과 아닌 웹이 있다.


    웹 크롤러가 콘텐츠를 색인화하려면 서버 자원이 필요하다.

<br/>


웹 크롤러도 서버의 응답이 필요한 요청을 냅니다. 과도한 색인화는 서버 과부하, 대역폭 비용을 고려해서 각 페이지의 콘텐츠 양이나 사이트 내의 페이지 수에 따라, 검색 색인화를 자주 허용하지 않는 것이 웹사이트 운영자에게 유리한 경우도 있습니다.

시지를 맞춤화하거나 페이지 성능을 정확하게 측정할 수 있기 때문입니다. 이 경우, 랜딩 페이지에 "no index" 태그를 추가하여 검색 엔진 결과에 표시되지 않게 할 수 있습니다. 또한, 페이지나 robots.txt 파일에 "disallow" 태그를 추가할 수도 있으며, 이렇게 하면, 검색 엔진 스파이더는이를 크롤링하지 않습니다.

웹사이트 소유자가 다양한 이유로 웹 크롤러 봇이 사이트의 일부 또는 전부를 크롤링하지 못하게 하고자 하는 경우도 있습니다. 예를 들어, 사용자에게 사이트 내의 검색 기능을 제공하는 웹사이트는 검색 결과 페이지를 차단할 수 있습니다. 이들은 대부분의 사용자에게 유용하지 않기 때문입니다. 한 명의 사용자 또는 소수의 특정 사용자에게만 유용한 자동 생성 페이지도 차단해야 합니다.

SEO란? 검색 엔진 최적화
 SEO 마케팅에 있어서는 검색 니즈에 맞춘 콘텐츠 (contents)가 중요하다

SEO의 기술적 요소: 메타 태그 (meta tag), 캐노니컬 태그 (canonical tag) 

웹사이트가 검색 엔진 결과의 상단에 표시되도록 콘텐츠를 검색 색인화에 맞게 준비하는 방식을 말합니다.

node 기반에 라이브러리
Crawler, Axios, Cheerio 등의 node 모듈 패키지를 활용할 수 있다.

 * 크롤링 도구마다 어떤 방식을 사용하는지, 어떤 차이점이 있는지 비교해보기를 권장한다.


    Axios : 브라우저와 Node 환경에서 사용하는 Promise 기반의 HTTP Client로 사이트의 HTML을 가져올 때 사용할 라이브러리입니다.

    Cheerio : Node.js 환경에서 JQuery 처럼 DOM Selector 기능들을 제공합니다. Axios의 결과로 받은 데이터에서 필요한 데이터를 추출하는데 사용하는 라이브

노드 모듈을 설치하려면 npm 이란 패키지 의존성 관리 도구를 설정해서 사용해야 한다.

NPM는 Node Package Manager의 약자이다. 자바스크립트 패키지 매니저이고 NodeJS에서 사용할 수 있는 모듈들을 패키지화하여 모아둔 저장소 역할을 하며 설치/관리를 수행할 수 있는 CLI를 제공한다


package.json

package.json 에는 사용하고 있는 패키지들의 명세가 작성되어 있기 때문에 프로젝트를 다른 사람에게 공유하고 싶다면 package.json을 공유하여 개발 환경을 빠르게 구축할 수 있다. JAVA에서는 Maven의 pom.xml과 비슷한 역할을 한다고 한다.
package.json은 프로젝트 루트에서 npm init -y 명령어로 생성할 수 있다. 방금 명령어로 생성한 파일은 아니지만 개발중인 사오정 서버 프로젝트의 package.json 을 살펴보자


package.json 에서 name 과 version 은 생략할 수 없다. dependencies 에는 프로젝트가 의존하는 패키지들의 이름과 버전을 명시한다. 패키지에서 사용하는 패키지들을 말한다. npm i <패키지명> 으로 패키지를 설치하면 dependencies 에 명시되지 않는다. dependencies 에 명시하려면 npm i --save <패키지명> 을 사용하자. NPM@5부터는 --save가 기본 옵션이라고 한다.
devDependencies 에서는 개발 단계에서만 사용하는 패키지를 명시한다. npm i --save-dev <패키지명> 으로 설치하면 된다.
만약 내가 Git을 통해 프로젝트를 배포받았다면 프로젝트 루트에서 npm i 를 입력해야 프로젝트가 정상적으로 동작한다. 패키지 파일들은 모두 gitignore 당하기 때문에 package.json 에 명시된 dependencies 를 보고 새로 설치해야한다.


    npm init -y
    npm -i --save axios cheerio // dependencies 에는 프로젝트가 의존하는 패키지들의 이름과 버전을 명시한다

request, request-promise는 HTTP 클라이언트 라이브러리이다. 웹사이트의 HTML을 로드할 목적으로 사용할 것이다.

cheerio는 오늘의 주인공이다. JQuery와 거의 동일한 기능의 HTML DOM 파씽 기능을 제공한다.



<img width="486" alt="Screen Shot 2021-07-21 at 2 28 52 PM" src="https://user-images.githubusercontent.com/74404132/126435803-4027b4bb-c770-4da8-be5d-ad644ef36b1a.png">


데이터 가져오기
뉴스 목록에서 요소 검사를 눌러서 데이터를 가져올 HTML의 태그 이름과 Class 이름 목록을 정리합니다.

mac html code 열기

    Option+Command+U


html 그대로 긁어오면 동적인 데이터는 그대로 뜬다. 






      

      1. initial setup
        nodejs redownload
        /usr/local/bin/node
        /usr/local/bin/npm
        Make sure that /usr/local/bin is in your $PATH.

        NPM 계정이 먼저 있어야한다....



        echo $path

        sudo vi /etc/paths

        ~/bin 추가.

        npm install -g n
        The operation was rejected by your operating system.

        [Error: EACCES: permission denied, access '/usr/local/lib/node_modules'] {

        sudo chown -R ownerName: /usr/local/lib/node_modules

        sudo chown -R janna: /usr/local/lib/node_modules 

        npm도 git처럼 npm init이라고 저장소를 만들어주고 사용해야 패키지 관리가 가능한것으로 보인다.
        npm 관련 폴더를 하나 만들어준다.

        mkdir 3day

        npm init를 사용하면 자동적으로 정해지는 파일의 이름이 

        npm init -y sets up a package that allows you to download lot of dependencies
        index.js이다. packege.json 파일에서 정해둔 'main' entry에 해당하는 파일이 없을 경우 node.js는 index.js 파일을 자동으로 찾아 불러온다. 또한 package.json 파일이 없을 경우에도 동일한 작업을 수행한다.


        rm 명령어는 -r 옵션을 주지 않을 경우 디렉토리는 삭제할 수 없다
        rm -r 3day/node_modules 

        /Users/janna/.rbenv/shims /Users/janna/.rbenv/bin /Library/Frameworks/Python.framework/Versions/3.9/bin /usr/local/bin /usr/bin /bin /usr/sbin /sbin /Users/janna/.rbenv/shims /Users/janna/.rbenv/bin /Users/janna/opt/anaconda3/bin /Users/janna/opt/anaconda3/condabin /Library/Frameworks/Python.framework/Versions/3.9/bin
        세상에..

        그 파일로 이동해서 
        npm init

        npm init -y
        npm i cheerio node-fetch typescript ts-node// a library for fetching data ex axios 

<br/>

    ## AJAX 란?
    Asynchronous JavaScript ans XML 

    비동기적으로 JSON 이나 XML 등의 데이터를 받을 수 있는 방법

    curl get 의 역할을 하는 axios 등 함수는 AJAX 리퀘스트를 할 수 있는 라이브러리다

> Docs: [https://axios-http.com/docs/intro](https://axios-http.com/docs/intro)

<br/>

    cheerio
    JQuery 처럼 DOM Selector 기능을 제공한다. axios로 받은 HTML 데이터에서 실제로 필요한 정보를 파싱하는 데 사용

#### Python 의 Beautiful Soup 과 유사하다.

api docs: https://npmdoc.github.io/node-npmdoc-cheerio/build/apidoc.html






          "scripts": {
            "start": "ts-node src/index.ts" // test -> start to run typescript file
          },

        touch src/index.ts
        mv nodeTest src 파일명변경

        typescript 설치가 필요했다...

        npm install -g typescript

        tsc index.ts 하면 test.js 생성된다.


        html 에서
        <body>  
            <script src="test.js"></script>  
        </body>  
        부분에 document.body.textContent = sayHello(user); 함수 이런값이 실행 되는 것.

        셋 다 같은 폴더에 있어야 한다.

        function sayHello(person : string){
            return "Hello, " + person;
        }

        let user = "Janna User";
        // document.body.textContent = sayHello(user);

<img width="699" alt="Screen Shot 2021-07-21 at 6 10 03 PM" src="https://user-images.githubusercontent.com/74404132/126468969-cc477196-cce2-4a29-b7e9-8e117251a2df.png">


<srcipt ~> 쓴 html 만들고 실행하면 잘 된다.


        그래도 Failed at the crawl@1.0.0 start script.
        해결:
        npm install -D tslib @types/node

        실행은 성공

        Cannot find name 'document'. D

<img width="627" alt="Screen Shot 2021-07-21 at 6 19 01 PM" src="https://user-images.githubusercontent.com/74404132/126468792-b6fbdb00-8f90-4b71-a05d-88168f162d1c.png">

        console.log('hello world'); 만 내용물로 두면 실행된다 저 문제는 나중에 다시 찾기.

        will be writing script in typescript for completion



      2. fetching html

          web crawler whould fetch some html from a website.

          tst html 을 가져옴 
          npx http-server -p 10000 html

        이거 안됨. 통과

        http://toscrape.com 이용


        fetch expects 2 arguments ??

          npx 는 npm을 좀 더 편하게 사용하기 위해서 npm에서 제공해주는 하나의 도구




      3. searching for elements

      4. crawling the links

      5. stay on the same page

      - const { host, protocol } = urlParsar.parse(url);
      - handle absolute vs relative links
      - downloading images
      */
      const axios = require("axios"); // axios.get 함수를 이용하여 비동기로 스포츠 뉴스의 html 파
      const cheerio = require("cheerio"); // Promise 객체에 cheerio를 이용하여 데이터를 가공합니다
      const log = console.log;

      const getHtml = async () => {
        try {
          return await axios.get('https://leetcode.com/problemset/all/');
        } catch (error) {
          console.error(error);
        }
      };

      getHtml()
        .then(html => {
          let ulList = [];
          const $ = cheerio.load(html.data);
          const $bodyList = $("div.wrapper tr").children("tr.array");

          $bodyList.each(function(i, elem) {
            ulList[i] = {
                title: $(this).find('array-tl a').text(),
                url: $(this).find('array-tl a').attr('href'),
                //image_url: $(this).find('p.poto a img').attr('src'),
                //image_alt: $(this).find('p.poto a img').attr('alt'),
                summary: $(this).find('p.lead').text().slice(0, -11),
                date: $(this).find('span.p-time').text()
            };
          });

          const data = ulList.filter(n => n.title);
          return data;
        })
        .then(res => log(res));


동작 방식
웹 브라우저에서 동작하는 방식도 있지만, 웹 브라우저가 보내는 것처럼 HTTP 요청을 만들어서 보내고 응답으로 받은 페이지 내용을 분석하는 방식을 주로 사용한다.
크롤링 도구마다 어떤 방식을 사용하는지, 어떤 차이점이 있는지 비교해보기를 권장한다.


### Javascript Promise, Async, Await란?

<br/>

### Promise

<br/>


상태(Status)

    pending: 아직 약속을 수행중인 상태(fulfilled, reject 전)

    fulfilled: 약속(promise)이 지켜진 상태

    rejected: 약속이 어떤 이유로 못지켜짐

    settled: 약속 지켜진 여부에 상관없이 결론이 난 상태

<br/>

    var _promise = function(param){
      return new Promise(function (resolve, reject)){
        window.setTimeout(function()){
          if(param){
            resolve("resolved");
          }

          else{
            reject(Error("error));
          }
        }, 3000);
      });
    });

<br/>

선언은 new로 하면 되며, callback 함수의 인자 두개를 가진다.


<br/>


### .then()
then을 비동기함수 뒤에 붙여 함수 실행 순서, 데이터 전달을 가능하게 한다.

    promise(true)
      .then(function (text){
        console.log(text);

      }, function (error){
        console.error(error);
      }
      );


### catch().
then으로 이루어진 비동기함수 중간에 에러가 날 시 catch로 잡을 수 있다. 

_promise(true)
  .then(JSON.parse)
  .catch(function()){
    window.alert('error while chaining);
  })
  .then(function (text){
    console.log(text);
  });

<br/>

### async && await

https://developer.mozilla.org/ko/docs/Learn/JavaScript/Asynchronous/Async_await

추가된 기능이다. 기본적으로 비동기를 쓰고 Promise를 더 읽기 쉽도록 만들어준다.

async function() 은 await 키워드가 비동기 코드를 호출할 수 있게 해주는 함수이다.


1. async의 특징중 하나: 반환받는 값은 Promise 가 된다.

<img width="443" alt="Screen Shot 2021-07-22 at 2 48 49 AM" src="https://user-images.githubusercontent.com/74404132/126535745-80b96511-e903-4a7f-8b03-93b890b5d8e4.png">

2. 

<img width="367" alt="Screen Shot 2021-07-22 at 2 53 59 AM" src="https://user-images.githubusercontent.com/74404132/126536490-e96b3557-39b3-4ec2-b288-6a4b9f9b968e.png">

<br/>

3. 실제로는 fulfill Promise 가 반환되기 때문에 반환된 값을 가용하기 위해선 .then() 블럭을 사용해야 한다.

<img width="367" alt="Screen Shot 2021-07-22 at 2 53 59 AM" src="https://user-images.githubusercontent.com/74404132/126537028-74282302-b632-4bd1-beb6-71d1189616b1.png">

    async 함수는 결과를 직접 반환하는 게 아니라 Promise 를 반환하게 한다.





주의사항
웹 크롤링은 법적으로 보호받을 수 있는 한계가 있기 때문에 주의해야 한다. 개인적인 용도와 저작권법에서 보호하는 공정한 사용 범위 내에서만 사용해야 한다. 만약 스크래핑한 데이터를 다른 곳에 공개하거나, 웹 사이트를 공격하거나 저작권으로 보호하는 데이터를 수집하려는 의도를 갖고 하면 불법 행위로 간주된다. 봇배제표준(robots.txt)에 대해 알아보고, 사용자 에이전트(User Agent) 표기 방식, 웹 크롤링 불법 사례에 대해 학습한다.

> 봇 관리에 대한 글 https://www.cloudflare.com/ko-kr/learning/bots/what-is-bot-management/

2. LRU 캐시 동작 방식

https://en.wikipedia.org/wiki/Cache_replacement_policies

학습한다. 그 중에서 LRU (Least recently used) 방식을 활용해서 문제 해결해야 한다.
캐시 정책 결정 기준

### Cache란?
<ol>
캐시는 성능개선에서 가장 많이 사용되는 방법이다.

요청 받아올 때 가장 좋은 건 아무것도 안하는 것, 즉 이미 저장된 데이터를 쓰는 것

제약 조건: 시간
제한 시간이 유효하다면 캐시를 통해 성능개선을 할 수 있다.

캐시 주의할 점? 메모리가 제한돼 있다. 제약 조건을 두고 cache overflow 시 이전의 데이터를 삭제해 주는 것
잘 쓰지 않는 오래된 데이터를 삭제해주는 정책
hit count 고려해서 삭제한다.


</ol>



개수 제한, 용량 제한, 시간 제한 등을 정책적으로 결정할 수 있는 방법들을 확인한다.
<br/>




<br/>

## js 로 크롤링 하는 법

npm 을 이용한다.
프로젝트에 필요한 설치도구등을 이용하기 쉽게 관리해주는 패키지 툴이다.

npm init -y // 기본값으로 하나 만든다
npm install axios



pacakage.json

    {
      "name": "hi",
      "version": "1.0.0",
      "description": "",
      "main": "index.js",
      "scripts": {
        "start": "node index.js"
      },
      "keywords": [],
      "author": "",
      "license": "ISC",
      "dependencies": {
        "axios": "^0.21.1"
      }
    }



npm start 하면 스크립트에 써있는 그대로가 스크립트 언어로 실행되는것.



<br/>

이제 index.js 만들어서 크롤링 모듈 이용해서 코드를 작성한다.



    console.log('hi'); // 비동기 처리 할 만한게없다


    // npm: json 파일에 명시돼있는걸 그대로 
    //스크립트 파트에 가서 해달하는 명령어르 ㄹ그대로 수행시키는 것

    const t = require('axios').default; // 이 라이브러리에 디폴트 넣어라
    // 함수나 클래스 일수있다.
    console.log(t.get("https://google.com")) //결과 생각했더니 모름 io작업이 대표적인 비동기처리
    // chrong v8 엔진 오면 그떄 처리하고 다므 작업부터 하는 것
    // Promise 값 아직 모르는 채 종료된것

    t.get("https://google.com").then((r) => {  //동기 역할
        console.log(r)
    })

    // 인풋 들어오면 하던거 멈추고..


    콜스탠에 넣은걸 이따 처리함

    이벤트핸들러는? 

    // html 만 필요한지 통신정보 url도 필요한 지

    //callback 함수

    //add(1, 2, print)
    // print 가 콜백함수이다

    // add 결과 다름에 실행할 함수
    // 쉘이 저걸 그대로 쳤더니 저런 실행은 없다고 알려준 것

    //io 작업하는데 수행 완료되기 전에 된거라
    // 비동기 처리임
    // 동기처리하지 않는 모든게 비동기로 실행된다.

    console.log(1 + 2)
    console.log(1)

    // 컴퓨터의 모든 자원에