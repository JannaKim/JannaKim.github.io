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

![image](https://user-images.githubusercontent.com/74404132/129674067-522221b0-5303-4f27-b468-c12425cbc1f5.png)

Assume we have P1, P2 and we know all of the instructions.

In P1, it is only 3, 4 that is accessing the shared memory.
In P2, 4, 5

At any point of time, both processes should not be in the CS in the same time.

We need to avoid inconsistency and race condition

![image](https://user-images.githubusercontent.com/74404132/129674441-d3472b27-b6c8-4f39-809b-f30e7748de36.png)

Assume that we have two rooms. We dont want people to enter rooms at the smae time.  If one person enters room1, nobody should enter room 2 at the same time.

How can we do this? 

                We place a watchman and give him a single ticket or single token. If a new person comes to enter either one of the rooms, the watchman will give the token to this person, so the watchman doesn't have the token anymore.

                If a new person comes to enter some room, he will ask watchman for token. BUt watchman will be not have token because he gave it to previous person. So he will tell this person to wait.

                Once the previous guy comes out of the room, he will give the token to the watchman. So the watchman will give the token to the ney guy and he will enter the room.

                In this scenario, it will never come where both these rooms are having people at the same time.

                A person who wants to enter needs to get the token from the watchman and enter. If the watchman doesn't have the token, the person obviously has to wait.

The rooms are nothing but critical sections. We dont want two processes to be inside the critical section at the same time.

Our CPU obviously will fetch instruction by instruction and execute it.

![image](https://user-images.githubusercontent.com/74404132/129675879-8706c6b0-6bc2-416d-89b1-3fb991ee77f8.png)

After CPU has executed line 3, 
sssume the schedular has preempted this process, and had scheduled. 

In P2, 1, 2, 3 will be fetched and executed

                We should make sure that CPU doesn't fetch line 4 and execute it.

Because P1 is already in critical section.

After the CPU has "completed" P1 line 4, ans has started line 5.

How do we do this? 

![image](https://user-images.githubusercontent.com/74404132/129676591-7b7e2bf8-9b16-46f9-ab95-bd44d9cacf48.png)

We place a code above CS and below CS.

                A piece of code ? Its just a two or three lines of instructions.

                above : entry section

                below : exit section

What will this entry section and exit section do?

Before line 4, we are making the CPU th fetch entry section code one by one.

In entry section, we will check whether other process is inside the critical section or not, with the help of token.

In case the process is inside the critical section, CPU cannot march further.

Which means, our process will be blocked in the entry section.


Why do we need exit section?

Only after one process has come out of CS, other process can enter CS.

Once one process gets out of CS, watchman is getting the token back using Exit section code.

How will it stop the process ans for how long?

We will implement this code using while loop.

We will execute entry section code over and over just to check whether this process has come out of the critical section.

                This mechanism is synchronization mechanism.
                It is the tecnique of using entry section and exit section.

There are a lot of synchronization mechanisms.   


entry and exit section code can be written in a lot of ways.

Based on the way we write code, where will be a lot of synchronization mechanism.

We will see each one by one and see the advantages and disadvantages.

Base on written code, we classify the synchronization mechanism.

How will you tell which is a better synchronization mechanism?


![image](https://user-images.githubusercontent.com/74404132/129680442-5ce016fb-6398-4415-a74c-4900f09f6b7e.png)

                That judgement is made based on 3 parameters

                1. Mutual Exclusion
                2. Progress
                4. Bounded waiting

If a synchronization mechanism satisfiesd all these three conditions, than we will say that it is best.

1. Mutual Exclusion : A way of making sure that if one process is executing the CS, " then other processes " cannot enter the CS until the executing process comes out of the CS.

If not more than 1 process is inside the CS, it can be said that such a synchronization mechanism satisfies mutual exclusion.


We can execute the instructions of both these process in lots of ways.

 = Our CPU can execute these 2 programs in a lot of ways.

For example, 

P1 1, 2 -> P2
P1 1, 2, 3 -> P2

Our context switching can happen any time.

In all possible ways, whatever way we'll execute, 
we will always make sure that not more than 1 process can be inside the CS.

Than we say that mutual exclusion is satisfied.

If we are trying all the possible ways, but we cannot find even a single instance where more than 1 process is inside the critical section, than we can say that mutual execlusion is satisfied.


### basic idea of progress

if a process is not inside the critical section, it will not block other processes from entering the critical section.

When a process is inside the critical section, it is actually blocking other processes from enthering the critical section.

If a process is in non critical section, it should not block.

                But if a process is in a non-critical section and if it blocks other processe to enter the critical section, we can say that the progress is not satisfied for such a synchronization mechanism.


So everything depends on how we write the code for entry section and exit section.

If written in prefect way, it will satisfy progress.

If we make sure that if a progress is a non-critical section and never blocks other process from entering the CS, we cay say such synchronization mechanism satisfies progress.

In case there exists " even a single process " in non-critical section blocks others form entering critical section, it does not satisfy progress.
 

### basic idea of bounded waiting

idea: How will entry section look?

Generally, entry section will be written in the form of a while loop.

In while loop, we will have a relational statement.

If such condition is true, we will enter while loop, if false, cannot enter while loop

If we don't enter while loop, we will be entering critical section.

        Entry section's while loop will be true if other process is inside the CS
        false if the process is inside the CS.

        In case such process has left the critical section, we will make sure that while loop will return false.

How do we write this code depends on the various sychronization algorithm.

What can actually happen is, let us assume our CPU has scheduled P1.
 
Assume that P1 is CS has been preempted ans OS have scheduled P2.

The entry section of P2 is supposed to block entering the CS.

How ? Our while loop will return true.

While loop will be repeated again and again as long as P2 is preempted.

The CPU will be simply doing unnecessary work. Important thing is P2 is not entering the CS.

After P1 enters exit section, P1 execute non-critical section.

If it is made of while loop and P1 again enters entry section, it will not be blocked because other process is not in the CS.

Now let us assume that P1 is preempted by P2.

P2 again executes while loop since P1 is inside CS.

Let us assume that P2 is preempted by P1. 

P1 has completed exit section and again enters entry section.

It will easily enter CS.

                When P2 is executed, P2 still cannot enter Cs because P1 is in CS.

                This can keep on happening 

                This should not happen, because P2 is starving.

                If is not entering CS for infinite amount of time.

                P2 is not at all executing, whereas P1 is keep on executing.

                In our computer, every P is supposed to run.

All the softwares whould be working.

                We need to have a bound on the number of times a P can enter.

                Entry section should block the process though where is no P inside the CS, 
                still some process is waiting to enter the CS for a long time.

<br/>        

                Bounded Waiting : A way of making sure that there exists a bound (or limit) on the number of times other processes are allowed to enter the CS after a process of times other processes are allowed to enter the CS after a process has made request to enter TX, and "before" that request is granted.

                If some P is executing entry section, it means that it wants to enter the CS.

                After there has explictly set the desire to enter the CS, " there should be a bound " on the number of times this process can enter the critical section.

<br/>

                Once some P has expressed the desire to enter CS, there should be a bound or limit of number of times this process is allowed to enter into CS.


We can say that bounded waiting condition is guaranteed or satisfied.

Synchronization mechanism : writing entry section and exit section.

                If we wrote a good synchronization algorithm or mechanism, there will be a limit of number of times a P can enter, AFTER other P has "expressed" its desire to enter CS. = entered entry section


Important thing is, while loop ends in while(lock != 0);
lock = 1 is not the part of while loop

When lock == 0, P1 makes lock = 1 and enter CS.

When P1 is premempted and P2 is scheduled, P2 is blocked.

P2 will keep on revolving while loop, as long as P2 is running.

when lock == 1, other Ps should be blocked by entry section.

In this case, there is a chance that more than one P is inside CS.

Why not guaranteed? Lets assume P1 has been scheduled.

P1's while loop will be false 

                Assume that after P1 executes while(lock != 0);, P1 is preempted.

                P2 will again check while loop, and it will also be written false.

                Because P1 has not made lock equal to 1. Before P1 makes lock = 1;, P2 is scheduled.

Assume P2 is exceeding execution, makes lock = 1 and enters CS.

                If P1 is then executed, it will execute from the place where it left out.

P1 will make lock = 1, which is already 1.

More than one is in CS, and we might get inconsistency.

                Lets check whether this synchronization mechanism satisfies progress or not.

Progress ?  If a P is in non-CS, it should not block other P from entering CS.

When will a P kept block in the entry section? It will be blocked only if the value of lock is already 1

The val of lock is 1 only if there is a process inside CS.

It is not the case that P is in a non-CS and blocks entire P from entering CS.

Progress condition is definitely satisfied.

                Lets see whether bounded waiting is satisfied for this synchronization mechanism or not.

Bounded waiting? if a process has " expressed its desire " to enter the CS, then there should be a bound on the number of times " other processes " are allowed to enter CS.

Our synchronization doesnt satisfy bounded waiting.

