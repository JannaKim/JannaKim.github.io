---
layout: post
title:  "Web crawling"
excerpt: "reviews"


categories:
  - Blog
tags:
  - [Blog, jekyll, Github, Git]

 
date: 2021-07-21
last_modified_at: 2021-07-21
---


<br/>

1. 웹 크롤링

finds every link, find, go inside and does the same logic

웹-크롤링 Web-Crawling은 웹 사이트에 있는 데이터를 추출해서 사용하기 위한 목적으로 홈페이지 내용을 수집하고, 추출하는 것을 의미한다. 특정한 규칙에 맞춰서 웹 페이지에 방문해서 내용에 포함된 데이터를 가져오는 것을 말합니다. 사용자가 웹 브라우저로 검색해서 결과로 나온 정보를 노트에 써놓는 것과 비슷한 행동을 프로그램이 반복해서 저장하도록 만드는 것이다.

> 읽어볼만한 글 : https://www.cloudflare.com/ko-kr/learning/bots/what-is-a-web-crawler/


웹 크롤링: 수집한 데이터에 검색 알고리즘을 적용하는 것


웹 크롤러 봇은 종자, 즉 알려진 URL 목록에서 시작합니다. 먼저 해당 URL에서 웹페이지를 크롤링합니다. 이 과정에서 다른 URL에 대한 하이퍼 링크를 찾게 되면, 다음으로 크롤링할 페이지 목록에 추가합니다.

메타데이터: 웹사이트가 무엇에 대한 것인지 알려주는 데이터. 용자가 볼 수있는 웹 페이지의 콘텐츠와 달리 검색 엔진 결과 페이지에 표시되는 경우가 많다. 

검색 색인화란? 정보를 필요로 하는 사람에게 인터넷의 어디에서 그 정보를 찾을 수 있는지 알려주기 위해 검색 엔진이 만드는 것. 페이지에 대한 메타데이터에 중점을 둔다.


웹 크롤러 작동 방식:
웹 크롤러는 크롤링할 페이지, 크롤링 순서, 콘텐츠 업데이트를 확인하기 위해 다시 크롤링하는 빈도에 대해 보다 선택적인 정책을 따릅니다.
해당 페이지에 중요한 정보가 포함될 가능성을 나타내는 요소인 해당 페이지를 링크하고 있는 다른 페이지 수, 페이지 방문자 수 등의 요소를 기준으로 먼저 크롤링할 페이지를 결정한다.

웹페이지 재방문: 웹 콘텐츠는 지속적으로 변경되거나 삭제되고 새로운 위치로 이동합니다. 웹 크롤러는 정기적으로 페이지를 다시 방문하여 최신 버전의 콘텐츠를 색인화해야 합니다.


웹 크롤러 봇이 액세스 허용된 웹가 아닌 웹


웹 크롤러가 콘텐츠를 색인화하려면 서버 자원이 필요합니다. 웹 크롤러도 서버의 응답이 필요한 요청을 냅니다. 과도한 색인화는 서버 과부하, 대역폭 비용을 고려해서 각 페이지의 콘텐츠 양이나 사이트 내의 페이지 수에 따라, 검색 색인화를 자주 허용하지 않는 것이 웹사이트 운영자에게 유리한 경우도 있습니다.

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

주의사항
웹 크롤링은 법적으로 보호받을 수 있는 한계가 있기 때문에 주의해야 한다. 개인적인 용도와 저작권법에서 보호하는 공정한 사용 범위 내에서만 사용해야 한다. 만약 스크래핑한 데이터를 다른 곳에 공개하거나, 웹 사이트를 공격하거나 저작권으로 보호하는 데이터를 수집하려는 의도를 갖고 하면 불법 행위로 간주된다. 봇배제표준(robots.txt)에 대해 알아보고, 사용자 에이전트(User Agent) 표기 방식, 웹 크롤링 불법 사례에 대해 학습한다.

> 봇 관리에 대한 글 https://www.cloudflare.com/ko-kr/learning/bots/what-is-bot-management/

2. LRU 캐시 동작 방식

https://en.wikipedia.org/wiki/Cache_replacement_policies

학습한다. 그 중에서 LRU (Least recently used) 방식을 활용해서 문제 해결해야 한다.
캐시 정책 결정 기준


개수 제한, 용량 제한, 시간 제한 등을 정책적으로 결정할 수 있는 방법들을 확인한다.
<br/>




<br/>
