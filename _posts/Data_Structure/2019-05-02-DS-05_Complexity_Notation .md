---
layout: post
title:  Chapter 5 - Complexity notations
category: datastructure
description: Big O , Big Theta , Big Omega
---

# 5 Complexity Notaion

## 5.1 Asymptotic notations（漸進符號）

![Big-theta](https://i.imgur.com/KadyP7p.png)

### $\Theta$ -Notation


let g (n) be a function from a set of numbers to a set of numbers

$\Theta( g(n))$ is the set of those functions $f(n)$ for  which there exists positive constants $c1,c2$ and $n_{0}$ so that for all $n\geq n_{0}$,

-  $$
   0 \leq c_{1} \cdot g(n) \leq f(n) \leq c_{2} \cdot g(n)
   $$

   三文治夾住！

-  The function in the picture (c) $f(n) = \Theta (g(n))$

-  $ f(n) \in \Theta (g(n) $    f(n) is a member of $ \Theta (g(n))$ 

-   $f(n) = 3n^2 + 5n - 20 = \Theta (n^2)$

-  $
   a_{k}n^k +a_{k-1}n^k-1+... + a_{2}n^2 + a_{1}n + a_{0} = \Theta(n^k)
   $



### $O$ -Notation

-  Asymptotic upper bound
-  Worst-case efficiency


$  O( g(n))$ is the set of those functions $f(n)$ for which there exists positive constants  $c $  and  $n_{0}$ so that for all $n\geq n_{0}

$$
0 \leq f(n) \leq  c \cdot g(n)
$$



-  the function in the picture (a) $f(x) = O(g(n))$

-  if $f(n) = \Theta(g(n))$, then $f(n) =O(g(n))$
-  $n^2 = O(n^3)$ , but $n^2 \neq  \Theta(n^3)$
-  if $k\leq m, n^k = O(n^m)$, e.g. $2<=9, n^2 = O(n^9)$
-  if the **slower** case is $O(g(n))$ , then the running time of **every** case is $O(g(n))$ 



### $\Omega$ - Notation

-  Asymptotic lower bound
-  Best-case efficiency
-  
  $  O( g(n))$ is the set of those functions $f(n)$ for which there exists positive constants  $c $  and  $n_{0}$ so that for all $n\geq n_{0}$
  
$$
0\leq   c \cdot g(n) \leq f(n) 
$$

-  the function in the picture (b) $f(x) = \Omega(g(n)) $
-  $f(n)=\Theta(g(n) )$ if and only if $f(n) = O(g(n))$ and  $f(n) = \Omega(g(n)) $
-  if the **fastest** case is $\Omega(g(n)) $, the running time of **every** case is $\Omega(g(n))$



## 5.2 Concept of efficiency

-  not just in point of view of **running-time**
-  **Memory Consumption** 
-  **bandiwidth Usage**



### Running Time 

-  Any constant time operation can be used as the step
-  operation independent of the size of the input —> Constant time
-  variable assignment , if statement, a single step

-  $\Theta(1) + \Theta(1) = \Theta(1)$



### Memory Use

-  bit ,a byte,  a word
-  int —> 16,32 bits
-  char —> 8 bits
-  point —> 4 bytes
-  searching for a char string from an input file does not store the entire input but just scans through 



## 5.3 Binary Search

-   Search in sorted data
-  comparing a search key to middle element in the data
   -  divide the search area into two 
   -  choose the half where the key must be , ignore the other
   -  continue until only one element left
      -  it is the key 
      -  the element is not in the data set

```pseudocode
BIN-SEARCH(A,1,n,key)
	low:= 1; hi := n  //初始化
	
	while low < hi do //直至所以elem都已經被cover
		mid:= [low + hi /2]	//拿中點
		if(key <= A[mid])	//if the key is in the bottom half 
			hi = mid;
		else				//upper half 
			low:= mid + 1
			
	if A[low] = key then
		return low 		//found
	else
		return 0 			//not found
```



| Binary Search |         |
| ------------- | ------- |
| Best-Case     | Θ(1)    |
| Worst-Case    | Θ(logn) |
| Average-Case  | Θ(logn) |