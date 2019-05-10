---
layout: post
title:  Chapter 6 - Serverless Computing
category: Web-Architecture
description: Chapter 6
---
# Servereless Computing 

### The evolution - the big picture of software



![BigPicture](https://i.imgur.com/Q1SRi2Z.png)

### IaaS vs CaaS vs PaaS vs Faas

   

![IaaS](https://2.bp.blogspot.com/-up9VKdT6Dc0/WrBnlNcERsI/AAAAAAABPN4/aHdsMceWrvcwATkoFa61lDbOTD6DSvqtACLcBGAs/s640/FaaS.png)



-  Infrastructure as a Service (IaaS) — Amazon EC2, Azure VMs, ect.
-  Containers as a Service (Caas) — Docker Cloud, Amazon ECS ect.
-  Platform as a Service (Paas) — Heroku, Amazon Elastic Beanstalk, ect.
-  Function as a Service (Faas) — AWS Lambda, Google Cloud Functions ect.

![img](https://1.bp.blogspot.com/-GUlqTjNmTf4/WrBtLt31kyI/AAAAAAABPOc/ZC-2JH_cH5E5eHvLygaSPBTzNzz48so-wCLcBGAs/s640/FaaS%2BGood.gif)

### What is Serverless

-  Serverless abstracts infrastructure and its provision, scaling, maintenance
-  In genreal , Serverless architecture refers to <u>software system architecture</u> where the application is built using serverless components (computation, storage and networking)
-  In essence, it allows developers to focus on developing value-adding functionality without having to bother with complex infrastructure.
-  Resource costs are well aliged with usage



#### Definition

>   Serverless computing allows you to build and run applications and services without thinking about servers. Serverless applications don’t require you to provision, scale, and manage any servers. You can build them for nearly any type of application or backend service, and everything required to run and scale your application with high availability is handled for you.					—AWS
>



### Monlithic Services

-  microservices and
   functions
-  ![monilihic](https://docs.microsoft.com/en-us/azure/service-fabric/media/service-fabric-overview-microservices/monolithic-vs-micro.png)

-  typically buit on top of complex frameworks
-  Technologies ar defined by base components
-  Often a lot of shared code even with independently deployable pieces
-  More susceptible to system-wide failures
-  Scaling involves updating or replicating the whole stack

### **Microservices**

-  Independently deployable, bounded scope components, message based communication
-  In contrast to monolithic services
   -  mutiple smaller code bases
   -  Freedom to choose technologies within the service
   -  Less coupled failures
   -  Individually monitored
   -  Individually scaled

### Microservices vs SOA

-  **Service Orientated Architecture**
   -  Everything is a service, reusable, independent development and deployent
   -  Loose coupling, late biniding
-  **Microservices**
   -  Typically stateless communication
   -  Run services independently
   -  Develop using different technology
   -  Linux Containers made popular

### Functions 

-  Functions can be as little as a few lines of code that are handed over the platform provider(AWS lambda)
   -  The provider will take care of hardware, virtualisation, containerisation
-  API gateways in front of functions to handle incoming requests
-  Limitations
   -  on resources: memory, CPU, how long operations can run
   -  Amount of connections : other functions, databases
-  Asynchronous 
   -  promote event-driven execution model
   -  Decoupled from other components and each other

### Serverless vs server 

-  a remote API including deployment, config, monitoring ,logging
-  No SSH to servers
-  No containers
-  All focus on application functionality and architecture

### Co-evolution of Functions and APIs 

-  API lifecycle is tied to the evolution of functions and this extra mapping needs governmance
-  Minor release
   -  backward compatible, no updates required from users, semantics intact
   -  changes are of addictive or optional nature
-  Major release
   -  allowed to break compatibility
   -  migration is planned and managed 

### Pros and Cons serverless 

| Advantages                                                  | Disadvantage                                                 |
| ----------------------------------------------------------- | ------------------------------------------------------------ |
| Lower adminstration and management effort                   | No compatibility                                             |
| Focus on adding value—> faster time-to-market               | Vendor lock-in                                               |
| Auto-scaling                                                | No control                                                   |
| Pay-per-execution, not for idle                             | Cold starts and resource limitation                          |
| Codebase separation , independence of functions (and teams) | Complex apps are still hard to build, harder to maintain etc. |



### Hybrid Approach

|               | *Serverless*        | *Microservice*            |
| ------------- | ------------------- | ------------------------- |
| **Benefits**  | Cheaper to operate  | Always On                 |
|               | Less management     | No resource limitation    |
| **Drawbacks** | Only Async          | More expensive to operate |
|               | Resource limitation | More management           |

-  Microservice for request-response communication in customer facing APIs
-  Functions for operations with indirect or neglible impact to users(e.g. logging, billing, post-processing)



### Serverless Platform

#### Azure Functions

-  Azure Functions is a solution for easily running small pieces of code, or "functions," in the cloud. You can write just the code you need for the problem at hand, without worrying about a whole application or the infrastructure to run it.

#### Amazon AWS Serveless and Lambda

- AWS Lambda lets you run code without provisioning or managing servers. You pay only for the compute time you consume - there is no charge when your code is not running.”

#### Google Cloud Funtions

- Cloud Functions provides a connective layer of logic that lets you integrate and extend GCP and third-party services, making it possible to rapidly build serverless applications that are highly available, secure, and cost- effective

#### Nuclio

- Nuclio is an open source and managed serverless platform which allows developers to build and run auto- scaling applications without worrying about managing servers

#### OpenFass
- write functions in any language for Linux or Windows and package in Docker/OCI image format

#### Fn Project 
- The Fn project is an open-source container-native serverless platform that you can run anywhere -- any cloud or on-premise. It’s easy to use, supports every programming language, and is extensible and performant

#### OpenWhisk
- opensource,distributed serverless platform that executes functions (fx) in response to events at any scale