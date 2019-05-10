---
layout: post
title: Chapter 2 - Wi-Fi MAC basics IEEE 802.11(2)
category: Wireless Networking
description: basics of IEEE802.11
---



# Wi-Fi MAC basics: IEEE 802.11(2)

## WLAN technical chanllenges and design issues

### Problems making WLAN design a complicated task:

-  <u>Address</u> is not a physcial location 
-  Dynamically changed <u>topology</u>
-  <u>Medium</u> boundaries are **soft** 
-  <u>Erroneous</u> medium
-  Hidden and exposed terminal problems

—> Reliable network using unreliable channels

### Criteria to be met

-  <u>Operational</u> Simplicity
-  <u>Power</u> efficient opeartion
-  <u>License</u>-free operation
-  Tolerance to <u>interference</u>
-  <u>Security</u>
-  <u>Compatibility</u> 
-  Global usability, safety, QoS



## Overview of IEEE 802.11

-  802.11x specifies the **physical** and the **medium access conrol (MAC)** layers only
-  interfaces and higher layer is the same as those in IEEE 802.x standards
-  MAC layers should be able to work with multiple physical layers

#### Task Group

| 802.11 Task group | description                                                  |
| ----------------- | ------------------------------------------------------------ |
| 802.11 WG         | develop MAC layer and physical layer specifications, 1997    |
| **802.11a WG**    | **WLAN operations in 5Ghz freq.band , 1999 (54Mbps), **, (first appeared on the market) |
| **802.11b WG**    | **2.4GHz (ISM) frequency band, 1999,11Mbps, refer to Wifreless Fidelity (Wi-Fi)** (<u>most successful among family )</u> |
| 802.11c WG        | bridging and access points operations, 1998                  |
| 802.11d WG        | 802.11 operation in different countries,2001                 |
| 802.11e WG        | QoS provision extension                                      |
| 802.11f WG        | inter access point protocols for operation in ESS, 2003      |
| **802.11g WG**    | **54Mbps, compatible with 802.11b;**                         |
| 802.11h WG        | MAC layer to be in compliance with European standards, 2003  |
| 802.11i WG        | security extensions for 802.11                               |
| 802.11j WG        | 4.9GHz band in Japan                                         |
| **802.11n WG**    | **MAC layer to achieve very high data rates (up to 600Mbps) **, <u>is backward compatible with 802.11b/g</u> |

#### Development and layered structure of IEEE 802.11

-  Wireless *connection* management 
-  link *reliablity* management
-  *power* and *security* management

