flutter channel beta
flutter upgrade
flutter config --enable-web



index.js 에서 파이어베이스 설정한다.
<!-- The core Firebase JS SDK is always required and must be listed first -->
        <script src="https://www.gstatic.com/firebasejs/8.9.0/firebase-app.js"></script>

        <!-- TODO: Add SDKs for Firebase products that you want to use
            https://firebase.google.com/docs/web/setup#available-libraries -->

        <script>
        // Your web app's Firebase configuration
        var firebaseConfig = {
            apiKey: "AIzaSyBxmFMAzssYdyJoc0UKlFHkfzosEyGwzPo",
            authDomain: "boostcamp-relay6-mora.firebaseapp.com",
            projectId: "boostcamp-relay6-mora",
            storageBucket: "boostcamp-relay6-mora.appspot.com",
            messagingSenderId: "1001306782708",
            appId: "1:1001306782708:web:af3a0a421f727850a217a1"
        };
        // Initialize Firebase
        firebase.initializeApp(firebaseConfig);
        </script>


내 authorized google 계정 넣는다.

    <meta name="baradamoh" content="1001306782708-ketcv4bu2mt10gtns1epuf8kiqt4r8j2.apps.googleusercontent.com
provider에  user.dart 만든다

        /*
        //  read all user code from database.

        // append all users in moders using user dart file
        */

        import 'package:chat_app/models/user.dart';
        import 'package;chat_app/services/user.dart';
        import 'package:flutter/material.dart';

        class UserProvider with ChangeNotifier {
            List<UserModel> users = [];
            UserServices _userServices = UserServices();

            UserProvider.init(){}{
                _getUsers();
            }

            _getUsers() async{
                users = await _userServices.getAll();
                notifyListners(); // get all data and notify listners
            }
            
        }


widget 에 side_menu.dart
여기서 user display 



flutter run -d chrome --web-port 5000 // make sure you specify the web port to 5000



my cloud storage id

00b4903a97b6612743f774d2253c048606466c420e692b90a9d00dbeac6f8a0d

273992418943-qba5o5hrogck4mhcfpba1f1l5254ht7e.apps.googleusercontent.com




key 가져오기