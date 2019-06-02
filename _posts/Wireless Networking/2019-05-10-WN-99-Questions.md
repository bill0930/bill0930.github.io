---
layout: post
title:  Chapter 99 - Question Revision
category: Wireless Networking
description: for revision some main point
---




### Spread Spectrum

-  Spread-spectrum is designed to trade bandwidth efficiency for reliability, integrity, and security
-  **FHSS**
   -  Frequency Hopping Spread Spectrum
   -  Spectrum is divided into many subchannels 
   -  two communicating systems hop on same frequency
-  **DSSS**
   -  Direct Sequence spread spectrum
      -  stations are assigned orthogonal codes
      -  use these code for transmission
      -  other stations transmissions appears an noise

![fhss-dsss](https://i.imgur.com/UbF8Pr0.png)

### ARQ 

-  Automatic Repeat reQuest
-  **Reactive** protocol
-  **control protocols** for transmission of data over noisy or unreliable communication network.
-  Use **ACK** and **timeouts** to acheive reliable data transmission
-  Stop-and-wait ARQ, Go-Back-N ARQ



### Aloha VS slotted Aloha

-  **Aloha** 
   -  a terminal transmits whenever the user data is ready
   -  if the sender finds that the packet get collided
      -  it **waits for a random period of time** 
      -  send the packet again
   -  Throughput : $S_{pure} = Ge^{-2G}$
-  **Slot-Aloha**
   -  time is slotted
   -  length on the slot is the time to transmit a packet
   -  node starts transmission in the beginning of the slots only
   -  if collision occurs
      -  sender **waits for a random number of slots**
      -  transmit Packets agains
   -  Throughput:  $S_{slotted} = Ge^{-G}$

![Throughput vs. Traffic Load of Pure Aloha and Slotted Aloha.](https://upload.wikimedia.org/wikipedia/commons/thumb/a/a5/Aloha_PureVsSlotted.svg/1024px-Aloha_PureVsSlotted.svg.png)

 

### Why does IEEE standardize only two lower layers for WLANs

-  only standardize PHY and MAC lyaer
-  Interfaces to higher layer is the same as those in iEEE 80.2x standards
-  The upper layers is still the same as normal LAN
-  what the different is the medium for tranmission , it is in wireless now. 



### BEB works in IEEE 802.11 WLAN.

-  Binary Exponential Backoff
-  When multiple entities attempt to gain access to a shared resource, only one of them will succeed. 
-  Those who fail wait til the resoure becomes available then retry.
-  **Binary Exponential Backoff (BEB)** is an algorithm to determine how long entities should backoff before they retry. 
-  With every unsuccessful attempt, the **maximum backoff interval is doubled**.
-  BEB **prevents congestion** and **reduces the probability** of entities **requesting access at the same time**,

### Why RTS-CTS needed

​	- to solve hidden terminal problem

![é±èç¯é»](https://pic.pimg.tw/oilcut123/1393228354-2638627403.png)

-  **hidden terminal problem** occurs when a node can communicate with a wireless access point (AP), but cannot directly communicate with other nodes that are communicating with that AP.

-  **RTS-CTS**
   -  the senders A sends RTS to receiver B
   -  once the receiver B get RTS, it starts to send CTS to all other terminals, indicating that sender A is going to communicate with receiver B. After the this handshake, they can start send data.

### Network allocation vector

-  **Shared Medium Access**
   -  **Carrier Sensing**
      -  **Virtual Carrier Sensing** 
         -  provided by the <u>Network Allocation Vector (NAV)</u>
         -  NAV Indicates <u>how long the medium is reserved</u>
         -  NAV is set **acccrdoing to fields (Duration ) indicated in most frames**
-  It is a virtual carrier sensing mechanism. 
-  The station listens to *duration* field to set their NAV
-  It is a indicator for a station on how long it must defer from accessing the medium



### ESS and Infrastruture BSS difference

**Basic Service Set (BSS)** : a set of stations communicating with each other

**Extended Service Set (ESS)**: linking BSS using backbone network

​	

 **Infrastructure BSS (Infracstruture mode)**

-  Terminals communicate via  AP 
-  centralized

![ãInfrastructure BSSãçåçæå°çµæ](http://4.bp.blogspot.com/_mx1N_ZN8DgU/Sm6wcnWhGGI/AAAAAAAAAWs/5OslarklpWs/s400/2.jpg)

**Extended Service Set (ESS)**:

-  provide larger service areas
-  does not specify pariticular technology
-  requires backbone to provide a specific set of service 

![ãInfrastructure BSSãçåçæå°çµæ](http://4.bp.blogspot.com/_mx1N_ZN8DgU/Sm6wcnWhGGI/AAAAAAAAAWs/5OslarklpWs/s400/2.jpg)

### Bluetooth topology

![A typical Bluetooth Piconet Â ](https://www.researchgate.net/profile/Farhat_Saleemi2/publication/228990705/figure/fig1/AS:393606675353600@1470854552026/A-typical-Bluetooth-Piconet.png)

![A Bluetooth scatternet](https://www.researchgate.net/profile/Xu_Cheng23/publication/4162479/figure/fig2/AS:667607342538754@1536181402464/A-Bluetooth-scatternet.png)

-  **Piconet** 
   -  master and slaves architecture
   -  maximum up to 7 slaves
-  **scatternet**
   -  a group of piconet

### **Main Appilcation of ZigBee**

-  Low Data-rate radio services

   -  Remote control,

   -  Joystick

   -  Personal Health care

   -  sensors

      ![ZigBee application](https://i.imgur.com/DtCu7G3.png)

### ZigBee Mesh Topology 

![02fig05.jpg (500Ã417)](http://ptgmedia.pearsoncmg.com/images/chap2_9780137134854/elementLinks/02fig05.jpg)

### MIssion of 3gpp

-  The 3rd Generation Partnership Project (3GPP)

-  developing globally acceptable specifications for third generation (3G) mobile systems. 

### shortcomings of CSMA/CD in wireless networks

-  collisions in wirerless channels are harder to detect
-  colisions leads to usage of bandwidth which is scarce

### Which layers IEEE 802.11 specify in their standards? Why?

-  only standardize PHY and MAC lyaer
-  Interfaces to higher layer is the same as those in iEEE 802.x standards
-  The upper layers is still the same as normal LAN
-  what the different is the medium for tranmission , it is in wireless now. 

### What are two principle operation modes of 802.11a/b/g/n systems?

-  ad-hoc mode
-  infrastructure mode

### Briefly explain evolution of air interface technology from GSM towards LTE.

**GSM**

-  TDMA and CDMA
-  FSK digital modulation

GPRS

EDGE

1. Why is ad-hoc networking useful in militaristic applications?

