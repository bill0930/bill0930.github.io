---
layout: post
title:  Chapter 4 - Asymptotic notations
category: datastructure
description: efficiency of a algoorithm
---

# Asymptotic notations


- It is **occasionally important to know the exact time it takes** to perform a certain operation.
- It is most of the time of it  is enough to know how the **running time of the algorithm changes as the input gets larger**.
- The **calculations are not tied to a given processor**, architecture or a programming language



![BigOnotation](https://i.imgur.com/UYCBsJV.png)

Clearly
==O(n!) > O(2<sup>n</sup>>) > O(n<sup>2</sup>>) > O(nlogn) > O(n) > O(logn) > O(1)==



![datastructure_complexity](/Users/billy/Documents/Learning_Notes/Data_Structures/images/datastructure_complexity.png)

![Sorting_complexity](https://i.imgur.com/jIfYUL1.png)

```pseudocode
Linear Search(A, x)
for i := 1 to A.length do
	if A[i] = x then 
			return i 
```

| Linear Search |      |
| ------------- | ---- |
| Best-Case     | Θ(1) |
| Worst-Case    | Θ(n) |
| Average-Case  | Θ(n) |


```pseudocode
//finding the common element in two arrays
FindingCommonElement(A,B)
for i :=1 to A.length do
	for j:=1 to B.length do
		If A[i] = B[j] then
			return A[i]
```
| Common Element |        |
| -------------- | ------ |
| Best-Case      | Θ(1)   |
| Worst-Case     | Θ(n^2) |
| Average-Case   | Θ(n^2) |



```pseudocode
Insertion-Sort(A)
for j:=2 to A.length do  // n times
   key:= A[j]  // n -1 times;
   i := j - 1  //n -1 times;
   while i > 0 and A[i]>key do 
      A[i+1] := A[i]
      i = i - 1
	A[i+1]:=key
```

| Insertion Sort |        |
| -------------- | ------ |
| Best-Case      | Θ(n)   |
| Worst-Case     | Θ(n^2) |
| Average-Case   | Θ(n^2) |



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

| Quick Sort |     	   |
| -------------- | ------ |
| Best-Case      | Θ(nlogn) |
| Worst-Case     | Θ(n^2) |
| Average-Case   | Θ(nlogn) |


``` pseudocode
MERGE-SORT(A, left, right)
	if left < right then  					// if there are elements in the array
			middle :=  (left + right)/2 //	divide it into half
			MERGE-SORT(A,left,middle) 	// sort the upper half
			MERGE-SORT(A,middle+1,right) //... and the lower half
			MERGE(A,left,middle,right)	// 將兩個subarray做比較, 並合併出排序後的矩陣


MERGE(A, left, middle, right)
	for i:= left to right do 		//scan through the array
		B[i] := A[i] 						// and copy it into a temporary array
	
	i:=left									// set i to indicate the endpoint of the sorted part
	j:= left ,k:= middle + 1 //set j to indicate the beginning of lower half array
														// set k to indicate the begining of upeer half array
	while j<=middle && k<= right do	//Scan直至其中j或指向subarray的end
		if B[j]<=B[k] then  // if the first element in the lower half is samller 
			A[i] := B[j]			//copy it into the result array
			j:=j+1						//increment the starting point of lower half
		else
			A[i]:=B[k]			//copy the first element of upper half
			k:=k+1					//and increment its starting point
		i:=i+1						//increment its strating point of the finished set
------------------------
//各個subarray可能差最後一個element未放入A[i]
	if j>middle then   		//如果upper subarray未放曬入A[i]
		k:= 0
	else 								//如果lower subarray未放曬入A[i]
		k:=middle - right
		
		for j:=i to right do
			A[j] := B[j+k]
```

MERGE Process
![Mergesort](https://i.imgur.com/GdS3RSh.png)

| Merge Sort |     	   |
| -------------- | ------ |
| Best-Case      | Θ(nlogn) |
| Worst-Case     | Θ(nlogn) |
| Average-Case   | Θ(nlogn) |

