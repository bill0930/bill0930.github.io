---
layout: post
title: Chapter 1 - Wi-Fi MAC basics IEEE 802.11(1)
category: Wireless Networking
description: basics of IEEE802.11
---

# Wi-Fi MAC basics: IEEE 802.11(1)

## Centralized multiple access

### Why we need multiple access scheme

-  bandwidth is a scarce resource at the air interface (頻寬是珍貴的資源)
-  there are a numbers of users that want to transmit （有很多users想要transmit）



### Centralized vs. Random access

-  Centralized: master contorls assignment 
   -  Wireless Wide Area Netowrk (WWAN)
   -  Wireless Metropolitan Area Networks(WMAN)
-  Random: Station compete for access 
   -  Wireless Local Area Network (WLAN)
   -  Wireless Personal Area Network (WPAN)
   -  Wireless Body Area Network (WBAN)
-  Therera are total four centralised multiple Access schemes
   -  Frequency Division Multiple Access (FDMA)
   -  Time Division Multiple Access (TDMA)
   -  Code Division Multiple Access (CDMA)

#### Frequency Division Multiple Access( FDMA)

![FDMA](https://i.imgur.com/Dr3N2f4.png)

-  Share avaliable bandwidth in the **frequency domain**

-  avaliable bandwidth is *divided* into **a number of channels**;

-  there should be a *guard band*  between adjacent channels;

   -  guard band —> inefficient use of the spectrum

-  each transmitter/receiver pair is assigned the same channel for operation

   

#### Time Division Multiple Access (TDMA)

![TDMA](https://i.imgur.com/TFGVTaI.png)

-  Share avaliable bandwidth in the **time domain**
-  frequency band is divided into **a number of time slots**
-  a set of **periodically repeated time slots** is known as *<u>TDMA frame</u>*
-  each node is assigned a slot in each frame and transmits only in this slots 



#### Spread Spectrum Techniques

-  every user uses the entire spectrum
-  individual transmission are **encoded** with **pseudo-random sequences**
-  assigned codes are *orthogonal* so that the ***simultaneous transmission* are possible** 
-  Two types
   -  Frequency Hopping Spread Spectrum (FHSS)
      -  Spectrum is divided into many subchannels
      -  two communicating systems hop on same frequencies 
   -  Direct Sequence Spread Spectrum (DSSS)
      -  station are assigned orthogonal codes
      -  use these codes for transmission
      -  other stations transmission appears an noise



## Random Access Schemes

-  provideds access to a channel for multiple concurrent stations 
-  is not needed when there is a centralized control 
-  required when the access is *distributed* 
-  can be used for decentralised in TDMA and FDMA channels

-  ALOHA and slotted ALOHA
-  Carrier Sense Multiple Access (CSMA)
-  Carrier Sense Multiple Access with Collision Avoidance (CSMA/CA)
-  Carrier Sense Multiple Access with Collision Detection (CSMA/CD)





### ALOHA

#### Pure Aloha

-  a terminal transmits whenver the user data is ready
-  if the sender finds that the packet get collided
   -  it waits for a random period of time and sends the packet again

#### Slotted Aloha

-  time is slotted, length on the slot is the time to transmit a packet
-  node starts transmission in the beginning of slots only
-  if collisions occurs:
   -  sneder waits for a random number of slots
   -  transmits packet again

Throughput: Slotted Aloha is better than Pure Aloha but still low



### Carrier Sense Multiple Access

-  Throughput of ALOHA is low
-  should listen for packet transmissions
-  3 types of  CSMA
   -  1-persistent CSMA
   -  non-persistent CSMA
   -  p-persistent CSMA

#### 1-persistent CSMA

![1 Persistent CSMA](http://ecomputernotes.com/images//thumb477-1-Persistent-CSMA-a40386981840fd08910d6519fb6240a7.jpg)

-  when the packet is ready for transmission, the sender listens to the channel

-  if the channel is free,  packet is immediately transmitted

-  if not ,the senders continues to listen till the channel becomes free

-  If two are more stations becomes ready at the same times, collision happens

   -  Probability of starting transmission when the channel is free: 1.

-  Two bad effect 

   -  Wrong "Channel free" effect 

      -  an arbitray node starts transmitting
      -  a node near the destination sense the channel and finds it free since packet has not yet arrived 

   -  Synchronization effect

      -  the propogation delay




#### Non-persistent CSMA

![Non persistent](http://ecomputernotes.com/images//thumb477-Non-persistent-aa89bbc631b8fe7790ec84457669dbc4.jpg)

-  to solve the synchronization problem
   -  when the packet is ready for transmission , the sender listens the channel
   -  if the channel is busy , the sender goes in the waiting state for a randomly chosen time
   -  after this time , the sender sense the channel again

![Non-persistent CSMA](https://i.imgur.com/rQ2a6bc.png)

### p-persistent CSMA

-  the cahnnel is slotted
-  transmission is free channel is preformed with Probability $p$
-  When the packet is ready for transmission , the sender listens the channel
-  if the channel is busy , the sender keeps listens the cahnnel until it finds the channel idel;
   -  if idle
      -  the sender transmits the packet in this slot with probability $p$
      -  defers transmission to the next slot with probability $q=1-p$

![p persistent CSMA](http://ecomputernotes.com/images//thumb477-p-persistent-CSMA-c651238f482b7294a12aff223c8278e9.jpg)





### Carrier sense multiple access with collision detection(CDMA/CD)

![Fig06-11](https://player.slideplayer.com/16/5112858/data/images/img1.jpg)

-  if the collision is detected , the nodes immediately aborts its current transmission
-  then, the node sends a brief jamming signal
-  any other transmitting node on hearing the jamming signal abort their tranmissions
-  after transmitting the jamming signal the node waits for a random time and repeats the CSMA.