---
layout: post
title:  "How Floyd Warshall works"
excerpt: "classification: Graph"


categories:
  - Blog
tags:
  - [Blog, jekyll, Github, Git]

 
date: 2021-02-18
last_modified_at: 2021-02-18
---
* * *

##### This algorithm follows the dynamic programming approach to find the shortest paths.
#
####
#
>
> > #### chap 1: introduce the essential steps for F-W algo implementation.
>
> > #### chap 2: explain how it works: why does it need 3 loops?
>
#
#
#
### chapter 1) the essential steps for F-W algo implementation
#
#### step 1) initialization
##### At first, each cell is filled with given cost of a->b.
##### dp[v][v]=0 and if there is no path, the cell is left as infinity.
#
        dp= [[1e9]*n for _ in range(n)]
        for _ in range(m):
            a, b, c=[int(i)-1 for i in input().split()]
            c+=1
            dp[a][b]=min(dp[a][b],c)
        for i in range(n):
            dp[i][i]=0
#
#
#

#### step 2) create 3 loops as below:
#
        for i in range(n):
            for j in range(n):
                for k in range(n):
                    if j!=k:
                        dp[j][k]= min(dp[j][k], dp[j][i]+dp[i][k])
#
##### Simply put:
##### examines shorter path from vertax j to vertax k: it compares whether passing through vertax i is smaller or not.
#
#
#
##### As it's done.
##### After passing the nested loop above, the shortest path between all the pairs of vertices in a weighted graph are found. (If there are none, its value is infinify)
#
#
#
#
### How is it possible? 
#
#### chap 2: why is implementing 3 loops an if and only if condition?
#
#
#
        for i in range(n):
            for j in range(n):
                for k in range(n):
                    if j!=k:
                        dp[j][k]= min(dp[j][k], dp[j][i]+dp[i][k])
#

##### The important thing is, when value of 'i' is enhanced i to i+1, it means that:

#
> #### All pairs of vertices has "completed" to check whether it costs less when passing through i.
#
#
#
# 
##### For example, let's say there are more than 3 vertax, and each are 0, 1 and 2.
#
##       dp[j][k]= min(dp[j][k], dp[j][i]+dp[i][k])
#### the code above can be drawn to graph.
##### 
![IMG_24F6E432ECE3-1](https://user-images.githubusercontent.com/74404132/108319206-62536400-7204-11eb-8366-3eedc914fd5e.jpeg)
#### Now let's switch i to real value. i starts with 0(vertax 0)
![IMG_85B9D3903283-1](https://user-images.githubusercontent.com/74404132/108319408-b65e4880-7204-11eb-88fb-b65112a5cc70.jpeg)

#### Seems like nothing happened. Now turn i to 1 (vertax 1)
![IMG_60C51274B6E1-1](https://user-images.githubusercontent.com/74404132/108320518-3fc24a80-7206-11eb-946d-d7618e2c8064.jpeg)
#### * Note: since i is 1, ALL PAIRS of verticles has "COMPLETED" to check whether it costs less when passing through "0".
#
#### Thus : dp[j][1] and dp[1][k] has "COMPLETED" to check whether it costs less when passing through "0"
![IMG_47D54B0FA45D-1](https://user-images.githubusercontent.com/74404132/108321443-82d0ed80-7207-11eb-8f32-7b25119614a6.jpeg)
#
#
#### Below is all compared process for dp[j][k] when i=2.
![IMG_8268FE08400C-1](https://user-images.githubusercontent.com/74404132/108322994-7b124880-7209-11eb-9856-ddd104d1cd53.jpeg =250x)
#
#
####... and on and on.

#
#

* * *

### Floyd
##### URL https://www.acmicpc.net/problem/11404
##### difficulty: __Gold 4__
#
#
> ### Problem description:
> #### There exists n village: 1, 2, ..., n.
> #### cost to move from v1 to v2 are given.
> #### The goal is to find the shortes cost.
> #
> > #### input(s)
> > ##### n: number of vertax
> > ##### m: number of costs given
> > ##### m lines: v1, v2 and cost
> #
> > #### print out(s):
> > ##### 1. all shortest cost between all vertax.
> > ##### print 0 if it doesn't exists.

* * *

#
full code)

        import sys; input= lambda: sys.stdin.readline().rstrip()
        n= int(input())
        m= int(input())
        dp= [[1e9]*n for _ in range(n)]
        for _ in range(m):
            a, b, c=[int(i)-1 for i in input().split()]
            c+=1
            dp[a][b]=min(dp[a][b],c)
        for i in range(n):
            dp[i][i]=0

        for i in range(n):
            for j in range(n):
                for k in range(n):
                    if j!=k:
                        dp[j][k]= min(dp[j][k], dp[j][i]+dp[i][k])

        for i in range(n):
            for j in range(n):
                print([dp[i][j],0][dp[i][j]==1e9], end=' ')
            print()




