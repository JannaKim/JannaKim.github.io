---
layout: post
title:  "flutter chat app tutorial"
excerpt: "reviews"


categories:
  - Blog
tags:
  - [Blog, jekyll, Github, Git]

 
date: 2021-08-09
last_modified_at: 2021-08-09
---

1. 플러터 실행

flutter pub get // 으로 패키지 다 설치 해준다.

flutter run -d chrome --web-renderer html


## what is renderer?
https://stackoverflow.com/questions/41077723/what-is-the-exact-meaning-for-renderer-in-programming

        코드의 버튼에 달린 객체에는 pos, size, text content, color 등 다양한 properties 가 담겨 있다.
        renderer 이란 버튼에 이런 속성들을 모델링 해놓고, 스크린에 그 버튼을 실제로 그린다.
        버튼안에 속성이 담긴 custom render을 가지고선 원하는 걸 실현할 수 있다.


renderer html 을 이용해 flutter를 실행시키지 않으면 
파이어베이스의 사진을 제대로 불러올 수 없다.

html 실행:

<img width="200" alt="image" src="https://user-images.githubusercontent.com/74404132/128645274-01ce69fa-0c39-48b7-bb9c-69862abe334c.png">


<p>

</p>

html 실행 x:
<img width="200" alt="image" src="https://user-images.githubusercontent.com/74404132/128645361-44de1194-ab4d-4153-834c-e51030aab124.png">




2. StatelessWidget, StatefulWidget 

대부분의 클래스는 StatelessWidget, StatefulWidget 을 상속받는다.

StatelessWidget은 실행할 시 실제 값은 잘 바뀌지만, 
위젯서에는 반영되지는 않는다

        class MyApp extends StatelessWidget {

        @override
        Widget build(BuildContext context) {
            return X;
        }

화면이 생성될 때 한 번만 실행시키려면 StatelessWidget.
이 클래스는build 메서드를 호출한다.

build 메소드는 이 둘 에서 구성,화면을 구성할 UI들을 구현한다.
화면이 출력될 때 build 메서드가 호출되면서 build 메서드 내부에 구현한 UI 위젯들이 화면에 출력 된다.

        class ChannelView extends StatefulWidget {
        final Map? channel;

        const ChannelView({required this.channel});

        @override
        _ChannelViewState createState() => _ChannelViewState();
        }

        class _ChannelViewState extends State<ChannelView> { // 채팅 치는 창
        TextEditingController _textEditingController = TextEditingController();

        var focusNode = FocusNode();
        String chatText = '';


        @override
        void initState() {
            super.initState();
        }

        void handleSubmit() {
            setState(() {
            chatText = _textEditingController.text;
            });
            createChat(widget.channel?['id'], { // 여기서 이런식으로 채팅 받아서 디비에 저장한다
            'content': chatText,      
            'name': getCurrentUserData().displayName,
            });
            setState(() {
            _textEditingController.clear();
            });
            focusNode.requestFocus();
        }

        @override
        Widget build(BuildContext context) {

https://www.wenyanet.com/opensource/ko/6044b05547f91c7d100a74ee.html

main.dart // 앱 켰을 때 딱 한 번만 실행시킬 홈 화면을든다.

** 홈 화면에 상태값 변화가 필요한 부분이 있다면, return X 에 StatefulWidget을 상속 받는 클래스를 넣어준다.

3. 클래스에 파라미터 넘기는 법


4. firebase

        firebase 에 해당 값 저장하는 법

        import 'package:firebase_auth/firebase_auth.dart';

        FirebaseFirestore.instance
            .collection('channels')
            .doc('모라')
            .collection('chat')
            .add({...chat, 'time': DateTime.now()}).then((value) {

<br/>

        firebase에 해당 값 갖고 오는 법

            FirebaseFirestore.instance
                .collection('ROOM')
                .get()
                .then((QuerySnapshot querySnapshot) {
                return querySnapshot;
            }).catchError((error) {
                print("Failed to read rooms: $error");
            });

<br/>
        firebase 에 저장된 모든 값 가져와서 붙여넣기? - Santos Enoque Youtube

        /*
        //  read all user code from database.

        // append all users in moders using user dart file
        */

        import 'package:chat_app/models/user.dart';
        import 'package:chat_app/services/user.dart';
        import 'package:flutter/material.dart';

        class UserProvider with ChangeNotifier {
            List<UserModel> users = [];
            UserServices _userServices = UserServices();

            UserProvider.init(){
                _getUsers();
            }

            _getUsers() async {
                users = await _userServices.getAll();
                notifyListeners(); // get all data and notify listners
            }
            
        }

<br/>

5. 

Expanded : 끝까지 넓힘

위아래 패딩 : padding: EdgeInsets.fromLTRB(0, 10, 0, 10),

TextField - 이용자에게 값을 입력받기 위해 사용한다 controller가 반드시 필요하다.


Text 한번에 여러개 : 

RichText(
    
    text: TextSpan(
    children: const <TextSpan>[
        // TextSpan(text: 'bold', style: TextStyle(fontWeight: FontWeight.bold)),
        TextSpan(text: ' = ', style: TextStyle(fontSize: 13,
                height: 1.0,
                color: Colors.blue)) ,
        //text : data['content'],
        //TextSpan(data['content']),
        TextSpan(text: '"', style: TextStyle(
            
                fontSize: 13,
                height: 1.0,
                // color: Color(0xffFF0E58),
                color : Color(0xFF76FF03))
        )
        
    ],
    ),
//Text(data['content']),
),



Center :  기본값 중앙

mainAxisAlignment: MainAxisAlignment.start,
crossAxisAlignment : CrossAxisAlignment.start,


git stash // 하던 거 임시 저장
git stash list // 임시 저장 뭐 돼있는지
git stash pop // 최근 꺼 팝
