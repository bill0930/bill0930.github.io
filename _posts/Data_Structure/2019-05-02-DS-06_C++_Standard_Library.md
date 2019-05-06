---
layout: post
title:  Chapter 6 - The C++ Standard Library
category: datastructure
description: Some  C++ coding
---

# The C++ Standard Library

## 6.1 General

-  STL, standardised together with C++ language autumn 1998
-  C++17 2017
-  Cotain most important basic data structures and algorithms
-  contains
   -  Inputs/output ,cin,cout..
   -  processing character strings
   -  minimum,maimum
   -  search / modifying operations of queues
   -  support for functional programming
   -  complex number
   -  arithmetic fnctions
   -  vector arithmetrics and support for matrix 
-  Lambdas , C++ 11
-  Generic algorithms with iterators



## 6.2 Iterators

-  STL data structures as **black boxes** with a lot of common characteristics
-  They contain the **elements** we have stored in them 
-  They implement a certain **set of interface functions**
-  We can only **handle the contents of the containers** through 
   -  the interface functions
   -  the iterator

![enter image description here](https://i.stack.imgur.com/ZsVTd.png)

-  Each iterator points to 
   -  the begining or the end of the data structure  
   -  between two elements 
-  The element **on the right side** of the iterator can be **accessed** through it
   -  except if the question is a ***reverse iterator*** which is used to access the element on the **left side**
-  The operations of moving the reverse iterator work in reverse, ++i, moves iterator on step to the left  (i++時，iterator正路右行，但reverse iterator就向左行)
-  The container can invoke  the iterators poinitng to the beginning and the end of the container by `container.begin(),  container.end()`  
-  `container.rbegin(),  container.rend()`return the reverse iterators
-  An iterators can be used 
   -  reading or writing
   -  iterate over the elements of the container

Each Container has its own iterator type

-  different containers provide different possibilities of moving the iterator from one place to another efficiently
-  iterators can be divided into categories based on which constant time operations they are able to provide

 ![Picture 2013-05-10 17_41_33](https://images0.cnblogs.com/blog/84159/201305/10174640-d48d2bb8ecb24391b36519e17db20309.png)

Input Iterator

-  read elements values but not change them
-  `*p` (read the value by dereferencing iterator p )
-  `p->first` `p->second` (a field of the element the itertaor points to can be read or its memeber function can be called)
-  `++p / p++` move one step forward
-  `p=q, p==q, p!=q` assign/ compare


#### output iterator 

-  An output iterator is like an *input iterator* but it can be **used only to change the elements (*p=x)**

#### forward iterator

-	A forwaed iterator is a **combination** of the interfaces of the **input and output iterators**

#### bidirectional iterator 

A bidirectional iterator is able to move one step at a time backwards(--p or p--)

#### random access iterator 
A random access iterator is like a bidirectional iterator but it can be **moved an arbitrary amount of steps forwards or backwards**.



## 6.3 Containers

-  Two types of container

   ![container_concepts.png (242Ã97)](https://www.cs.helsinki.fi/u/tpkarkka/alglib/k06/lectures/container_concepts.png)

   -  **sequences**
      -  can be searched based on their number in the container a[0],a[1]
      -  Can be added and removed at the desired location 
      -  can be scanned based on their order
      -  array,vector,deque,list,forward_list
   -  **associative containers**
      -  elements placed in the container to the location determined by their ***key***
      -  operator < can be used to compare the key values of elements in the ordered containers
      -  map, set, unordered_map, unordered_set

- Adapters : Queue Stack

- Containers are **passed by value**

   - It takes **a copy of the data** stroed in it and returns copies of the data it contains
   - Elements stored into the containers must **implement a copy constructor and an assignment operator**
   -  Elements of a type defined by the user **should be stored**
      **with a pointer** pointing to them(efficiency)

```c++
  std::shared_ptr<int> foo = std::make_shared<int> (10);
  std::cout << "*foo: " << *foo << '\n'; //(*foo: 10)
```

![containers](https://i.imgur.com/SBpXnPz.png)

### Sequence container 

#### Array

```c++
template < class T, size_t N > 
class array;
```

```c++
//Initialization
array<int, 3> a = {1, 2, 3};

array<int, 100> b = {1, 2, 3};  // a[0] ~ a[2] = 1, 2, 3; a[3] ~ a[99] = 0, 0, 0 ... 0;

array<int, 3> c; //c[0]~c[2] not yet initialized
```

```c++
Array<int , 10> array
array.size();
array.max_size();
array.at(0);
array[0];
array.front();
array.back();

//Modifier
array.fill(5); //fill the array with the value 5
array.swap(array2) //swap the value with another array

```



#### Vector

```c++
template < class T, class Alloc = allocator<T> >
class vector; // generic template
```

```c++
//Initialization
  std::vector<int> first;                                // empty vector of ints
  std::vector<int> second (4,100);                       // four ints with value 100
  std::vector<int> third (second.begin(),second.end());  // iterating through second
  std::vector<int> fourth (third);                       // a copy of third

// Constant time Indexing .at(),[]
// Constant time addition push_back() and removel pop_back()
// Linear time Insertion with insert() and removal erase() O(n)
// emplace_back(args) build the element directly into the vector
// Size can ce increased by .resize(size, initial_val)
```

Iterators invalidated when

-  Insertion
   -   All iterators which point to an element **before the point of insertion are unaffected** but all others are invalidated.
   -   If the size is larger due to insertion, all iterators get invalidated .
-  Removal
   -  Every iterator and reference after the point of erasing is invalidated.



#### Deque 

```c++
template < class T, class Alloc = allocator<T> > 
class deque;
```

```C++
 std::deque<int> first;                                // empty deque of ints
  std::deque<int> second (4,100);                       // four ints with value 100
  std::deque<int> third (second.begin(),second.end());  // iterating through second
  std::deque<int> fourth (third);   

//Amortized running-time of adddition and removal at both ends
second.push_front(val);
second.emplace_front(args);
second.pop_front();
```

Iterators invalidated when

-  Insertion
   -  All iterators and references are invalidated
      -  unless the inserted member is **at an end (front or back)** of the deque
         -  all iterators are invalidated, but **references to elements are unaffected**
-  Removal
   -   All iterators and references are invalidated
      -  unless the erased members are **at an end (front or back)** of the deque
         -  only iterators and references to **the erased members are invalidated**



#### List

```c++
template < class T, class Alloc = allocator<T> > 
class list;

//Constructor
  std::list<int> first;                                // empty list of ints
  std::list<int> second (4,100);                       // four ints with value 100
  std::list<int> third (second.begin(),second.end());  // iterating through second
  std::list<int> fourth (third);                       // a copy of third

// Constant time in Addition and Removal
// Addition and Removal do not invalidate the iterators or references (except naturally to elements removed)

//transfer the element from list to list
list1.splice(location, list2) // makes the other list a part of the second list in front of the location
list1.splice(location, list2, val) // moves an element from another list or the same list in front of the location 

```





### Amortized running time（攤分運作時間）

-  ```pseudocode
   Insert 11  |11|
              +--+
              +--+--+
   Insert 12  |11|12|
              +--+--+
              +--+--+--+--+
   Insert 13  |11|12|13|  |
              +--+--+--+--+
              +--+--+--+--+
   Insert 14  |11|12|13|14|
              +--+--+--+--+
              +--+--+--+--+--+--+--+--+
   Insert 15  |11|12|13|14|15|  |  |  |
              +--+--+--+--+--+--+--+--+
   ```

-  When insert 12, 15  , the arraysize has been doubled.
  
   -  it taks O(n) to create a double-size array and do a copy the old value to the new array
-  Otherwise, it takes O(1) times to do the insertion
- The average operation time is  $\frac{nO(1)+O(n)}{n+1}$ , which is a constant.

-  each size addition operation that requires expensive memory allocation is preceded by an amount of inexpensive additions relative to the price of the expensive operation(在expensive additon 操作之前都經歷過很多inexpensive addtion)
-  the cost of the expensive operation can be equally divided to the inexpensive operations
-  now the inexpensive operation are still constant time
-  the savings can be used to pay for the expensive operation



### Associative container 

#### set and multiset

-  Can be Searched added and delted in logarithmic time $\Theta(logn)$

-  Can be Scanned in ascending order in amortized constant time. $\Theta(1)$

-  Scan from the beginning to the end is alwasy in a linear time $\Theta( n )$

-  The same element can be in the multiset several times

-  In the set elements are unique

-  Chaning the value of the element directly has been prohibited

   -  The old element needs to be removed and new one added instead(先刪除舊元素後增加新元素，不能直接改變)

  

```c++
template < class T,                        // set::key_type/value_type
           class Compare = less<T>,        // set::key_compare/value_compare
           class Alloc = allocator<T>      // set::allocator_type
           > class set;

//Constructor
 std::set<int> first;                           // empty set of ints

  int myints[]= {10,20,30,40,50};
  std::set<int> second (myints,myints+5);        // range

  std::set<int> third (second);                  // a copy of second

  std::set<int> fourth (second.begin(), second.end());  // iterator ctor.

  std::set<int,classcomp> fifth;                 // class as Compare

  bool(*fn_pt)(int,int) = fncomp;
  std::set<int,bool(*)(int,int)> sixth (fn_pt);  // function pointer as Compare

.find(val)  //Get iterator to element (public member function )
.lower_bound(val)  finds the first element ≥ element
.upper_bound(val) finds the first element > element
```

#### map and multimap

-  the type of the pair is pari<T1,T2>
-  a pair can be created by make_pair
-  .first() .second()

```c++
template < class Key,                                     // map::key_type
           class T,                                       // map::mapped_type
           class Compare = less<Key>,                     // map::key_compare
           class Alloc = allocator<pair<const Key,T> >    // map::allocator_type
           > class map;

the type is a pair
typedef pair<const Key, T> value_type;
 foo = std::make_pair (10,20);

bool fncomp (char lhs, char rhs) {return lhs<rhs;}

struct classcomp {
  bool operator() (const char& lhs, const char& rhs) const
  {return lhs<rhs;}
};

std::map<char,int> first;

  first['a']=10;
  first['b']=30;
  first['c']=50;
  first['d']=70;

  std::map<char,int> second (first.begin(),first.end());
  std::map<char,int> third (second);
  std::map<char,int,classcomp> fourth;                 // class as Compare

  bool(*fn_pt)(char,char) = fncomp;
  std::map<char,int,bool(*)(char,char)> fifth (fn_pt); // function pointer as Compare

  return 0;
```



#### Hash Tables

![img](https://upload.wikimedia.org/wikipedia/commons/thumb/7/7d/Hash_table_3_1_1_0_1_0_0_SP.svg/315px-Hash_table_3_1_1_0_1_0_0_SP.svg.png)

-  Unordered **Set and Multiset** is a structure hat containts a set of elements and unodered map/multimap contains **a set of key-value** pairs.

-  The elements are not ordered
-  Addition, Removal, and searching is on average constant time 
   -  worst case is linear time
-  The size of hash table is automatically increased
   -  because it has to keep the ***load factor*** 
   -  the number of keys stored in the **hash table** divided by **the capacity**



#### Stack 

![stack](https://i.imgur.com/ki0tqW0.png)

```c++
template <class T, class Container = deque<T> > class stack;

  std::deque<int> mydeque (3,100);          // deque with 3 elements
  std::vector<int> myvector (2,200);        // vector with 2 elements

  std::stack<int> first;                    // empty stack
  std::stack<int> second (mydeque);         // stack initialized to copy of deque

  std::stack<int,std::vector<int> > third;  // empty stack using vector
  std::stack<int,std::vector<int> > fourth (myvector);

stack.size();
stack.top();
stack.push(val);
stack.pop();
stack.empty()
```

#### Queue

![ãqueueãçåçæå°çµæ](https://www.geeksforgeeks.org/wp-content/uploads/gq/2014/02/Queue.png)

```c++
template <class T, class Container = deque<T> >
class queue;

  std::deque<int> mydeck (3,100);        // deque with 3 elements
  std::list<int> mylist (2,200);         // list with 2 elements

  std::queue<int> first;                 // empty queue
  std::queue<int> second (mydeck);       // queue initialized to copy of deque

  std::queue<int,std::list<int> > third; // empty queue with list as underlying container
  std::queue<int,std::list<int> > fourth (mylist);
```

#### Priority_Queue

-  identical interface as queue
-  implemented with a heap
-  top() returns the largest

```c++
template <class T, class Container = vector<T>,
class Compare = less<typename Container::value_type> > 
class priority_queue;

class mycomparison
{
  bool reverse;
public:
  mycomparison(const bool& revparam=false)
    {reverse=revparam;}
  bool operator() (const int& lhs, const int&rhs) const
  {
    if (reverse) return (lhs>rhs);
    else return (lhs<rhs);
  }
};

int main ()
{
  int myints[]= {10,60,50,20};

  std::priority_queue<int> first;
  std::priority_queue<int> second (myints,myints+4);
  std::priority_queue<int, std::vector<int>, std::greater<int> >
                            third (myints,myints+4);
  // using mycomparison:
  typedef std::priority_queue<int,std::vector<int>,mycomparison> mypq_type;
   
   
```



-------

## 6.4 Generic Algorithm

-  All algorithms have been implemented with function templates that get all the necessary information about the containers through their parametres
-  The container are not passed directly as a paramount to the algorithm
   -  iterators to the containers are passed
   -  parts of container can be handled
-  The standard library algorithm are in $algorithm$
-  The standard defines the C-language libray $cstdlib$



### Binary Search

-  *binary_search(first, end, value)* return boolean



### Sorting Algorithms

-  *sort(beg,end)* and *stable_sort(beg,end)*
   -  cannot be used with lists
-  *partial_sort(beg, middle, end)*
-  *is_sorted(beg, end)*
-  *is_sorted_until(beg, end)*

-  *nth_element( first, nth, end )*  //• finds the element that would be at index nth in a sorted container



### Partition 

-  *partition(first, end, condition)*
-  *stable_partition(first, end, condition)*
-  *merge( beg1 , end1 , beg2 , end2 , target)*
   -  • The algorithm merges the elements in the ranges beg1 - end1 and beg2 - end2 and copies them in an ascending order to the end of the iterator target

### Heaps

-  push_heap(first, end) ==>对刚插入的（尾部）元素做堆排序
-  pop_heap(first, end) ==> 将front（即第一个最大元素）移动到end的前部，同时将剩下的元素重新构造成(堆排序)一个新的heap。
-  make_heap( first, end) BUILD-HEAP
-  • sort_heap( first, end ) HEAPSORT



### Set

-   *includes( first1 , end1 , first2 , end2 ) subset ⊆*
-  *set_union( first1 , end1 , first2 , end2 , result ) union ∪*
-  *set_intersection(. . . ) intersection ∩*
-  *set_difference(. . . ) difference -*
-  *set_symmetric_difference(. . . )*



## 6.5 Lambdas ()(){}
   *find_if, for_each, sort*
-  ```c++
   [environment](parameters) -> returntype {body}
   e.g. 
      [](int x , int y ){
      return x + y;
   }
   
   for_each(v.begin(),v.end(),,[] (int val) {cout<<val<<endl;})
   ```

