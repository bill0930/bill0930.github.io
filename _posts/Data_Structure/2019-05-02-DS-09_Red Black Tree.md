---
layout: post
title:  Chapter 9 - RedBlack Tree
category: datastructure
description: balanced tree 
---

# Red Black Tree

## General

![img](https://github.com/julycoding/The-Art-Of-Programming-By-July/raw/master/ebook/images/rbtree/1.png)



-  Are balanced binary search trees
-  when making addition and removals
   -  modified the trees to keep balanced 
-  Basic idea of red-black trees
   -  each node contains one extra bit : its colour
      -  either is red or black
   -  the other fields are the old key,  left, right, p
   -  the colour fields are used to maintain the red-black
-  Invariant to quarantees that the height of the tree is kept in $\Theta(logn)$



### Invariant of red-black trees

1. If the node is red, it either has (紅node不能只有一個黑child)
   -  no children, or
   -  it has two children, both of them black
2. for each node, all paths from a node down to **descendant** leaves contains **the same number of black nodes** 
3. The **root** is black

>  1.节点是红色或黑色。
>
>  2.根节点是黑色。
>
>  3.每个叶子节点都是黑色的空节点（NIL节点）。
>
>  4 每个红色节点的两个子节点都是黑色。(从每个叶子到根的所有路径上不能有两个连续的红色节点)
>
>  5.从任一节点到其每个叶子的所有路径都包含相同数目的黑色节点。



### Black height

-  The black height of the node $xbh(x)$ is
   -  the amount of black nodes on the path from it down to the node with 1 or 0 children.
   -  all alternate paths from the root downwards have the same amount of black nodes
   -  the black height of the tree is the black height of its root
-  The maxium height of a red-black tree
   -  $h $ is the height, $n$ is the amount of nodes
   -   at least **half the nodes** on any path from the root down to a leaf $\frac{h}{2}+1$ **are black*
   -  there is the same amount of black nodes on each path from the root down to a leaf

#### LEFT-ROTATE

![TreeMap_rotateLeft.png](https://images2015.cnblogs.com/blog/939998/201605/939998-20160517212009529-1958413310.png)

```pseudocode
LEFT-ROTATE(T,x)
y:= x->right ;  //relationship
x->right := y->left 	//讓x的right指向y的leftchild

if y->left != NULL then //更新y的leftchild的parent
	y->left->p := x 
// x 和 A，B成功互相指向
----------------------
if x->p =NULL // x 是 root
	T.root = y //讓y做root
else if x = x->p->left //x是parent的leftchild
	x->p->left :=y //update y
else if x = x->p->right //x是parent的leftchild
	x->p->right := y 
y->left := x, 
x->p:=y

--------------------
x 始終與他的leftchild連線
y 始終與他的rightchild連線


```

new item : u

u's parent : t

t 's sibling v

t and v 's parent : p

