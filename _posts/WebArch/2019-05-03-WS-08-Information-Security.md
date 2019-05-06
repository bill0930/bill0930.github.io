---
layout: post
title:  Chapter 8 - Information Security
category: Web-Architecture
description: Chapter 8
---

#  **Information security** 

### Information Security 

-  Class model for information Security 

![ãinformation Securityãçåçæå°çµæ](https://kirkpatrickprice.com/wp-content/uploads/2017/10/KP_BlogPost_28_700x500.png)

-  Confidentiality （機密性）
-  Integrity（完整性）
-  Availablity（可用性）

#### Confidentiality

-  refers to protecting information from being accessed by unauthorized parties.
- In other words, only the people who are authorized to do so can gain access to sensitive data.



#### Integraity 

-  refers to ensuring the authenticity of information
-  that information is not altered, and that the source of the information is genuine（not fake/modified）.



#### Availability 

-  that information is accessible by authorized users



### Information Security of Web App

-  Protected data stored e.g. encryption or restricted access to storage
-  Protect communication 
   -  between client and server e.g. TLS
   -  between distributed components TLS
-  How to ensure who sends or requests data
   -  Identify each application with *authentication*, e.g. user name and password
   -  *Certificates or tokens* etc. to sign that data comes from a certain party (and that is hasn’t been altered on the way)



### Application software architecture considerations

-  Distributed software components and services
   -  own backend or distributed services around the Internet ?
   -  Can you rely on the "local" network e.g. docker environment?
-  Intermediary components such as a message bus, Can you trust that only authorized parties access that service?  i.e.  messages received are from who they are

### Web application security in general

-  **Keep an inventory of your web applications**
   -  need to know which applications are being used
   -  Who is using them and for what purpose
   -  Who is responsible for maintaining, are their dependencies know
-  **Proritize your applications**
   -  E.g. critical, normal, less important
   -  <u>Based on sensitive information</u> they contain or their criticality to operations
-  **Prioritize vulnerabilities** 
   -  Many applications have several vulnerabilities, prioritize which to eliminate

![Infected Websites Platform Distribution](https://blog.sucuri.net/wp-content/uploads/2019/03/19-sucuri-2018-hacked-report-infected-website-platform-650x408.png)



### How to prepare for vulunerabilities 

-  Use least permissive application privileges possible
-  Have protection in place, e.g. using firewalls
-  bounty program（bug賞金獵人）
-  Continuous monitoring of application instances  and suspicious activity
   -  Identifed vulnerabilities in applications and libraries used



#### Tools and security technology 

-  Black box testing tools such as *web scanners* and *penertration testing software*
   -  Dynamic Application Security Testing (DAST) tools to automatically test cross-site scripting, SQL
      injection etc. generic vulnerabilities with miminum effort
-  White box testing tools such as *static code analyzers*
   -  More specialized towards certain frameworks and libraries

-  Web application firewall (WAF)
   -  Application level rules, e.g. detecting and filtering of certain types of HTTP requests
   -  Can also analyze response information to be returned



### Qos

-  Quality of Service
   -  ***Availability*** of the applications and systems
   -   ***Performance*** of the applications and system

-   Mechanisms to achieve
   -  Over-provisioning (e.g. sufficient resources always available)
      -  Dynamic provisioning (e.g. clouds)
-  Prioritation
   -  Planning (in advance )

### SLA 

-  Service Level Agreement (SLA) 
-  defines the engagements between a provider and a consumer of a service
   -  The provider can be, for examle, a hosting provider, telecommunications service provider or SaaS provider.
   -  The consumers are those whose experience is affected by the SLA.
-  defines the QoS  and expresses itself typically in *percentages* or concrete amounts of contractual objectives.
-   For example, a 99.5% of the time availability. A 7 minutes downtime during a week or on a daily, monthly or yearly level?



### Data and semantics for interoperable systems

 - Interoperability 
    - means using compatible means of communication as well as messages understood by all parties
    -  Using JSON or XML does not imply interoperability, it is only the encoding
    -  different protocols as well as means for discovery, binding and configuration can provide interoperability for applications compositions

![interoperable](http://www.isko.org/cyclo/interoperability1.jpg)

-  Service composition compatibility

![web-service](https://ai2-s2-public.s3.amazonaws.com/figures/2017-08-08/edc52a68e7f2e2a8d7e4ae41b6c68098566e8996/14-Figure1-1.png)