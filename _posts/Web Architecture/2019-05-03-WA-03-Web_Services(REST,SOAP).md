---
layout: post
title:  Chapter 3 - Web Services
category: Web-Architecture
description: Chapter 2
---
# Web Services 

### Definition:
- A Web Serbice provides functionality to its consumer applications 
- through an interface independent of its underlying operating system, programming language or implementation technology
   - acessible over the internet
   - Reusable, funtional service, component
   - Agreed message structures (Json,XML)
- Client Server Based
   - request-response communication



### Service-Oriented Architeture

-  Ideally, Services are discovered and bound at run-time in a dynamical manner
-  The provider is lsited somewhere, e.g., in a broker, from which the requester can find it

![Service-Oriented Architecture](https://www.w3.org/2003/Talks/0521-hh-wsa/soa.png)



### SOAP Web Service

-  **Simple Object Access Protocal**
-  XML based protocol for accessing Web Service 
-  defines how a XML document message is communicated between two Web Services in an Internet context
-  Consists of 
   -  envelope 
   -  header 
   -  body

![Diagram of SOAPMessage Object with SOAPPart, SOAPEnvelope, SOAPHeader, and SOAPBody](https://docs.oracle.com/cd/E19575-01/819-3669/images/saaj-noAttach.gif)

### WSDL

-  stand for **Web Services Description Language** 
-  describe how to access a web service and what operations it will perform
-  WSDL is a language for describing how to interface with XML-based services.
-  Three major elemens
   -  Types
   -  Operations
   -  Binding

```xml
<definitions name = "HelloService"
   targetNamespace = "http://www.examples.com/wsdl/HelloService.wsdl"
   xmlns = "http://schemas.xmlsoap.org/wsdl/"
   xmlns:soap = "http://schemas.xmlsoap.org/wsdl/soap/"
   xmlns:tns = "http://www.examples.com/wsdl/HelloService.wsdl"
   xmlns:xsd = "http://www.w3.org/2001/XMLSchema">
 
   <message name = "SayHelloRequest">
      <part name = "firstName" type = "xsd:string"/>
   </message>
	
   <message name = "SayHelloResponse">
      <part name = "greeting" type = "xsd:string"/>
   </message>

   <portType name = "Hello_PortType">
      <operation name = "sayHello">
         <input message = "tns:SayHelloRequest"/>
         <output message = "tns:SayHelloResponse"/>
      </operation>
   </portType>

   <binding name = "Hello_Binding" type = "tns:Hello_PortType">
      <soap:binding style = "rpc"
         transport = "http://schemas.xmlsoap.org/soap/http"/>
      <operation name = "sayHello">
         <soap:operation soapAction = "sayHello"/>
         <input>
            <soap:body
               encodingStyle = "http://schemas.xmlsoap.org/soap/encoding/"
               namespace = "urn:examples:helloservice"
               use = "encoded"/>
         </input>
		
         <output>
            <soap:body
               encodingStyle = "http://schemas.xmlsoap.org/soap/encoding/"
               namespace = "urn:examples:helloservice"
               use = "encoded"/>
         </output>
      </operation>
   </binding>

   <service name = "Hello_Service">
      <documentation>WSDL File for HelloService</documentation>
      <port binding = "tns:Hello_Binding" name = "Hello_Port">
         <soap:address
            location = "http://www.examples.com/SayHello/" />
      </port>
   </service>
</definitions>
```

-  **Definitions** − HelloService
-  **Type** − Using built-in data types and they are defined in XMLSchema.
-  **Message** −
   -  sayHelloRequest − firstName parameter
   -  sayHelloresponse − greeting return value
-  **Port Type** − sayHello operation that consists of a request and a response service.
-  **Binding** − Direction to use the SOAP HTTP transport protocol.
-  **Service** − Service available at http://www.examples.com/SayHello/
-  **Port** − Associates the binding with the URI http://www.examples.com/SayHello/ where the running service can be accessed.



### HTTP CRUD

- POST,GET,PUT, DELETE

-  The methods are separate from the resource (indicated by URI)
   -  Uniform Resource Identifier
      -  e.g. *http://www.cisco.com/en/US/partners/index.html* 
         -  protocol : htto
         -  Domain name: www.cisco.com
         -  path: /en/US/partners/index.html
   -  Different Language Version
   -  Alternatively content negotiation, one URI but client application requests certain kind of content 
      -  e.g. HTTP Header-Type: application/xml OR application/json
-  As With SOAP Web Services, direct HTTP calls are not made by clients but supporting libraries are used 
-  No direct replacement for WSDL , no that big of need as with SOAP Web Serbies
   -  WADL(Web Application Description Language)
   -  OpenAPI Specification (Swagger)

| HTTP Verb | CRUD           | Entire Collection (e.g. /customers)                          | Specific Item (e.g. /customers/{id})                         |
| :-------- | :------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| POST      | Create         | 201 (Created), 'Location' header with link to /customers/{id} containing new ID. | 404 (Not Found), 409 (Conflict) if resource already exists.. |
| GET       | Read           | 200 (OK), list of customers. Use pagination, sorting and filtering to navigate big lists. | 200 (OK), single customer. 404 (Not Found), if ID not found or invalid. |
| PUT       | Update/Replace | 405 (Method Not Allowed), unless you want to update/replace every resource in the entire collection. | 200 (OK) or 204 (No Content). 404 (Not Found), if ID not found or invalid. |
| PATCH     | Update/Modify  | 405 (Method Not Allowed), unless you want to modify the collection itself. | 200 (OK) or 204 (No Content). 404 (Not Found), if ID not found or invalid. |
| DELETE    | Delete         | 405 (Method Not Allowed), unless you want to delete the whole collection—not often desirable. | 200 (OK). 404 (Not Found), if ID not found or invalid.       |

### OpenAPI Specification / Swagger

JSON description of resources, allowed operations, parameters, expected return values, etc/



### SOAP VS REST 

-  SOAP
   -  methods described in the interface agreement (WSDL)(Web Services Description Language)
   -  Message structures described in the interface description(WSDL, XML)
   -  Complex additional specification (information security, transaction, eventing)
-  RESTful web services using hTTP
   -  No explicit interface description but(WADL, WSDL2.0, SWAGGER)
   -  Basic methods readily avalible 
   -  Resource centric, no specific format(XML/JSON)
   -  Resources need to be defined
   -  Lighter and less stricty defined compared to SOAP based
   -  They typical modern way

|                      | SOAP                                                         | REST                                                         |
| -------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Meaning              | Simple Object Access Protocol                                | Representational State Transfer                              |
| **Design**           | **Standardized protocol with pre-defined rules to follow.**  | **Architectural style with loose guidelines and recommendations.** |
| Approach             | Function-driven (data available as services, e.g.: “getUser”) | Data-driven (data available as resources, e.g. “user”).      |
| **Statefulness**     | **Stateless by default, but it’s possible to make a SOAP API stateful.** | **Stateless (no server-side sessions).**                     |
| Caching              | API calls cannot be cached.                                  | API calls can be cached.                                     |
| **Security**         | **WS-Security with SSL support. Built-in ACID compliance.**  | **Supports HTTPS and SSL.**                                  |
| Performance          | Requires more bandwidth and computing power.                 | Requires fewer resources.                                    |
| **Message format**   | **Only XML.**                                                | **Plain text, HTML, XML, JSON, YAML, and others.**           |
| Transfer protocol(s) | HTTP, SMTP, UDP, and others.                                 | Only HTTP                                                    |
| **Recommended for**  | **Enterprise apps, high-security apps, distributed environment, financial services, payment gateways, telecommunication services.** | **Public APIs for web services, mobile services, social networks.** |
| Advantages           | High security, standardized, extensibility.                  | Scalability, better performance, browser-friendliness, flexibility. |
| **Disadvantages**    | **Poorer performance, more complexity, less flexibility.**   | **Less security, not suitable for distributed environments.** |

### Implementing Service

-  *Services* are made up of *components*
   -  *components* made up of objects
   -  possibility to reuse code
   -  Implementation technologies can vary
-  *Service layer* functionality 
   -  Run on server that routes requests to the application logic
   -  Include some kind of server features,

### Composition of Services

-  Services can act as 
   -  composite controller (Composing other services)
   -  composite member
   -  or in both both
-  All services are not necessarily related to processing service consumer output
   -  e.g. post-processing or logging

![File:WSC.png](http://thinc.cs.uga.edu/thinclabwiki/images/d/d9/WSC.png)

### Service Layers

-  One simple division 
   -  *Orchestration layer* 
      -  implementing value adding business processes
   -  *Business Service* *layer*
      -   containing application logic, tasks and resources
   -  *Application Service layer*
      -  Connecting implementing components and application systems


### Orchestration VS Choreography

![Orchestration](https://i.stack.imgur.com/hUbdsm.png)
- Central Coordinator
- Coordinator decides all actions and their order


![Choreography](https://i.stack.imgur.com/e186jm.png)
- No central coordinator
- Predefined rules of engagement and collaboration

### SOA patterns

#### Service Facade

   -  ![A diagram showing the behavior of the pattern. Applications send service requests to the broker, which fulfills these requests by using functionality which does not provide a service interface.](https://www.ibm.com/support/knowledgecenter/pt-br/SSMKHH_9.0.0/com.ibm.etools.mft.pattern.sen.doc/sen/sf/facade.gif)
   -  **Problem**
      -  The *coupling* of the *core service* to *contracts* and *implementation resources* can 
         -  i*nhibit(抑制) its evlolution*
         -  *negatively impact service consumer*
   -  **Solution**
      -  A *separate facade components* is incorporated into the service design 
   -  **Impacts**
      -  The addition of the facade component 
         -  introduces design effort 
         -  performance overhead


#### **Redudant Implementation**

-  ![Redundant Implementation: Having redundant implementations of agnostic services provides fail-over protection should any one implementation go down.](https://patterns.arcitura.com/wp-content/uploads/2018/09/fig1-88.png)

-  **Problem**
   -  A *service* that is being **actively reused** introduces a potential single point of failure that may **jeopardize the realiablity of all composition in which it participaties** if an unexpected error condition occurs(重用的服務會可能導致all composition穩定)
-  **Solution**
   -  Resusable Service can be deployed via r*edundant Implementation* or with failover support
-  **Application**
   -  The same service implementation is **redundantly deployed** or supported by infrastructure with redundancy features
-  **Impacts**
   -  Extra governance effort is required to keep all redundant implementation in synch.



#### Service Data Replication

-  ![Service Data Replication: By providing each service its own replicated database, autonomy is increased and the strain on the shared central database is also reduced.](https://patterns.arcitura.com/wp-content/uploads/2018/09/fig1-94.png)


-  **Problems**
  
   -  *Service logic* can be deployed in isolation to increase service autonomy, but services continue to *lose autonomy* when requiring access to *shared data sources*.
   
-  **Solution**
  
-  Services can have their own dedicated databases with replication to shared data sources.
  
-  **Application** 

   -  An *additional database* needs to be provided for the service and one or more replication channels need to be enabled between it and the *shared data sources*

- **Impacts**

  -  This pattern results in *additional infrastructure cost and demands*, and an *excess of replication* channels can be difficult to manage.

   
  
   



#### Partial State Defferal

-  ![Partial State Deferral](https://patterns.arcitura.com/wp-content/uploads/2018/09/fig1-81.png)

-  **Problems**
   -  Service capabilities may be required to store and manage large amounts of *state data*, resulting in **increased memory consumption** and **reduced scalability**.
-  **Solution**
   -  Even when services are required to remain stateful, a subset of their state data can be temporarily deferred.
-  **Application**
   -  Various state management deferral options exist, depending on the surrounding architecture.
-  **Impacts**
   -  Partial state management deferral can add to *design complexity* and bind a service to the architecture.

#### Partial Validation 

-  ![Partial Validation](https://patterns.arcitura.com/wp-content/uploads/2018/09/fig1-82.png)
-  **Problems**
   -  The generic capabilities provided by agnostic （跨平台）services sometimes result in service contracts that *impose unnecessary data* and *validation* upon consumer programs.
-  **Solution**
   -  A consumer program can be designed to *only validate the relevant subset of the data and ignore the remainder*.

-  **Impacts**
   -  Extra design-time effort is required 
   -   the additional runtime data filtering-related logic can reduce the processing gains of avoiding unnecessary validation.

#### UI Meditator (UI調解)

-  ![UI Mediator: The mediator service](https://patterns.arcitura.com/wp-content/uploads/2018/09/fig1-110.png)

-  **Problems**
   -  Because the behavior of individual services can vary depending on their design, runtime usage, and the workload required to carry out a given capability
   -   the consistency with which a service-oriented solution can respond to requests originating from a user-interface can fluctuate, leading to a poor user experience.
-  **Solution**
   -  Establish mediator logic solely responsible for ensuring timely interaction and feedback with user-interfaces and presentation logic.
-  **Application** 
   -  The mediator logic establishes an additional layer of processing that can dd to the required runtime processing

### Microservices Architecture

-  An approach to developing a single application as *a suite of small services*, each running in its own process and communicating with lightweight mechanisms, ofeten an HTTP resources API

![img](https://microservices.io/i/Microservice_Architecture.png)

### Run only on demand 

![Run-only-one-demand](https://i.imgur.com/r5UCCpY.png)



### Monlithic Services

-  microservices and
   functions
-  ![monilihic](https://docs.microsoft.com/en-us/azure/service-fabric/media/service-fabric-overview-microservices/monolithic-vs-micro.png)

-  typically buit on top of complex frameworks
-  Technologies ar defined by base components
-  Often a lot of shared code even with independently deployable pieces
-  More susceptible to system-wide failures
-  Scaling involves updating or replicating the whole stack