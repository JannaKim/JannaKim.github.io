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


<br>

<li> vector <int> v(2,3); // 2개의 3으로 백터를 채운다.

<br/>


1. pair(utility 헤더)

함수에서 두 개의 변수를 return하고 싶을 때, 혹은 좌표평면 상의 점의 좌표나 분수와 같이 두 개의 속성을 계속 가져갈 필요가 있을 때, 구조체를 선언해서 사용해도 되지만 그보다는 pair를 쓰는게 더 간편합니다. pair간의 크기 비교에서는 첫 번째 속성을 먼저 비교하고, 값이 동일하다면 두 번째 속성을 비교합니다.

- 선언

pair<int, int> p1;  // 초기값을 주지 않으면 first, second 모두 0
pair<char, int> p2 = make_pair('c', 3);
pair<int, double> p3 = {3, 5}; // C++11 부터에서 지원
pair<int, int> p4[100];

- 속성

pair<int, int> p = {2,4};
cout << p.first; // 2
cout << p.second; // 4

- 예시(분수의 덧셈)

pair<int,int> func(pair<int,int> f1, pair<int,int> f2){
int a1 = f1.first * f2.second + f1.second * f2.first;
int a2 = f1.second * f2.second;
return {a1, a2};
}

2. tuple(tuple 헤더)

함수에서 세 개 이상의 변수를 return하고 싶을 때, 혹은 세 개 이상의 속성을 계속 가져갈 필요가 있을 때, 구조체를 선언해서 사용해도 되지만 그보다는 tuple을 쓰는게 더 간편합니다. tuple간의 크기 비교 또한 pair와 유사하게 첫 번째 속성을 먼저 비교하고, 동일하다면 두 번째 속성을 비교하고, 동일하다면 세 번째 속성을 비교하는 방식으로 사용합니다. (속성이 2개여도 되지만, 2개라면 차라리 pair를 쓰는게 더 낫겠죠.) tuple은 C++11 이상 버전에서 지원됩니다.

- 선언

tuple<int, int, double> t1;
tuple<char, int, double> t2 = make_tuple('c', 3, 2.0);
tuple<int, double, int> t3 = {3, 5.2, 5};

- 속성

tuple<int, int, double> t1 = {1,2,3.5};
cout << get<0>(t1); // 1
cout << get<1>(t1); // 2
cout << get<2>(t1); // 3.5

- 추가적인 정보

변수 a,b,c에 t1의 0,1,2번째 속성의 값을 넣고싶다고 해봅시다. get<0>(t1), get<1>(t1), get<2>(t2)로 쓰는 대신 tie(a,b,c) = t1 으로 아주 깔끔하게 값을 넘겨받을 수 있습니다.

저는 tuple을 애용하지만 값을 가져오기가 번거롭다는 이유로 tuple 대신 pair<int,pair<int,int>>와 같은 방식으로 처리하거나 아예 구조체를 만들어 쓰는 경우도 있습니다. 속성이 너무 많아지면 그냥 vector를 쓰는 것을 추천합니다.

3. vector(vector 헤더)

배열과 쓰임새가 비슷하나 배열보다 기능이 더 추가된 STL입니다. Graph의 adjacency matrix를 잡을 때 동적할당을 쓰는 대신 vector를 이용해 코딩을 더 편하게 할 수 있고, 이외에도 배열 대신 vector를 썼을 때 배열에 비해 메모리를 아주 조금 더 사용한다는 점 이외에는 전혀 문제가 없기 때문에 편의에 따라 활용할 수 있습니다.

- 선언

vector<int> V1;
vector<double> V2(10);  // 10개의 원소를 담는 vector, 각 원소는 0.0으로 초기화되어있음
vector<int> V3(5,8); // 5개의 원소를 담는 vector, 각 원소는 8로 초기화되어있음
vector<pair<int,int>> V4;

- 제공되는 함수
begin : vector의 시작 부분을 가리키는 iterator
end : vector의 끝 부분을 가리키는 iterator
size : vector 내의 원소의 갯수
front : vector의 첫 원소
back : vector의 마지막 원소
push_back : vector의 끝 부분에 원소를 삽입. O(1)
pop_back : vector의 마지막 원소를 제거. O(1)
insert/erase : 임의의 위치에 원소를 삽입/제거. 해당 위치 이후의 원소의 갯수에 비례한 시간복잡도.
clear : vector를 초기화(모든 원소를 제거한 것과 동일). vector 내의 원소들에서 따로 초기화가 필요하지 않으면 O(1). 앞의 표현이 잘 이해가 안가면 그냥 O(1)이라고 생각해도 무방.

- 추가적인 정보

원래 bool은 1바이트 자료형인데 vector<bool>은 각 bool을 1비트 단위로 저장하기 때문에 메모리를 획기적으로 줄일 수 있습니다.

생소할 수도 있지만 vector간의 비교도 가능합니다.
vector<int> a1 = { 2,2 };
vector<int> a2 = { 1,2,3 };
cout << (a1 < a2); // 0
a1 = {1,2};
cout << (a1 < a2); // 1


private:
    vector<int> m;
    int ans;
public:
    Solution() : m(2501, -int(1e9)) {};


백터는 오버로딩과 프렌드를 사용하는 또 하나의 클래스이다.


int& prev_end = merged.back()[1];

갱신됨

sort(intervals.begin(), intervals.end(), [] (const vector<int>& lhs, const vector<int>& rhs)->bool {
            return lhs[0] < rhs[0];
        });

        