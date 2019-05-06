---
layout: post
title:  Chapter 2 - Single Page Application
category: Web-Architecture
description: Chapter 2
---

# Single Page Application 

### Traditional HTML output and SPA 

#### Traditional HTML output 

-  the server outputs HTML shown in the browser, typically the entire page
-  Increases data exchange, server work load, latencies



#### SPA

-  UI Clients
-  The Client has a JavaScript layer that communicates with the server
-  Fast, efficient, reduces server work load but increases client work load

### MVC

-  Model-View-Controller Pattern
-  Pros
   -  better and **eaiser code maintanance and reusability**
   -  easier to **coordinate in teams** due to the sepration
   -  ability to provide **multiple views**
   -  support for **asynchronous implementation**
-  Cons
   -  an increased complex setup process
   -  dependencies, changed in model or controller affect the whole entity

![img](https://pic1.zhimg.com/80/3d2abf5c8d81424c4797201384b456ac_hd.png)

![img](https://cdn-images-1.medium.com/max/800/0*DJAFh9Y0CnIAPu7X.png)

-  Limitation
   -  When Multiple Views and Multiple Models
   -  ![img](https://pic4.zhimg.com/80/74383cc223b0a29bec6650826bdc72cb_hd.png)

### React, Flux

-  Flux 
   -  to remove the need of bidirectional communication and 
   -  reduce cascading effects
-  Terms
   -  **Actions**
      -  objects with property and data
   -  **Stores**
      -  Contains the application's state and logic
   -  **The dispatcher**
      -  proccesses registered actions and callbacks
   -  **Views**
      -  Listen to changed from the stores and re-render themselves
   
   ![flux-architecture](https://danke77.github.io/2016/10/25/understanding-flux/flux-architecture.png)

![flux-data-flow](https://danke77.github.io/2016/10/25/understanding-flux/flux-data-flow.png)

[怎样理顺react，flux，redux这些概念的关系，开发中有必要使用它们吗?](https://www.zhihu.com/question/47686258/answer/107209140)

#### VS MVC

-  Flux is unidirectional instead of bidirectional
-  Stores are able to store any application related state
   -  whereas the model in MVC was designed to store single objects the initiating point
-  Dispatcher makes debugging much easier



### Redux 

-  Principle
   -  **Single source of truth**
   -  **state is read-only**
      -  The only way to change the state is to emit an action
   -  **Changed are made with pure functions** 
      -  arguments not change
      -  always return the same set of arguments according to the arguments
      -  it doesnt mutate any data and it doesn't have any side affects
   -  Speicfy the transformation by actions with reducers, which allow to navigate through states.



-  Do not have the concept of a *dispatcher* because it relies on pure functions instead of event emitters
-  Redux assumes you never mutate your data. It return a new object.

![Redux åºç¡ - react å¨å®¶æ¡¶å­¦ä¹ ç¬è®°ï¼ä¸ï¼](https://pic1.zhimg.com/v2-2a204f8894aedc7458c236c072966d08_1200x500.jpg)