---
layout: post
title:  Chapter 3 - Algorithm Design Technique
category: datastructure
description: Decrease and Conquer, Divide and Conquer, Randomization...
---


## Algorithm Design Techniques

### Decrease and Conquer

> **Decrease and Conquer** strategy is used if we could reduce a problem into its smaller state by a factor and solving for it. The solution to this smaller instance, would form the basis to larger instances of the same problem. 
>
> - Problem of size n
> - Solve for n - 1 (or n - constant factor)
> - Repeat the above and eventually the problem is reduce to something trivial that we can solve immediately. ie: n = 1 or n = 0



**Decrease** or reduce problem instance to smaller instance of the same problem and extend solution.
**Conquer** the problem by solving smaller instance of the problem.

### Insertion sort

#### Insertion Sort description

插入排序（插入分頁）的算法描述是一種簡單直觀的排序算法。它的工作原理是通過構建有序序列，對於未排序數據，在已排序序列中從後向前掃描，找到相應位置並插入。

#### Insertion Sort Steps:

一般都採用in-place在array上實現

1. 從第一個element開始，該元素可以認為已經被排序（sorted）
2.  取出下一個element，在sorted elements 序列中從後到前掃描
3. 如果該元素（sorted）大於new element， 將該元素移到下一個位置
4. 重複Step3，直到找到One of sorted elements that 小於或者等於new eleement的位置
5. 將new element 插入該位置後
6. 重複步驟2～5


#### Insertion sort **gif demonstration**

![selectionsort](https://i.imgur.com/BZlfKKJ.png)

```pseudocode
Insertion-Sort(A)  					//input the array A
	for j:=2 to A.length do 	 // increment the size of sorted range
           key := A[j] 			// handle the first unsorted element 
           i = j - 1 
      
          while i > 0 and key < A[i] do //find the correct location for the new element
                A[i+1] := A[i]			 //make room for the new element
                i = i - 1 

          A[i+1] := key			 // set the new element to its correct location
```



#### Decrease and Conquer in Insertion-Sort

- Initially the entire array is unsorted
- on each round the size of the sorted range in the beginning of the array increases by one element
- in the end the entrie array is sorted

----



### Divide and Conquer

- The problem is divided into several subproblems that are like the original but smaller in size
- Small subproblems are solved straightforwardly



#### Divide and Conquer in QuickSort

快速排序的基本思想：通過一趟排序將待排記錄**分隔成獨立的兩部分**，其中一部分**記錄的關鍵字**均比另一部分的**關鍵字小**，則可分別對這兩部分記錄繼續進行排序，以達到整個序列有序。

- 從Array中挑出一個元素，稱為"pivot"
- 重新排列Array， 所有元素比pivot值小的擺放在pivot前面，所有元素比pivot值大的放在pivot後面相同的數可以到任何一邊。在這個paritiion退出後，該pivot便位於數列的中間的位置，已經in order
- 遞歸地（Recursively）把小於基準值元素的subArray和大於pivot值的元素的subArray排序

![quicksort](https://i.imgur.com/SLkOUNU.png)

``` pseudocode
QuickSort-algorithm

QUICKSORT(A, left, right)

if left < right then
	pivot:=PARTITION(A,left,right)
	QUICKSORT(A, left, pivot-1)
	QUICKSORT(A, pivot+1, right)
	
 

PARTITION(A, left, right){
	pivot := A[right] //choose the last element as the pivot
	i := left -1 // use i to mark the end of the smaller elements
	
	for j:=left to right-1 do //scan to second last element
      if A[j] <= pivot // (if A[j] goes to the half with the smaller elements
          i := i + 1 // increment the amount of the smaller elements
          exchange A[i] with A[j] //and move A[j] there
      exchange A[i + 1] with A[right]  //place the pivot between the halves
	return i + 1// return the location pivot
}

```



### Algorithm Design Technique: Randomization

-  **avoid worst-case** inputs
-  likelihood(可能性) of the **best-case and worst-case  in practise decreases**
-  The input can be randomized
   -  **before** running the algorithm
   -  by **embedding** the randomization into the algorithm

-  QUICKSORT can choose any element in the array as the pivot
   -  elements besides largest and smallest are good
   -  difficult to guess whether the selected element is smallest / largest
   -  a few bad guesses doesn't ruin the effciency of QUICKSORT

### Algorithm Design Technique: Transform and Conquer

-  modfies the problem's instance to be more amemable to solution
-  The problem is solved
-  Three way to transform the instance
   -  Instance simplification
   -  Representation change
   -  Problem Reduction

