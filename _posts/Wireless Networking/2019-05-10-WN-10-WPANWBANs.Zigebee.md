---
layout: post
title: Chapter 10 - WPAN/WBANs.Zigebee
category: Wireless Networking
description: WPAN/WBANs.Zigebee
---



# WPAN/WBANs.Zigebee.m

## IEEE 802.15 WG 

-  Specify WPAN standard
-  Wireless Personal Area Network 

-  **TG 1 802.15.1: WPAN/Bluetooth**
   -  defines PHY and MAC of Bluetooth
   -  standard issued in 2002 and 2005
-  **TG 2: 802.15.2: coexistence**
   -  coexistence of WPANs with other networks in unlicensed band;
   -  EEE 802.15.2-2003 published in 2003 and then ”hibernated”.(休眠)
-  **high rate WPAN**
   -  802.15.3-2003 is a MAC and PHY standard for high-rate (11 to 55 Mbit/s) WPANs;
   -  802.15.3a: UWB PHY... no agreement when choosing PHY (MB-OFDM vs. DS-UWB);
   -  802.15.3b-2005: improve implementation and interoperability of the MAC;
   -  802.15.3b-2009: mm-wave-based PHY, 57-64Ghz unlicensed band, >2Gbps
-  **TG 4: Low Rate WPANs**
   -  long battery life, low data rate, low complexity;
   -  802.15.4 standard released in May 2003;
   -  many networks runs on top of 802.15.4: ZigBee, 6LoWPAN, WirelessHART, etc.
-  **Enhancements of 802.15.4**
   -  802.15.4a-2007: additional PHYs, e.g. UWB pulsed radio;
   -  802.15.4-2006: clarification of the original standard;
   -   IEEE 802.15.4c: adaptation to unlicensed bands in China;
   -  IEEE 802.15.4d: adaptation to unlicensed bands in China;
   -  IEEE 802.15.4e: enhancements for industrial apps, e.g. channel hopping;
   -  IEEE 802.15.4f: active RFID systems;
   -  IEEE 802.15.4g: smart utility networks: large networks with a lot of end systems.

-  **TG 5 Mesh networking**
   -  two parts: low rate and high rate mesh networks;
      -  low rate: IEEE 802.15.4-2006 MAC
      -  high rate: IEEE 802.15.3/3b MAC;
   -  common features: network initialization, addressing, multihop unicasting;
   -  low rate: multicasting, broadcasting, portability, trace route and energy saving
-  **TG 6 Body Area Network**
   -  low-power short range standard, draft in 2011
-   **TG 7: visible light communication**
   -  work in progress

## ZigBee

-  developed by ZigBee Alliance
-  on top of IEEE 802.15.4
-  Particular implementation of those features specified in IEEE standard
-  Toptology in
   -  Centralized star
   -  Cluster-tree-based
   -  full mesh(requires additional routing protocol)
-  Specifics:
   -  low-rate (even compared to Bluetooth)
   -  extremely low power consumption
   -  example of applicability: sensor networks

### Comparison with other technologies