![802.11_structure](https://i.imgur.com/9hkHQTB.png)

## Physical Layer

![802.11_structure](https://i.imgur.com/FL94WOX.png)

-  IEEE has three options for medium to be used for communcation
   -  one is based on <u>infrared</u> 
   -  two tohers based on <u>radio</u> 
-  Physical Layer divided into 
   -  **PMD(Physical medium-dependent sublayer)（物理媒體相關子層）**
      -  Handles functions related to medium adaptation
         -  encoding
         -  decoding
         -  modulation
      -  **FHSS PMD (Frequency Hopping Spread Spectrum PMD)**
         -  2.4GHz ISM band
         -  use -2-level GFSK for 1Mbps and 4-level GFSK for 2Mbps
            -  Gauss frequency Shift Keying 
      -  **DSSS PMD (Direct Sequence Spread Spectrum)**
         -  operates in 2.4Ghz ISM band
         -  use DBPSK for 1Mbps and DQPSK for 2Mbps 
      -  **INFRARED PMD**
         -  operates in 850-950nm range
         -  provides data rates of 1Mbps and 2Mbps using PPM(Pulse Position Modulation)
   -  **PLCP(Physical layer convergence protocol)（物理層匯聚過程子層）**
      -  Abstract the functionality of PMD providing 
         -  Service Access Point (SAP)
         -  Clear Channel Assessment (CCA) Carrier sense signal

EXTENSTIONS FOR IEEE 802.11 DEFINE the following PMDs

| IEEE WLAN standards |                                                       |
| ------------------- | ----------------------------------------------------- |
| IEEE 802.11b        | 2.4Ghz ISM band, DSSS with CCK provide up to 11Mbps   |
| IEEE 802.11a        | 5Ghz, OFDM to provide up to 54Mbps                    |
| IEEE 802.11g        | 2.4Ghz , OFDM 20~54Mbps (DSSS with CCK if < 20Mbps)   |
| IEEE 802.11n        | 2.4Ghz OFDM+MIMO spatial streams, wider 40Mhz channel |



## MAC Layer Mechanisms

#### Main function of MAC Layers

-  to <u>arbitrate transmission requests</u> of wireless stations opearting in the area
-  to <u>multiplex transmission</u> requests
-  to provide <u>roaming</u> support
-  to authentication wireless stations;
-  to <u>conserve</u> power consumption

#### Service Support

- Asynchronous data service is mandatory
- Real-time  service is optional 

#### Medium Access Method Defined

![DCF_PCF](https://i.imgur.com/xUs4N8V.png)

-  **The Distributed Coordination Function (DCF)**
   -  primary access method defined in IEEE 802.11
   -  based on CSMA/CA that use RTS-CTS mechanism
-  **Point Coordination Function (PCF)**
   -  is implemented on top of DCF to provide real-time service
   -  AP controls medium access avoiding simultaneous transmissions 

### Interframe Spacing: Priorities in frame transmission

| Inter-frame Spacing (訊框間隔)      |                                                              |
| ----------------------------------- | ------------------------------------------------------------ |
| Shortest inter-frame spacing (SIFS) | the shortest ISF, highest priority, used for RTS/CTS and ACKs |
| PCF inter-frame spacing (PIFS)      | used by PCF in contention-free operation                     |
| DCF inter-frame spacing (DIFS)      | used by staions in DCF mode(asynchronous data)               |
| Extended inter-frame spacing(EIFS)  | used when there is an error in frame transmission            |

#### Choices for shared medium access

-  **CSMA-CD**
   -  used in IEEE 802.3 networks
   -  DISADV :collisions is wireless channels are harder to detect
   -  DISADV: collisions leads to usage of bandwidth which is scarce
-  **CSMA/CA was used**

#### Carrier Sensing

-  **Physical Carrier sensing**
   -  direct sensing of the PHY
   -  expensive  provided by the physcial layer, complexity depends on the PHY.
-  **Virtual carrier sensing:**
   -  provided by the <u>Network Allocation Vector (NAV)</u>
   -  NAV Indicates how long the medium is reserved
   -  NAV is set acccrdoing to fields (Duration ) indiated in most frames



#### How CSMA/CA Performs

-  if hte medium is sensed to be free for DIFS, the node access medium for transmission
-  if the medium is busy, the node **back off** for a contention time,
-  when back off time expires , the station can access the medium
   -  -during back off, if the node detect a channel busy, it freezes the CW, where is  *the integer multiply of slot times*
   -  CW is resumed when the channel is sensed to be free for DIFS

![frozen_backoff_timer](https://i.imgur.com/uQPhOjP.png)

##### Contention Window Size Setting

-  if CW is small in size
   -  values are close to each other at different MTs
   -  increases in the numbers of collision on the shared medium
-  if CW is very large
   -  unneccessary delay is introduced
-  contention window in set to a random value between (0,$CW_{min}$);
-  Collision occurs : CW doubles up to $CW_{max}$

![Contention_Windows](https://i.imgur.com/acQY72C.png)

### Acknowledgements

#### WHY ACKs

-  frequently frames are incorrectly received

#### HOW ACKS

-  if a packet is correctly received , the priority transmission is organized for ACK(SIFS)
-  the <u>receiver</u> accesses the medium after waiting for a SIFS and sends ACKS



### Error Detection

-  CRC code is used
-  if no ACK is recevied by the sender, frame is retransmitted 
-  the number of retransmissioned is limited
-  if the limit is exceedd , the rror to higher layer is reported



### RTS-CTS 

-  to solve Hidden Terminal Problem

![HTP](https://pic.pimg.tw/oilcut123/1393228354-2638627403.png)

#### RTS-CTS Mechanism

-  **the senders sends an *RTS packet* to the recevier including**
  
   -  the intended receiver of the **datapacket**
-  the whole expected **duration** of transmission 
  
-  **RTS packet is received by all MTs in one-hop neighborhood of the sender**
  
   -  they set their NAV
   -  NAV specifies the earliest time when the station is permitted to attempt transmission
   
-  **The intended receiver of packet does :**

   -  wait  for SIFS
   -  repsonse with CTS packet
   -  CTS contains the duration field

-  **CTS packets is received by all Mts in one-hop neightborhood of the receiver**

   -  set NAV
   -  if the set of stations receiving RTS and CTS are different, hidden terminal exist.

-  All stations are informed and <u>the medium is resreved for one sender</u> exclusively

-  The sender starts its transmission after waiting for SIFS

-  The receiver receives packets waits for SIFS and repsonds with ACK

   The NAV in each node marks the medium as free

![RTS-CTS-ACK](https://i.imgur.com/ZNqMQRI.png)

| Shortcoming                                         | Advantage                            |
| --------------------------------------------------- | ------------------------------------ |
| significant overhead and sometimes is not performed | remove the hidden terminal problem   |
|                                                     | Perforamnce well in overload network |

-  Sometimes RTS-CTS is not performed
   -  depends on ***RTS threshold***
      -  ">" RTS threshold , RTS-CTS-DATA-ACK
      -   "<" RTS threshold, DATA-ACK
   -  perform well in moderately loaded network but not in overload network



### Fragmentaiton and reassembly 

#### Purpose

-  to <u>decraese the number of incorrectly received frame</u> due to bit errors
-  <u>the length of the fragments are equal</u> to each other within a single packet
-  the length of final fragment can be less
-  fragments contains information nedded to resemble the initial packet

![Fragmentation](https://i.imgur.com/XC0EVPQ.png)

![ãFrame formatãçåçæå°çµæ](http://www.iitk.ac.in/mla/rgandhi%20website/80211b/frameformat_dataframe.jpg)



### Other Mac functions

-  Point Coordination Function(PCF)
   -  provides QoS parametres : max access delay, minimum transmission bandwidth
-  Synchronization
   -  each statiion has a clock ,all clocks have to be sychrnoized
-  Power management 
-  Qos in IEEE 802.11 environment
   -  Hybrid coordination Function (HCF)
-  Support for roaming
   -  AP has a range of up to several hundreds metres
   -  when the stations begins to experience a poor single quality it scans for a new AP



### Scanning Method 

-  **Active Scanning** 
   -  sends a probe on each channel and waits for responsive
-  **Passive scanning**
   -  listneing to the medium to find other networks



![Scan Methods](https://www.adriangranados.com/sites/default/files/images/blog/understanding-scan-modes-wifiexplorerpro/wifiexplorer-scan-modes.png)



|                     | IEEE 802.11b                           | IEEE 802.11a                                      | IEEE 802 .11g                                     | who wins                                    |
| ------------------- | -------------------------------------- | ------------------------------------------------- | ------------------------------------------------- | ------------------------------------------- |
| Power efficiency    | DSSS *direct-sequence spread spectrum* | OFDM *Orthogonal frequency-division multiplexing* | OFDM *Orthogonal frequency-division multiplexing* | 802.11b more powe efficient                 |
| Frequency           | 2.4Ghz ISM, highly overloaded          | 5Ghz,higher absorbtion rate                       | 2.4Ghz ISM, highly overloaded                     | poor performance  in overloaded environment |
| Communication range | ~150m                                  | ~50m                                              | 50~150m                                           | 802.11b                                     |
| Data-rate           | 11Mbps                                 | 54Mbps                                            | up to 54Mbps                                      | higher than b ,lower than a                 |
| Cost efficiency     | well-established manufacturing         | components are more expensive                     | expensive than 802.11b, less expensive than a     | 802.11b is cheaper                          |
| Compatibility       | first                                  | not compatible with 802.11b                       | compatible with 802.11b;                          | 802.11g is good                             |
| Number of users     |                                        | More users, higher bandwidth and more channels    | same number of channel as in 802.11b              | capacity of 802.11a is higher               |





## System design for networking in IEEE802.11	

## Types of network based on IEEE 802.11

#### Baic Concept in 802.11 System 

-  **Basic Service Set (BSS)**: a set of stations communicating with each other
-  **Basic Service Area(BSA)**:  area in which stations communicate

#### Two modes in operation 

-  **Independent BSS: IBSS (Ad-hoc mode)**

   -  MT communicates directly with other Mts with APs

   ![ãIBSSãçåçæå°çµæ](https://www.researchgate.net/profile/Abdel_Karim_Al-Tamimi/publication/228847534/figure/fig4/AS:340391829229571@1458167144257/WLAN-IBSS-Structure.png)
- **Infrastructure BSS (Infracstruture mode)**
  
   -  MTs communicatie via AP

   -  Less complex configuration
   
   -  Ap assists station in power savings
   

![ãInfrastructure BSSãçåçæå°çµæ](http://4.bp.blogspot.com/_mx1N_ZN8DgU/Sm6wcnWhGGI/AAAAAAAAAWs/5OslarklpWs/s400/2.jpg)

- **Extended Service Set (ESS)**
  - created by linking BSSs using backbone network
  - provide larger service areas
  - does not specify pariticular technology
  - just requires backbone to provide a specific set of service 

![ãâ¢ extended service set (ESS):ãçåçæå°çµæ](https://www.researchgate.net/profile/Mustafa_Mustafa3/publication/264347658/figure/fig2/AS:669052099891217@1536525859580/Extended-Service-Set-ESS-25.png)

### Components in infrastructure BSS/ESS

#### Compoents 

-  Distribution system : backbone network
   -  capabilities of bridging APs
   -  relay (接力) of frames within ESS
   -  Inter AP protocoal (IAPP)
-  Access points 
-  Wireless medium 
-  Station

### Network Services

Provided by 

#### AP

| Network Sevices provided by *AP* |                                                              |
| -------------------------------- | ------------------------------------------------------------ |
| Association                      | The address of MT must be known by AP before communication. This is done via association. |
| Reassociation                    | The established association is **transferred from one MT to another** using reassociation. |
| Disassociation                   | When node leaves AP or shuts down it enforces disassociation. |
| Distribution                     | This refers to the distribution of **traffic** within, in and out the network. |
| Integration                      | This service is evoked when transmission via non-IEEE 802.11 network is required |

#### MT

| Network Sevices provided by *MT* |                                                              |
| -------------------------------- | ------------------------------------------------------------ |
| Authentication                   | This is used in order to establish the identity of stations to each other. Authentication implementation may range from insecure handshake procedures, to public key encryption schemes. |
| Deauthentication                 | terminate existing authentication                            |
| Privacy                          | The contents of messages os sometimes **encrypted** using a certain protocol to prevent unauthorized reading. |
| Data delivery                    | IEEE 802.11 networks provide a way to transmit and receive data. The transmission is **not guaranteed to be completely reliable**. |

