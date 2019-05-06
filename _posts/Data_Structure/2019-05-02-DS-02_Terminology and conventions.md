---
layout: post
title:  Chapter 2 - Terminology and conventions
category: datastructure
description: Some terms and methods
---
## Terminology and conventions

### Goals of the course

> The main goal of the course is to provide a sufficient knowledge on and the basic tools for choosing the most suitable solution to a given programming problem

The course concentrates on **choosing a suitable dat astructure** for **solving a given problem**.

In addition, **common types of problems** and **the algorithms**
**to solve them are covered.**



### Termininology

#### Data Structure

A data structure is a collection of related data items stored in a **segment** of the computer’s memory

- data can be **added** and **searched** by suitable alogorithms
- a data structure can **consist of other data structures**

#### Algorithms

An algorithm is a ***<u>well defined</u>*** set of instructions that takes in a set of input** and produces **a set of output**, i.e. it gives a solution
to a given problem.

> #### Well defined
>
> - each step is detailed enough for the reader (human or
>   machine) to execute
> - each step in unambiguous(明確的)
> - the same requirements apply to the execution order of
>   the steps
> - the execution is finite

An algorithm solves a well defined problem

- the **relation** between <u>the results</u> and <u>the given input</u> is determined by the problem

  e.g 

  1. sorting the contents of the array

     **input**: a sequence of numbers a<sub>1</sub>, a<sub>2</sub>, …..a<sub>n</sub>

     **results**: Numbers  a<sub>1</sub>, a<sub>2</sub>, …..a<sub>n</sub> are sorted into an ascending order

  2. finding flight connetions

     **input**:a graph of flight connections, cities of departure and destination

     **results**:Flight numbers, connection and price information

     

#### Incorrect Algorithm

an algorithm can be **incorrect** in three different ways:

- producing an incorrect result
- crashing dring execution
- never halts .e.g. infinite execution 

an **incorrect algorithm** may sometimes be a very **usefull** one
<u>as long as a certain **amount of errors** is tolerated</u>. e.g. (Prime checking)



#### Choosing a Algorithm 

-  Key factor in choosing an algorithm is its **efficiency** in that situation. 
-  **Implemntation** is easy?
-  **Precision** of the results?
-  Variable of the **running-time**?
-  The programming environment limitations
   -  maximum size of arrays
   -  memory ran out with lists, not with arrays
   -  recursion space, memory
-  size  of the input data?
-  worst-case allowed?
-  Memroy use
-  one execution or several exectuions