---
layout: post
title:  "Process synchronization (ENG)"
excerpt: "reviews"


categories:
  - Blog
tags:
  - [Blog, jekyll, Github, Git]

 
date: 2021-08-14
last_modified_at: 2021-08-14
---

Let us assume, we have the RAM of our computer.
RAM will have a lot of processes

![image](https://user-images.githubusercontent.com/74404132/129439328-2d111010-601f-40d0-8ad8-3cd5b5b41ee0.png)

How is P1, P2 allocated? Either using contiguous allocation or using paging ... etc.

Assume P1, P2 is placed like that.

We also say these process as PCB.

PCB will have Stack segment, Heap segment, Code ,, 

#### LEts consider Code segment

Code segment is nothing but the program of this process.

Our OS will always ensure protection between processes.

ex) P2 can't access the PC of P1 "directly". (either code, data, variable...) 

Because of this, there is a problem. Most of the times, we want Communication between processes.

what is communication?

ex) P1 have many lines of code, and one of the lines is actually computing the value of C, and the value of C is somehow updated.

How wil this vallue be updated? "Only by running this process" = Only when CPu is executing this complete code.

Let's assume that P2 gets the value of C as input.
 
ex) d = c * e

So P1 should have been already executed.

P2 can't "directly" go to P1 and get the value of C, because of protection.

#### How to achieve this? 
For this purpose, we use the concept of Shared Memory.

P1, P2 will agree on some space in the RAM.


![image](https://user-images.githubusercontent.com/74404132/129439649-03e11a04-bbb4-4935-b717-554fdc702469.png)

They have agreed upon the fact that they're going to communicate using this address 1000

So, after execution of P1, the value of C will be written in address 1000.

P2 will get the data from this address.

### address 1000 is not a PCB of a process! It is a shared memory.

Both P1, P2 'can' directly access memory space 1000

So we say them as shared memory.

Communication : nothing but giving data or taking data.

This communicaiton has taken place only because of "Shared Memory"

### Communication between any pair of processes will happen only with the concept of shared memory.

### Because of shared memory, we will get come disadvantages. 

Some memory space will be accessed by more than one process DIRECTLY.

Because of this, we are coming across some problems, and those problems has been overcome by using something called Process Synchronization.

        1. We will first see what problems we are comming across of this

        2. We wil see the various synchronization techiques. We have a lot of synchronization techniques. 

        3. We will see the advantages and disadvantages of every technique.

![image](https://user-images.githubusercontent.com/74404132/129440029-80c95be9-bf14-4def-a3a7-783931f85ff2.png)

P1 has function f1 with some lines of code (in any length)
has variable cnt ++

P1 has function f2 ans has cnt --

assume P1, P2 is somehow related.

assume we have supermarket.
var cnt is counts who are inside the supermarket at any point of time.

        Assume that P1 is written in order to increment the value of cnt, if a new customer enters the supermarket.

        Assume that P1 is written in order to decrement the value of cnt, if a new customer leaves the supermarket.

        So both these programs are trying to access the vaue of cnt.

        Where should I maintain the value of cnt? In a shared memory.

 One important point : you need to know this is a high level pr gram : this is the syntax which we programmers follow in order to write a program or software.

Computers cannot understand these languages.

These langage will be converted into something called as Assembly Code.

Assembly code is an intermediate between High level code and Machine code.

Only machine code will be understood by our computer.

![image](https://user-images.githubusercontent.com/74404132/129440414-fe53ce12-9ca7-4444-a409-d32a2452cf3a.png)

        LOAD cnt from R1

In Assembly Code, we will LOAD the val of cnt in some register 
ex) LOAD the val of cnt in reg named R1
assume val of cnt is now 0

### <P1>
        INCR R1

        * dont follow the syntax. It varies from one computer arch to another computer architecture.

        syntex = INCR, increment, r1 = r1 + 1

Machine code is exactly same as assembly code, but it wil be in binary format.

        STORE cnt, R1

Understand that our CPU will always fetch instruction by instruction and then it will execute it.

Not line by line, but instruction bt instruction.

### <P1>
        LOAD R2
        DECR R2
        STORE R2, cnt
         

Because of the concept of shared memory, p1 and p2 are sharing this memory.

How will this execution happen initially?
We have schedular.
 
 schedular has scheduled process P1. This process will completely run.

 먼저 실행되어야할 프로세스에 대한 설명이 뭐였더라?

if P1 execute completed then P2 execute, there is no problem.

It means there is no pre-emption!
Once we have started this process, only at the completion we are starting the next process. 

We generally follow pre-emptive scheduling algorithms.

Let's assume that P1 has went into I/O. It has went into I/O state : P1 needs some date from either hard disk or I/O devices, so it cannot be executed by CPU.

In this example, we cannot preempt this process and schedule process P2.
non-proemptive scheduling algorithm? start new process only after the completion of a particular process.

P2 cannot preempt P1 -> out cpu is remaining idle.
because it is undergoing I/O, we cannot premept this process and introduce other process because we are following non pre-emptive scheduling algorithm.

Effectively our CPU is remaining idle.


preemptive algorithm : 
    ex) we can execute 2 lines of this P1 And we can come back to P2, and execute 2~3 lines, and back to P1.

Thats what we mean by context switching.

 ...

 The value of count is not right due to preemptive scheduling.

        Why did this happen? Because of shared memory.

 Both process are trying to access shared memory, and because of this, we are getting the inconsistent data.

This is inconsistency.

We dont follow non-preemptive scheduling because CPU efficiency will drop down.

We can use preemptive schduing and go to synchronization algorithm. and get rid of inconsistency. 

The synchronization mechanism will introduce its own disadvantage.  

![image](https://user-images.githubusercontent.com/74404132/129443187-cb32ec81-deec-4346-925a-8bb1cc2c9234.png)

This piece of code is also called critical section.

Only executing three lines, Im accessing the shared memory.

![image](https://user-images.githubusercontent.com/74404132/129443292-4a9cec33-9fd2-4730-b71b-c68a33a8c384.png)


others are called remainder section.

CS: the piece of code which is actually making us to access the shared memory. 

Similarly, the three lines are the only way through which we are going to access the shared memory.

Lets assume htat we have no remainder section in code.

Wrong = inconsistency.
Initially, our schedular has scheduled the process.

Depending on the order in which we execute the instructions, we are getting different output. 

Even in preemptive algorithm. 

        P1 1 -> P1 2 -> P1 3 -> P2 1 -> P2 2 -> P2 3

is definitely possible.

But it is actually as gool as non-preemptive scheduling algorithm.

Se we will definitely get the correct output.

depending on the order od execution of the instructions, we are getting different output

This is race condition.

        Whether wchich order the CPU executes, we are supposed to get the correct answer and the only answer.

        We will always avoid race condition.

How can we avoid race condition?

We always get the right answer in case if you're following the sequential approach.


we access the cs at the same time for both P1 P2

CPU is execution the cs of both the processes at the same time.

        We should make sure that we are not in the critical section of more than one process. If we avoid this, everything will be solved.
    
        We are going to achieve this with synchronization

synchronization mechanism? It is a tech using which, we will make sure that we are not enthering into more than one process's critical section at the same time.

![image](https://user-images.githubusercontent.com/74404132/129444616-d0fc2825-3960-4742-bbdc-670d799ace06.png)

summary : we cannot enter CS at the same time - 4)

cs : part of the program that shared memory is accessed.

reminder section : shared memory is not accessed.

race condition :  the order of execution of instructions of processes defines the results produced 