![Comparison](https://i.imgur.com/Tb2FbrU.png)

#### IEE 802.11x technolgies

-  **3x more expensive** than Bluetooth

-  **5x the power consumption** of Bluetooth

   ![IEE 802.11x technolgies](https://i.imgur.com/8VIrxBF.png)

#### Reason for Zigbee

-  low cost, high reliability, very long battery life
-  high security, self-healing properties, larger number of nodes supported
-  ease of deployment, guaranteed delivery, route optimization

-  NOT CHOOSING
   -  Very specific apps
   -  BLE Exists

### ZigBee application

![ZigBee application](https://i.imgur.com/DtCu7G3.png)

-  Wireless sensor networks

### ZigBee Protocol Overview

![Zigbee protocol](https://i.imgur.com/1EcuoD6.png)

### IEEE 802.15.4 PHY

-  **Three low power unlicensed radios:**
   -  2.4Ghz: 250Kbps(EU) 16 channels (ch11-ch26);
   -  915Mhz: 40Kbps(US) 10 channels(ch1 - ch10)
   -  868Mhz: 20Kbps(Europe and Japan) 1 channel (ch0)
-  **Cahnnels and modulation in 2.4Ghz**
   -  16 channels , each 5Mhz wide  ch 11-26
   -  actual throughput, 50% of 250Kbps due to overheads
      -  overheads: addressing, security, error control
   -  DSSS (direct sequence spread spectrum ) channel access
   -  O-QPSK modulation
-  **Other responsiblities of PHY**
   -  detecting transmissions from new nodes
   -  assessing quality of links with other nodes

### IEEE 802.15.4 MAC

-  **Functionlity** 
   -  CSMA/CA
   -  max.length of packet is 127bytes (2 bytes for CRC)
   -  guarantees? transmissions
-  **Two modes of operation** 
   -  Acknowledge
   -  Unacknowledge
-  **How ACK mode is implemented**
   -  setting ACK bit in a forward packet
   -  if set: receiver ACKs correct reception
   -  if no: ACK is received with some time, retransmission

### Device types

-  **FFD (Full Function Device)**
   -  capable of all the features and always "on"
   -  routing/coordination/network formation
   -  can talk to other FFDs and RFDs
   -  FFDs require more power
-  **RFD (Reduced Function Device)**
   -  Sometimes called leaf nodes
   -  simple netoworking functions
   -  end systems in a sensor network
   -  can talk to FFD only

### Logical entities 

| Full Function Device (FFD)     | Reduced Function Device (RFD)    |
| ------------------------------ | -------------------------------- |
| Found in any topology          | Found only in start topology     |
| Can be a network co-ordinator  | Cannot be a network co-ordinator |
| Can talk to any type of device | Talks only to FFD                |
| Usually main powered           | Usaully battered powered         |

-  **Network Coordinator**
   -  FFD, one per work
   -  Create a network , assign channel/address
   -  adds new devices to a network
   -  constant power supply
   -  sometimes serves as a gateway
   -  a node may join if the coordinator is up
   -  if down, already existing node may continue to network
-  **Router Functionality**
   -  FFD devices serving as a relay node
   -  range extension
   -  constant poewr suplly
   -  sores packets sent to sleeping nodes
   -  can be used to access the network
-  **End Device**
   -  FFD/RFD
   -  low power consumption
   -  sleeping modes are defined
   -  communication through routers

### Network Topologies 

#### Star Topology

![img](http://ptgmedia.pearsoncmg.com/images/chap2_9780137134854/elementLinks/02fig02.jpg)

| Advantage                     | Disadvantage                            |
| ----------------------------- | --------------------------------------- |
| small delay due to single hop | single point of failure(co-coodinator)  |
|                               | end devices cannot communicate directly |

#### Cluster-tree Topology

![img](http://ptgmedia.pearsoncmg.com/images/chap2_9780137134854/elementLinks/02fig04.jpg)

- two levels of hierarchy
- more nodes can be added via routers
- large coverage areas
- several paths in-between end nodes



#### Mesh Topology

![02fig05.jpg (500Ã417)](http://ptgmedia.pearsoncmg.com/images/chap2_9780137134854/elementLinks/02fig05.jpg)

-  extension of cluster-tree topology
-  connections to deveices at different layer feasible
-  RFD are still unable communicate directly

+  DELAY CAN BE REDUCED but COMPLEXITY of ROUTING is HIGH

### Access methods

-  **non-beacon access**
   -  transmit at anytime when channel is idle
   -  "free-for-all" environment
-  **beacon-based access**
   -  coordinator generates a superframe identified at beacon time
   -  all nodes are synchronized
   -  nodes transmit only i its designated time slot
   -  superframe may contain common slot when stations compete
   -  in-between: could go sleeping 



### Creating a network 

-  **Initialization for coordinator**

   -  a node searches for coordinators on all channels;
   -  if no coordinators, starts its own one using unique 16-bits PAN ID;

-  **Initialization for end nodes:**

   -  scanning all available channels;
   -   can detect *router* and *coordinator* with the same PAN ID
   -  if yes, device with *strongest SNR* is chosen;
      -  end devices sends "can i join"
      -  address is allocated if there is place for a new node

-  **Parameters set by a coordinator:**

   -  **max number of *child devices*** allowed per router
   -  **max number of *hops*** from the co-ordinator to the most distant device

###  

### Network Example

![zigbee_network](https://i.imgur.com/fA24reI.png)

### Addressing

-  **Three types of IDs**
   -  MAC address (64-bits ID)
   -  network address(16-bits ID)
   -  name of device

### Unicasting and broadcasting

-  **Usage of address** 
   -  while joining: extended MAC address
   -  while connected: short network address
-  **Unicast**
   -  network address is used as destination address in MAC header
   -  message is routed in the network
   -  destination accepts the message, others drop
   -  destination answers with ACK
   -  the process is a bit more complex: local ACKs
      -  ![LOCALACK](https://i.imgur.com/HmjTMdq.png)
-  **Broadcasting is used when** 

   -  joining or rejoining network
   -  discovering routes in the network;
   -  should be minimized  
- **Broadcasting**
  -  MAC address is 0XFFFF
  -  all active devices receive and analyse the message.
  -  all active FFD devices retransmit it
-  **ACKing broadcast message**
   -  no explicit active ACKs
   -  passive ACKing: listening whether all neighbors retransmitted
      -  if not repeat the transmission

### Routing and route discovery

-  **General consideration**
   -  star topology no need routing
   -  cluster-tree and mesh topologies need routing
   -  more than one approach
-  **Cluster-tree topology**
   -  tree-routing
      -  works fine for small networks
   -  route discovery
      -   work when network is unstable or large
-  **Mesh topology**
  
-  route discovery is only possible with AODV
  
-  **Tree routing**

   -  use tree hierarchial structure
   -  first decision: whether to go up or down in hierarchy
   -  examining
      -  if destination is a descendant, the device sends the packet to a child;
      -  otherwise, send it to a parent 
   -  upon reception by a node
      -  accepts if the destination is a directly connected child
      -  otherwise: sends to a parent

   BAD: path could be longer than needed

   GOOD: quite stable as tree structure is guaranteed

### Sleeping modes

#### General facts

-  reduce power consumptions
-  still retain network address while sleeping
-  parent device buffers packets while child is asleep
-  upon wake up it checks whether there are some in store

#### Two types of sleeping mode

-  Cyclic sleep
-  additional modes : can be controled , pin sleep

