---
layout: post
title:  Chapter 7 - Serverless Implementation consideration
category: Web-Architecture
description: Chapter 7
---

# Serverless, implementation considerations

### Traditional Web Application Vs. Serverless 

![tradion vs serverless](https://i.imgur.com/TZ6FEc8.png)

### What is Considered in  Serverless

-  FaaS
   -  Function as a Service
   -  chunks of code are executed and the short-lived run time instances are formed in response to events like HTTP calls to an API gateway or messages on a message bus or queue 

![AWS Lambda æªæ¡èç](https://d1.awsstatic.com/product-marketing/Lambda/Diagrams/product-page-diagram_Lambda-RealTimeFileProcessing.a59577de4b6471674a540b878b0b684e0249a18c.png)

-  BaaS

   -  Back-end as a Service
   -  Servies that provide functionality such as storage, messaging or authentication that typically scale well. e.g. Azure Cosmos, AWS dynamo DB

   ![Baas](https://i.imgur.com/zCUMrgN.png)

-  Fass Bass Common
   -  Server configuration and capacity management are completely hidden from developers and operators.
   -  Costs are aligned with the use of resources

### Serverless Architecture 

![Serverless Architecture ](https://i.imgur.com/FGpl0rg.png)

**Chanllenges** 

-  Performance and latency
-  Resource limits vs dedicated instances
-  Secruity of infrastructure and service functions
-  Privacy of data and operations
-  Monitoring and debugging is not as straightforward

**Software architecture and development
challenges**

-  Service and function dependencies, orchestration
-  Sercurity, authentication and authorisatinon of distributed invocations
-  Logging and keeping track of service and function performance
-  Debugging and analysing
-  Managing functions and services throughout the lifecycle
-  Communication between teams



## **Serverless software architecture**

### Cloud Application Matrurity

![CloudNative-AppMaturityModel](https://www.nirmata.com/wp-content/uploads/2015/03/CloudNative-AppMaturityModel.png)

| Level | Matrurity       | Criteria                                                     |
| ----- | --------------- | ------------------------------------------------------------ |
| 3     | Cloud Native    | - Transferable across infrastructure providers at runtime and without interruption of service <br>- Automatically scale out/in based on stimuli |
| 2     | Cloud resilient | -State is isolated in a minimum of services<br>-Unaffected by dependent service failure<br>-Infrastructure Agnostic |
| 1     | Cloud Friendly  | -Composed of loosely couled services<br>-Services are discoverable by name<br>-Components are designed to cloud patterns<br>-Compute and storage are separated |
| 0     | Cloud ready     | -Operated on virtualized infrastructure<br>-Instantiateble from image or script |

###  Cloud-Native Stack 

![cloud-native stack](https://www.researchgate.net/profile/Nane_Kratzke/publication/327014262/figure/fig3/AS:659495298531329@1534247340291/Cloud-native-stack-observable-in-a-lot-of-cloud-native-applications.png)

### Always On vs On Demand

-  *Always-on components* are one of the most <u>expensive</u> and <u>avoidable</u> cloud workloads 
-  Even with microservices architecture, there needs to be at least one microservice instance that is always on
   -  one containers instance running for each different micro service type
-  The *function as a service* approach exectue services only when requests take place (trigger activate)

### Blueprint of a serverless platform architecture

![Blueprint of a serverless platform architecture (adapted from [41])Â ](https://www.researchgate.net/profile/Nane_Kratzke/publication/326423781/figure/fig3/AS:649038529576961@1531754252246/Blueprint-of-a-serverless-platform-architecture-adapted-from-41.png)

### Cloud Application Architecture Redesign

![Cloud-based-archi](https://i.imgur.com/oKplKkL.png)

### Serverless promotes event-driven

### ![ãevent-driven serverlessãçåçæå°çµæ](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/serverless/_images/serverless-event-processing.png)

### Hybrid approach to serverless

![Serverless technologies and architectures](https://techbeacon.scdn7.secure.raxcdn.com/sites/default/files/serverless_technologies_and_architectures_image2.jpg)

### Patterns for the Serverless Architecture 

#### Comman Pattern

-  Invoke and control functions and services from a single function
-  Simplify, customise or extend API gateway functionality
-  If a response is required tp the API GW , another function adds latency

![CommonPattern](https://freecontent.manning.com/wp-content/uploads/Sbarski_PiSA_01.png)

>  The command pattern is used to invoke and control functions and services from a single function.



#### Messaging pattern

-    allows developers to build scalable and robust systems by decoupling functions and services from direct dependence on one another

-    allowing storage of events/records/requests in a queue.

  

  ![message-pattern](https://freecontent.manning.com/wp-content/uploads/Sbarski_PiSA_02.png)
>  The messaging pattern, and its many variations, are popular in distributed environments



#### Priority Queue Pattern 

-  Different *priority* on **processing of messages**
-  The system can implement workflows and use different services and APIs to cater for many types of needs and users 

![Priority Queue](https://freecontent.manning.com/wp-content/uploads/Sbarski_PiSA_04.png)

>  The priority queue pattern is an evolution of the messaging pattern.



#### Fan-out Pattern

-  Push messages to all listenrs or necessary functions or services using a queue or a message pipeline

-  Practical when multiple functions are needed to be invoked or as a in between if the function only supports one

   #### 

![fan-out pattern](https://freecontent.manning.com/wp-content/uploads/Sbarski_PiSA_05.png)

>  The fan-out pattern is useful, as many AWS services (such as S3) can’t invoke more than one Lambda function when an event takes place.



### Orchestration of functions 

AWS Steps Functions 

![sfn_how-it-works](https://d1.awsstatic.com/product-marketing/Step%20Functions/sfn_how-it-works.f795601e8338db32506b9abb01e71704f483fc81.png)

## Implementation considerations and concerns

### Security Considerations

-  Everything is managed by your provider
   -  Infrastructure, OS, VM, containerization, library support
-  All functions are entry points
   -  Dependency on external services
-  Privacy
   -  Exectuion patterns, number of requests. etc.

### Code-Related Concern 

-  Vulnerable libraries fetched from Maven and npm repositories and the likes. Functions are stale and static libraries are not auto-updated
   -  There might be nothing that notifies you even of their existence
-  Easy to copy & paste the codes, scripts, or even docket containers that are not or cannot be thoroughly reviewed
-  Permissions - its easier to add too many (and hard ot remove later on without breaking stuff)



### Features of Serveless

-  **Instance have a lifetime** 
   -  when request frequency increases , the instance lifetime tends to become shorter
      -  easier to balance resources for consistent loads
   -  ![Instancehavealifetime](https://jaxenter.com/wp-content/uploads/2018/08/academic3.jpg)

-  **ColdStarts** 
   -  launching a new function instance 
      -  Allocating memory and other resources
      -  Configuration
   -  Instance have a typical lifespan of hours or days
   -  ![ColdStarts](https://jaxenter.com/wp-content/uploads/2018/08/academic2.jpg)
   -  Keep function warm!
      -  Define a watch event to fire every few minutes and trigger your functions
         -  can be parallel to target serveral
      -  In the function, detect if it is a watch and return immediately
      -  Serious improvement in cold start problems among providers
   -  ![keep warm](https://blog.octo.com/wp-content/uploads/2018/08/09_cold_start_keep_warm.jpeg)

### Faas Monitoring

-  you should not include external logging libraries into functions unless necessary
-  Two options
   -  Standard metrics from the cloud environment logs
   -  Custom metrics from the application itself(by instrumenting additional code)
-  What typically given
   -  Duration of a function’s execution time (performance)
   -  Count of function invocations (throghput)
   -  Count of executions resulting in an error (errors)
   -   Count of throttled invocation（壓制） attempts (saturation)
-  Beneficial 
   -  Latency
   -  Requests, repsonse

-  Example:
   -  DataDog
   -  Epsagon
   -  AWS X-ray



### Cost in serverless 

-  DIrect costs
   -  requests : e.g. $0.2 per 1M executions
   -  CPU & RAM e.g. $0.000067 per GB-second
-  Indirect costs 
   -  API Requests :e.g. $3.50 per 1M executions
   -  Networking: e.g. $0.05- 0.09 per GB-out and easily double that
      between datacenter regions
-  Other costs
   -  Code maintainance

![double-billing](https://www.researchgate.net/profile/Nane_Kratzke/publication/327014262/figure/fig6/AS:659495298535432@1534247340548/The-double-spending-problem-resulting-from-the-Serverless-trilemma-42.png)

### Serverless Decide 

-  A specific operation with your application takes considerable computing effort but it is hard predict when.

-  It is triggered by something and does not need to stay always on.

-  When not to go or carefully consider serverless functions

   -  if your application does not already run on any cloud platform 
   -   then it might be better to consider a more thorough migration path. e.g. starting with migarting data stores
   -  going for a specific serverless technology if you are not already on the platform of that provider 

   ### Software development considerations

   -  **Project Size**
      -  Manage resources by ourself? Affordable?
   -  **Costs Estimations**
      -  How to manage storage, computation.
   -  **Teams and team size affects**
      -  Organizations which design systems ... are constrained to produce designs which are copies of the communication structures of these organizations

## DevOps

DevOps is a set of software development practices that combines *software development (Dev)* and *information technology operations (Ops)* to shorten the systems development life cycle while delivering features, fixes, and updates frequently in close alignment with business objectives.

### Serverless supports DevOps

-  Focus on <u>business goals</u> and <u>core value</u> development
-  <u>Agility</u>(敏捷) through <u>instant decision</u> and continuous improvement 
-  <u>Lower development costs</u> 
-  <u>Continuous deployment</u> allows perfecting the code without the hassle of the infrastructure and scalng
-  Freedom of technolgoies
-  Scaling and availablity , <u>lower administration overhead</u>
-  Ops teams are dissolved into developemnt Team
   -  any operations engineers’ responsibilities may shift deeper into the application stack
   -  monitoring and optimissation still needs to be done



### Programming Model and DevOps Challenges

#### Tools

-  Traditional tools that assume access to servers <u>to be able to monitor and debug applications</u> are **NOT applicable in serverless architectures**, and new approaches are needed.

#### Deployment
- Developers should be able to use <u>declarative approaches</u> to control what is deployed and tools to support it.

#### Monitoring and Debugging

-  As serverless functions are <u>running for shorter amounts of time,</u> there will be many orders of magnitude more of them running making it harder to identify problems and bottlenecks
-  When the functions finish , the only trace of their execution is <u>what the serverless platform’s monitoring infrastructure</u> recorded.

#### IDEs

-  Higher level developer capabilities, such as <u>refactoring functions</u> (e.g., splitting and merging functions) and r<u>everting to an older version</u>, etc. will be needed and <u>should be fully integrated with serverless platforms</u>.

#### Composability
- This includes being able to <u>call one function from another, creating functions that call and coordinate a number of other functions,</u> and higher level constructs such as parallel executions and graphs.
- Tools will be needed to <u>facilitate creation of compositions</u> and their maintenance.

#### Concurrency

-  Expressing concurrency semantics, such as atomicity (function executions need to be <u>serialized</u>), etc.

#### Recovery semantics

- Such as exactly once, at most once, and at least once semantics.

#### Code granularity
- ![granularity](https://sites.educ.ualberta.ca/staff/olenka.bilash/Best%20of%20Bilash/Images/granularity.gif)
- Currently, serverless platforms encapsulate code at the granularity of functions. It is an open question whether coarser（粗糙） or finer（細密） grained modules would be useful.

#### Long Running 

-  Currently, serverless functions are often limited in their execution time.
-  There are scenarios that require long running (if intermittent) logic.
-  Programming models and tools may decompose long running tasks into smaller units and provide necessary context to track them as one long running unit of work

#### State 
- Real applications often require state, and it is not clear how to manage state in stateless serverless functions
- programing models, tools, and libraries will need to provide the necessary.

### DevOps 2

-  Stack fully defined with code/text
   -  infrastructure can then be modified and re-deployed to systematically test hypotheses 
   -  automatic evaluation of any newly deployed architecture (e.g. flows) 
-  Constant iteration
-  However serverless architectures, most tools focus on the individual function 

- ![DevOps 2.0 Cycle LaunchDarkly Business Ops QA Dev Marketing Sales Business](http://blog.launchdarkly.com/wp-content/uploads/2016/05/DevOps2_Cycle.jpg)

-  An <u>automatic visualisation</u> of the <u>current run-time</u> architecture helps spot small differences 
-  <u>Invocation count and runtime of functions</u> can identify bottlenecks 
-  Assess <u>entire data flows</u> and interplay for top-down improvement (and prioritization) 



#### DevOps CI/CD (For OepnFaaS)

-  **持續整合(Continuous Integration, CI)**、**持續部署inuous Delivery, CD)**、**持續交付(Continuous Deployment, CD)**，
-  ![CI/CD process](https://alln-extcloud-storage.cisco.com/ciscoblogs/5b15739d2cf71.png)

-  Builds function images
-  Createa a tempory Swarm Environment
-  runs tests for the functons
-  releases the images to a registry if the tests pass
-  deploys the functions if the tests pass

-  Replicate conditions on your serverless cloud provider in the development and test environmetns
-  Test and production environment can be the same! 



### Some to Consider

#### Some Chanllenges

-  Understanding the flow of data and invocations
-  Maintaining interoperable semantics during development
-  Compatibility between different service versions

#### Some FaaS Function Registry requirements

-  Name, version, input/output
-  Dependencies on other functions and platform components, libraries and other shared codebase
-  Developers, teams and other responsibles