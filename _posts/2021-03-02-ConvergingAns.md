---
layout: post
title:  "converging ans using recursion"
excerpt: "recursion"


categories:
  - Blog
tags:
  - [Blog, jekyll, Github, Git]

 
date: 2021-03-02
last_modified_at: 2021-03-02
---
* * *

##### This post explains the way to return ans among all cases
#
####
#
>
> > #### for loop containing recursion
>

#
#### backtracking is composed of for loop+ recursion
#
##### all possible roads are checked with for loop. 
> > ##### strategy: 
> > > ##### 1. create variable 'answer' and initialize it with max size.
> > > ##### 2. create a variable 'tmp' and put the returning value of recursed function
> > > ##### 3. check all tmp values and find answer
> > > ##### 4. return answer

###### * essential element= chk list initialized with False

ex code)

    chk= [False]*n
    def backtrack(?):
        ans= 1e9
        for i in range(n):
            if not chk[i]:
                chk[i]=True
                tmp= backtrack(?)
                ans= min(ans, tmp)
        return ans

#
#
#
### Traveling Salesman
##### URL https://www.acmicpc.net/problem/10971
##### difficulty: __Silver 2__
#
#
> ### Problem description:
> #### There exists n village: 1, 2, ..., n.
> #### cost to move from v1 to v2 are given.
> #### The goal is to find the shortest cost to travel all village
> #### Each village should only be traveled once
> #### when all village are traveled, return to first village
> #
> > #### input(s)
> > ##### n: number of village
> > ##### 4 lines consisted of [i][j]: each represents cost traveling i->j
> #
> > #### print out(s):
> > ##### 1. shortest cost to travel all village, and return to first village

* * *

#
full code)

        n= int(input())

        L=[[*map(int, input().split())] for _ in range(n)]

        chk= [False]*n
        def td(i):
            if all(chk[1:]):
                return L[i][0] or 1e9

            ans= 1e9
            for j in range(1,n):
                if not chk[j] and L[i][j]: # 만약 길이 있다면
                    chk[j]=True
                    tmp= td(j)
                    chk[j]=False
                    ans= min(ans, tmp+L[i][j])
            
            return ans

        print(td(0))




