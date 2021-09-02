---
layout: post
title:  "Fundemental of Backtracking, using order of dictionary"
excerpt: "reviews"


categories:
  - Blog
tags:
  - [Blog, jekyll, Github, Git]

 
date: 2021-09-02
last_modified_at: 2021-09-02
---





<br/>

![IMG_425FAAAC9ACE-1](https://user-images.githubusercontent.com/74404132/131821376-af1a4afb-d4f9-4d2a-b364-0f39de76b6bc.jpeg)
![IMG_B6DBB322E9DD-1](https://user-images.githubusercontent.com/74404132/131821381-23f99a6e-9c16-41be-813a-d25f908dd655.jpeg)
![IMG_D8F825D8FBFE-1](https://user-images.githubusercontent.com/74404132/131821386-b5b93a3c-ad8b-4c5b-8975-c6813e51c551.jpeg)
![IMG_6A30024932BE-1](https://user-images.githubusercontent.com/74404132/131821400-0aea3759-e9da-417d-afe9-3b9f86d1678a.jpeg)
![IMG_A589171F707B-1](https://user-images.githubusercontent.com/74404132/131821419-92e7bede-d7d9-4bd9-87e6-949fc590da8e.jpeg)
![IMG_3CC8BAB3CDE7-1](https://user-images.githubusercontent.com/74404132/131821427-b24e09c2-dd03-4e66-a5ce-5cc1ecfe28b6.jpeg)
![IMG_219EDC73FA82-1](https://user-images.githubusercontent.com/74404132/131821430-6234e812-73aa-4cb0-ba5e-fb00aa61500a.jpeg)


<br/>

    #include <string>
    #include <iostream>
    using namespace std;

    string v = "AEIOU";
    string w;
    string occ = "";
    int ans = -1;

    bool dfs(int depth); // occurence

    int solution(string word) {
        w = word; //
        dfs(0);
        return ans;
    }

    bool dfs(int depth){
        ++ans;
        if(occ == w) return true; // compare cur with given
        if(depth == 5) return false;

        for(int i = 0; i < 5; ++i){
            occ.push_back(v[i]); // backtrack
            if(dfs(depth + 1)) return true;
            occ.pop_back();
        }
        return false;
    }

<br/>

<br/>



cf)

find rank of the word in the dictionary?

4 2 1 3 2 5
s e c r e t

look towards left, 

(find how many that is lower) / (repetitions)! * (descending idx)!

s : 4 / 2!    * 5!
e : 1 / 2!    * 4!
c : 0         * 3!
r : 1         * 2!
e : 0         * 1!
t : 0         * 0!

#### + 1

255.



