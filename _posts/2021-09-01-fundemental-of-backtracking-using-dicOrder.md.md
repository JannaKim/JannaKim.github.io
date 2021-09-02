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


![IMG_16C3A4B1B50F-1](https://user-images.githubusercontent.com/74404132/131818405-fa383411-affa-4e7a-bcfd-62b3ba3a0e18.jpeg)
![IMG_63F8037044AB-1](https://user-images.githubusercontent.com/74404132/131818435-245d077c-136b-4dc4-9b4d-19cc7cfcd0f0.jpeg)
![IMG_E01D2FEF15A2-1](https://user-images.githubusercontent.com/74404132/131818447-245dd7bc-ec6f-4686-9369-7b8ec9ce9ab8.jpeg)
![IMG_99C9FCCDAD3D-1](https://user-images.githubusercontent.com/74404132/131818457-820a7adc-90d6-432b-8497-c49b40c01d79.jpeg)
![IMG_36AB3A002E65-1](https://user-images.githubusercontent.com/74404132/131818479-54dde240-4a8a-4616-94c3-c6a79a1622df.jpeg)
![IMG_23F7C1AFE1F5-1](https://user-images.githubusercontent.com/74404132/131818482-7a9edbd4-bd59-4d96-a24f-95270d1ed6ed.jpeg)
![IMG_5BE9125D3ADA-1](https://user-images.githubusercontent.com/74404132/131818485-9f9932b9-66f3-407a-a829-f7d135be84ec.jpeg)

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



