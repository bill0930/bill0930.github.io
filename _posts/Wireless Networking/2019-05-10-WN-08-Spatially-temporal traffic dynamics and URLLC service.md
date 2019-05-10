---
layout: post
title: Chapter 8 - Spatially-temporal traffic dynamics and URLLC service  
category: Wireless Networking
description: URLLC 
---



# Spatially-temporal traffic dynamics and URLLC service 	

## General 

### Service Requirement 

#### 3GPP 5G Service

-  mMTC (massic Machine-Type Communication) 夠大

   -  Long Distance (link budge 164dB)
   -  Power efficiency (10+ years battery lifetime)
   -  Extremely dense (1+million devices/km<sup>2</sup>)
-  eMBB (enhanced Mobile Broadband) 夠寬

   -  Packet cell rate at 10Gbps

   -  Latency at air interface ~10ms
-  URLLC (Ultra Reliable Low Latency Communications) （夠低）
   - Air interface latency <1ms 
   - Prbability of devliery 0.9999999 

#### 5G NR Services

-  New bandwidth-greedy services
   -  VR,AR
   -  High-rate video application (FHD+)
-  High-end IoT application
   -  Inter-robot communication
   -  V2V communcation, V stands for Vehicle
   -  inter-UAV communications
      -  *unmanned aerial vehicle* (*UAV*)

## Servicing Spatially-temporal traffic

### Traffic Anaysis

![Spatio-temporal analysis](https://i.imgur.com/njBUdeS.png)

-  Different time of day

### Solution

-  Locailzation(off-loading ) using D2D(devices)
   -  A fraction of traffic can be localized
   -  Offloading onto direct links
-  On-demand service provisioning 
   -  Mobile access points
   -  "Cell on whieels" (CoW), UAV
      -  COW: portable mobile cellular site that provides temporary network and wireless coverage to locations where cellular coverage is minimal or compromised. 

### Traffic Localization (off-loading)

#### D2D Technologies

-  Wifi-direct, LTE-sidelink
-  3GPP plans to add NR-direct

-  Limitation
   -  Limited communication range
   -  Still limited support

#### D2D meshs

-  interference in adhoc network   
-  relaying a mesh

#### Blockchain 

![Blockchain](https://www.ibm.com/developerworks/community/blogs/73a1b0b2-6fe9-4c40-84b5-16c3212a7216/resource/BLOGS_UPLOADED_IMAGES/0_QAupL2jK-bAl9Gt7.jpg)



![COVERAGE](https://www.researchgate.net/profile/Zheng_Yan4/publication/308806942/figure/fig1/AS:472192451387394@1489590861618/D2D-communication-application-scenarios-and-use-cases.png)

### Mobile AP 

#### 3GPP Supoort 

-  UAV support in 3GPP
-  NR relaying/sidelink
-  Backhauling

#### Performance 

-  Backhaul is critial 
-  Dynamic optimization is critical 
-  Interplay between no. of UEs and no. of UAVs



## URLLC Service

### High-end IoT application 

-  Driven by new use-cases
-  Driven by elecronic evolution

### Industrial Automation

-  Autonomous production lines
-  Traffic characteristics 
   -  Low latency (few ms)
   -  High reliability (10<sup>-5</sup> BLER) (Block Error Rate)

![Industry 4.0](https://www.analog.com/-/media/analog/en/applications%20by%20market/iat/pavilion/industry-40-infographic-v5.gif?la=en)



#### Autonmous Driving

-  Future of car industry
-  Traffic characteristics
   -  Huge throughput
   -  Low latency

![The Future of Autonomous Vehicles and Kettering University](https://d1v86arogvust7.cloudfront.net/sites/default/files/styles/blogfeature_large/public/field/image/shutterstock_682503085.jpg?itok=f0QybLHo)



#### Healthcare : Remote surgeries

-  Traffic characteristics 
   -  Extremely Low latency (<1ms)
   -  Extremely High reliability (10<sup>-9</sup>)

#### Remote Diagnosis

-  NR+LTE

![img](http://www.masmachinetools.com/foto/dalkova-diagnostika-mcu-700.jpg)

### Addressing Latency

-  Main chanllenge
   -  NR frame duration : 1ms
   -  Latency <1ms
   -  How to conform?
-  Two principle ways
   -  Reservation/priorities
   -  **Non-Orthogonal multiple access (NOMA)**
      -  International overlapping of data
      -  Enable by flexible NR slot numberology

### Addressing Reliability

-  Bloackage may or may not lead to outage(中斷)
   -  Case 1: blockage leads to lower MSC scheme
      -  MSC: Mobile Switching Service Centre
   -  Case 2: bloackage leads to outage
-  Solution
   -  Case 1: provide more resources
      -  Bandwidth reservation
      -  Isolated deployments
   -  Case 2: find a new path
      -  3GPP multi-connectivity
      -  Dense deployments
-  Multi-connectivity 
   -  avoiding outage!
-  Bandwidth reservation
   -  Alleviating lower MCSs(Modulation and Coding Scheme)


