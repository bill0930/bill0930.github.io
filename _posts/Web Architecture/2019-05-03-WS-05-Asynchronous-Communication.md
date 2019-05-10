---
layout: post
title:  Chapter 5 - Asynchronous Communication
category: Web-Architecture
description: Chapter 5
---

# Asynchronous communication, Web Sockets, MQTT

### Synchronous communication

Example of synchronous communication

-  A user clicks a button on a webpage
-  The browser makes a HTTP request to the server
-  The browser waits until the server repsonds and renders and renders the output on the reponse 



JavaScript brings asynchronous nature to the UI. exmaple

-  A user clicks a button on a web page. This is intercepted by the JS layer. 
-  The JS layer makes a HTTP request to the server and binds an event handler to execute *when the response arrives*. Other activities can continue meanwhile. 
-  When the server responds, the event handler code is executed 

![synchronous communication vs asynchronous communicationãçåçæå°çµæ](https://www.webopedia.com/FIG/ASYNC.gif)

### Asynchronous Communication

-  Asycnronous commuicnation is often neccessary on the web
   -  HTTP requests have a time limit
   -  Activities may actually take long(e.g hours)
   -  We do not have control of the other end or its load
-  Three common ways to implement asynchronous communication using HTTP 
   -  **Polling**
      -  Sending requets at a consistent rate and server returns updates accordingly
   -  **Long-polling**
      -  the client sends a request which is immediately responded ,followed by another request for which the server returns a response when something new is available
   -  **Push**
      -  after  a request is being sent, the repsonse by the server kept open.

![img](https://cdn-images-1.medium.com/max/1600/1*zG7Jyeq02JRAN6Wz6gs15g.png)

### Web Socket 

-  HTTP is not a bi-directonal protocol
-  Web Sockets provdes full-duplex communication channel over a single TCP connection
   -  Allows interaction between a web browser or any other client application and the web server with *lower overhead*
   -  No need to make requests, each party can send content and pass messages back and forth
   -  Designed for standard ports 80 and 443 to be usable with firewall

Client request:

```http
GET / HTTP/1.1
Upgrade: websocket
Connection: Upgrade
Host: example.com
Origin: http://example.com
Sec-WebSocket-Key: sN9cRrP/n9NdMgdcy2VJFQ==
Sec-WebSocket-Version: 13
```

Server Respose:

```http
HTTP/1.1 101 Switching Protocols
Upgrade: websocket
Connection: Upgrade
Sec-WebSocket-Accept: fFBooB7FAkLlXgRSz0BT3v4hq5s=
Sec-WebSocket-Location: ws://example.com/
```

### Message Brokers

![img](https://cdn-images-1.medium.com/max/800/1*Op257GVcx9ybQuaxlUOp_Q.png)

-  can act as an intermediary between two communicating parties
-  Asynchronous by nature
-  Pattern
   -  Streams/queues
   -  Publish-subscribe
-  Many support HTTP, REST,SOAP or any other means for client/application components to connect

### MQTT(OASIS)

-  **Message Queuing Telemetry Transport**

-  Lightweight IoT or M2M protocol

-  Based on publish/subscibe communication pattern

   -  event-driven and enbales messages to be pushed to clients

-  Message exchanged based on topics

   -  my house/bedroom2/temperature
   -  house/+/temperature
   -  house/#

-  JSON/XML or whatever content

   ![MQTT](https://i.imgur.com/P4nPGTg.png)

#### MQTT messages and QoS

-  Messages

   -  Connect
   -  Disconnet
   -  Publich(TopicName, QoS, RetainFlag, Payload, Packet identifier, ...)
   -  Subscribe/SubAck
   -  Unsubscrible /UnsubAck

-  Each connection has QoS measure 

   -  at most once (QoS 0)

      -  the message is sent once and the client and broker take no additional steps to acknowledge delivery **(fire and forget)** 
-  At least once (QoS1) 
  
   -   the sender re-sends the message multiple times until acknowledgement is received **(acknowledged delivery)**
   - Exactly once (QoS2)
     -  the sender and receiver engage in a handshake to ensure only one copy of the message is received (Assured Delivery)

### AMQP

-  **Adanced Message Queuing Protocol** is an open standard protocol for *message oriented middleware*

-  -  *Message Oriented Middleware* is a concept that involves the passing of data between applications <u>using a communication channel</u> that carries self-contained units of information (messages).
-  AMQP was designed to efficiently support a wide variety of messaging applications and communication patterns.
-  Typically AMQP is used as a message broker and it has <u>much more complex</u> and <u>versatile</u> communication patterns than, for example, MQTT

-  Two versions currently
   -  Pre 1.0 (e.g. 0-9-1 RabbitMQ, ...)
   -  1.0 (ISO/IEC 19464) (fewer implementations, more complex) 
-  Can be <u>scaled and chained using multiple message broker</u> instances for extreme scalability (fairly easy above 1M+ message per second)

![AMQP - Advanced Message Queuing Protocol](https://www.cloudamqp.com/img/docs/camqp.png)

#### Exchange 

-  *Exchanges* are AMQP 0-9-1 entities where messages are sent
-  Exchanges take a message and route it into zero or more queues.
-  The routing algorithm used depends on the *exchange type* and rules called *bindings*

| Name             | Default pre-declared names              |
| :--------------- | :-------------------------------------- |
| Direct exchange  | (Empty string) and amq.direct           |
| Fanout exchange  | amq.fanout                              |
| Topic exchange   | amq.topic                               |
| Headers exchange | amq.match (and amq.headers in RabbitMQ) |

| Illustration of the                                          |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| ![exchange delivering messages to  queues based on routing key](https://www.rabbitmq.com/img/tutorials/intro/exchange-direct.png) | It has one special property that makes it very useful for simple applications: every queue that is created is automatically bound to it with a routing key which is the same as the queue name. |
| ![exchange delivering messages to three queues](https://www.rabbitmq.com/img/tutorials/intro/exchange-fanout.png) | A fanout exchange routes messages to all of the queues that are bound to it and the routing key is ignored. Fanout exchanges are ideal for the broadcast routing of messages. |



### DDS - Data Distribution Service

-  A real-time <u>machine to machine communication standard</u> aiming to enable <u>data exchange in a publish-subscribe pattern</u> to be 
   -  scalable
   -  real-time
   -  dependable 
   -  high-performance
   -  interoperable
-  Intended application areas includes
   -  Air-traffic control
   -  Smart-grid management
   -  Autonomous vehicles
   -  Robotics
   -  Transportation systems
   -  Aerospace
-  Characteristics
   -  Empahasis on *QoS parameters* and configuration up-front
   -  Anonymous transmission of messages
   -  Automatic failover and handling of-redundant information sources

![DDS](https://upload.wikimedia.org/wikipedia/commons/c/c2/Notional_OMG_DDS_Interoperability.jpg)

### OPC  UA 

![OPC-UA](https://www.br-automation.com/fileadmin/1455730630443-de-html-1.4.jpg)

-  Communication Standard originally designed for industrial automation and control purposes but nowadays has application in many other application areas as well

-  Designed to unify communication and facilitate integration of components from different vendors

   

**OPC UA Publish/Subscribe** **(2018)**

-  Message Bus based publish/subscribe communication
   -  Enables using the OPC UA information model in other means of  communication and standard exchange such as MQTT and AMQP