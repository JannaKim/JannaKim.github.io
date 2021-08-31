---
layout: post
title:  "Euler’s phi (totient) function"
excerpt: "PS"


categories:
  - Blog
tags:
  - [Blog, jekyll, Github, Git]

 
date: 2021-08-31
last_modified_at: 2021-08-31
---
<br/>
<br/>

# Euler’s phi (totient) function (BOJ 4355)

<br/>
<br/>

https://www.acmicpc.net/problem/4355

<br/>


<img width="801" alt="image" src="https://user-images.githubusercontent.com/74404132/131443780-76fb49cc-f8ba-4873-8f6e-71a742ca2edc.png">


<br/>
<br/>

### relatively prime = coprime

<br/>

### is when a divisor of both of them is 1.

####= components of undiminished fraction.


It is written as φ(n)

    ex) the totatives of n = 10 are 1, 2, 4, 5, 7, 8

    so φ(9) = 6

    φ(1) = 1

<br/>
<br/>

## Euler's totient function is a multiplicative function. φ(mn) = φ(m)φ(n)

<br/>
<br/>

### examples

<br/>

    φ(27) = φ(3)φ(7)

    φ(3) = 3, (1, 2)

    φ(7) = 7 = (1, 2, 3, 4, 5, 6)

    φ(27) = 21


    φ(12) = φ(3)φ(4)

    φ(3) = 2, (1, 2)

    φ(4) = 2, (1, 3)

    φ(12) = φ(3)φ(4) = 4, (1, 3, 5, 7)

    φ(20) = φ(4)φ(5) = 2 * 4 = 8

    φ(20) = φ(2^2 * 5) = 20 * (1 - 1/2) * (1 - 1/5) = 8

    = φ(2^2 * 5^1) = 2^(2-1) * 5^(1-1) * (5 - 1)

<br/>

    strategy : get 'primes' that is divisible with n and use that formula.

<br/>

### 0. get Primes

<br/>

        for(int i = 2; i < MAX; ++i){
          if(visited[i]) continue;
          Prime.push_back(i);
          for(int j = 2 * i; j < MAX; j += i) 
                  visited[j] = true;
        }

<br/>

<br/>

### 1. get primes that is divisible with n

<br/>

        void getPrimes(int x){
          if(x == 1) return;
          for(auto P: Prime){
            if(x % P == 0){
              Construct[P]++;
              getPrimes(x / P);
              return;
            }
          }
          if(x != 1) Construct[x]++; // when remaining, they're also prime number.
        }

<br/>
<br/>


### 2. use that formula.

<br/>

    while(1){
      cin >> N;
      if(N==0) break;
      Construct.clear();
      MakeCon(N);
      long long ans = 1LL;
      for(auto it: Construct){
        int num = it.first;
        int cnt = it.second;
        // using φ(p^k) = p^(k-1) x (p-1), which is
        cnt--;
        while(cnt--) ans*=num; // multiple p , k - 1 times
        ans*=(num-1); // multiple p - 1
      }
      cout << ans << '\n';
    }

<br/>
<br/>
<br/>
<br/>

full code C++

    #include <iostream>
    #include <map>
    #include <vector>
    using namespace std;
    const int MAX = 40000;
    typedef long long ll;

    int n;
    map<int, int> groups;
    vector<int> primes;
    bool vis[MAX];

    void search(int x);

    int main(){
        for(int i = 2; i < MAX; ++i){ // find all primes using net 
            if(vis[i]) continue;
            primes.push_back(i);
            for(int j = 2 * i; j < MAX; j += i)
                vis[j] = true;
        }

        while(1){
            cin >> n;
            if(n == 0) break;
            groups.clear();
            search(n);
            ll ans = 1LL;
            for(auto it : groups){ // all m, n s that are in φ(mn) = φ(m)φ(n) are measured before.
                int p = it.first;
                int k = it.second;
                // use φ(p^k) = p^(k-1) x (p-1). simply multiply them.
                --k;
                while(k--) ans*=p; // p^(k-1)
                ans *= (p - 1); // (p-1)
            }
            cout << ans << '\n';
        }

    }


    void search(int x){
        if(x == 1) return;
        for(auto num : primes){
            if(x % num == 0){ // found : 2 or 5 in φ(20) = φ(2^2 * 5)
                ++groups[num];
                search(x / num); // 10 is also divisible with 2, so two 2 could be found.
                return; // only once. 20 / 2 handles second 2
            }
        }
        if(x != 1) ++groups[x]; // if x == 20 and prime = 7, is should also be grouped.
    }


