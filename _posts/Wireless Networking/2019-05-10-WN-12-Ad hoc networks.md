---
layout: post
title: Chapter 12 - Ad hoc networks 
category: Wireless Networking
description: Ad hoc networks 

---





# Ad hoc networks 

## Cellular and ad-hoc wireless networks

| Cellular networks                           | Ad-hoc wireless network                      |
| ------------------------------------------- | -------------------------------------------- |
| Fixed infrastructure                        | No infrastructure                            |
| Single-hop wireless links                   | Multi-hop wireless links                     |
| Guaranteed CBR bandwidth (voice traffic)    | Shared radio channel (data traffic)          |
| Initially, circuit-switched                 | Initially, packet-switched                   |
| High cost and time of deployment            | Very quick and cost-effective                |
| Reuse of frequency via channel reuse        | Dynamic frequency sharing                    |
| Bandwidth reservation is achieved easily    | Complex MAC layer                            |
| Nowadays applications: civilian, commercial | Nowadays applications: military, rescue      |
| High cost of network maintenance            | Maintenance operations are built-in          |
| Low complexity of mobile devices            | Intelligent mobile devices are required      |
| Widely deployed, evolves                    | Still under development in commercial sector |



## Application of ad-hoc wireless network 

-  applications
   -  military applications
   -  collaborative and distributed computing
   -  emergency and rescue operations
   -  mesh networks
   -  wireless sensor networks
   -  hybrid cellular / ad-hoc wireless networks

-  why ?
   -  quick depolyment 
   -  inexpensive deployment and operation



## Technical challenges

### Medium Access Scheme

-  MAC usded for shared use of the transmission medium
-  performance depends on MAC protocol 
-  chanllenges
   -  distribution operation
   -  maximum throughput
   -  minimum access delay
   -  fairness
   -  real-time trafiic support
   -  power control capabilities
   -  use of directional antennas
   -  hidden/exposed terminal problems

### Routing 

-  responsible for 
   -  determining a feasible path
   -  discovering, storing, and exchanging routing information
   -   gathering information about a path breaks and updating route information accordingly
-  Challenges
   -  Mobility
   -  Bandwidth constraints
   -  Resource constraints
   -  Errorneous transmission  medium
   -  Location-dependent contention 
-  requirements on a routing protocol in ad-hoc networks
   -  minimum route acquisition delay
   -  Quick route configuration
   -  loop-free 
   -  distributed routing
   -  low overhead
   -  scalabiltiy
   -  privacy
   -  support for time-sensitive traffic

### Multicasting 

![Unicast-Broadcast-Multicast](http://www.steves-internet-guide.com/wp-content/uploads/Unicast-Broadcast-Multicast.jpg)

-  **Multicasting is an important feature in wireless ad-hoc networks:**
   -  search and rescue operations: distribution of commands
   -  military applications: distribution of command
-  **Why not to adapt something from fixed networks (CBT, PIM, DVMRP)**
   -  core base trees (CBT), distance vector multicast routing protocol (DVMRP), etc.
   -  mobility of nodes changes the topology of the network! Trees are unstable!
-  **There are following challenges in ad-hoc environment for multicasting:**
   -  Fast recovery;
   -  Control overhead;
   -  Efficient group management;
   -  Scalability;
   -  Security.



### Transport Layer Protocol

-  **Major function of connection-based transport layer protocol:**
   -  setting up and maintaining end-to-end connection
   -  reliable end-to-end delivery of data packets
   -  flow control
   -  congestion control
-  **Why not to go with UDP**
   -  does not perform *flow and congestion control* and *reliable* end-to-end transfer;
-  **Performance degradation stems from**
   -  high error rate
   -  frequent path breaks
   -  presence of 'old' routing information
   -  network partitioning



### Quality of Service provisioning 

-  **QoS**
   -  traffic performance in the network
   -  service support performance
   -  service operability performance
   -  service security performance
-  **To satisfy QoS**
   -  use values of traffic engineering variables that constitute the so-called Grade of Service (GoS)
-  **Provision of QoS requires:**
   -  negotiation between the host and a network
   -  resource reservation schemes
   -  priority scheduling
   -  call admission control

### Self-organization

-  **Self-organization is the main attractive property of ad-hoc networks.**
-  **To perform self-organization the following things are required:**
   -  **neighbour discovery**
      -  first phase when a node switches on;
      -  a node should gather network information (transmission of reception of discovery packets).
   -  **topology organization**
      -  every nodes gathers information about the entire network (a part of);
      -  construct and maintain the network topology.
   -  **topology reorganization**
      -  when links break, nodes switch off etc
      -  requires periodic or aperiodic exchange of topology information.

### Security 

-  **Ad hoc are more vlunerable to attacks because** 
   -  lack of central coordination
   -  shared wireless medium
-  **Two types of attacks**
   -  **passive attacks**
      -  malicious nodes attempt to obtain information relayed in the network;
      -  no damage to operation of the network, just capture if information
   -  **active attacks**
      -  **external attacks:** attacks executed by nodes outside the network;
      -  **internal attacks:** attacks executed by nodes belonging to the same network.
-  **Denial of Service**
-  **Resource consumption**
   -  **Energy Depletion**
      -  to deplete the power of the node relaying the traffic through them. 
   -  **Buffer overflow**
      -  fill the routing table with ’bad’ entries to consume the buffer space of the target node. 
-  **Host impersonalization**
-  **Infomration disclosure**
-  **Interference** 

### Addressing and service discovery

-  **Addresses**
   -  Global unique address
   -  autoconfiguration of address
   -  Duplicate address detection mechanism
-  **Meaningful features for ad-hoc network**
   -  automatic service advertisement mechanism
      -  should allow to identify the **current** location of the service
      -  it is not possible to assume static service locations in ad hoc networks.
   -  integration of service discovery protocols and routing protocols
      -  may allow to easily find the necessary service in a networ
      -   may violate the traditional design objectives of the routing protocol

### Energy management 

-   can be done
   -  shaping the energy discharge pattern
   -  use routes with minimal total energy consumption
   -  use special task scheduling schemes
   -  proper handling the processor and interface devices
-  can be achieved by
   -   Transmission power management
   -  Battery energy management
   -  Processor power management
   -  Interface power management



### Scalability

-  **Testbeds and operational ad hoc networks made so far:**
   -  contain only a limited number of nodes
   -  may not be good examples of ad hoc performance
-  **What we may expect in real implementations**
   -  performance of ad-hoc network degrades drastically with the increase of the number of nodes
   -  one may expect commercial realization of, at least, thousands of nodes

### Deployment 

-  **Low cost** : no cables, no configuration, no maintenance
-  **Incremental** : functioning starts immediately after minimum configuration is done
-  **short time** : no cables, no configuration, no maintenance
-  **reconfigurability** :   no cables, no configuration, no maintenance



## Example : data-link/network/transport 

### Data-link layer MACA

-  **MACA**: 
   -  stands for MAC protocol for ad hoc networks.
-  **major facts**

   -  contention-based without reservation and scheduling
   -  MACA was prposed as an extension for CSMA/CA protocol
   -  was further extended and adopted for IEEE 802.11
-  CSMA
   -  the sender sense the channel for the carrier signal;
   -  if the carrier is present it retries to sense the channel after some time (exp. back-off);
   - if not, the sender transmits a packet
-  Shortcoming for CSMA/CA
   -  hidden terminal problem leading to frequent collisions;
   -  exposed terminal problem leading to worse bandwidth utilization

**MACA avoids hidden and exposed terminal problems using the RTS-CTS.**

![RTS-CTS](https://i.imgur.com/w88AJEK.png)



-  RTS and CTS packets carry the expected duration of transmission;
-  	**a node near the sender**
   -   that hearing RTS do not transmit for a time to receive CTS;
-  **a node near the receiver**
   -  after hearing CTS differs its transmission
-  **if the neighbor hears the RTS only**
   -  it is free to transmit



### Network layer: Location Aided routing (LAR)

-  use the location information
-  reactive protocol

-  Two zones
   -  **Expected Zone**
      -  a geographical zone in which the location of the terminal is predicted based on:
         -  location of the terminal in the past
         -  mobility information of the terminal
   -  **Request Zone**
      -  a geographical zone within which control packets are allowed to propagate
         -  area is determined by the sender of the data packet
         -  control packets are forwarded by node within a RequestZone only
         -  if the node is not found using the first RequestZone, the size of RequestZone is increased.

-  Nodes decide whether to forward or discard packets based on two algorithms: 
   -  LAR type 1
      -  ![type1](https://i.imgur.com/ihS9gNr.png)
   -  LAR type 2
      -  ![type2algo](https://i.imgur.com/Dqz46uQ.png)



### Transport-layer protocols: Split TCP

-  **TCP major problems**
   -  **degradation of throughput with increase of path length**
      -  ![TCP-1](https://i.imgur.com/ylD7NOK.png)
   -  **unfairness among TCP flows**
      -  ![TCP2](https://i.imgur.com/xs3DqE4.png)

-  split-tcp provides the solution by splitting the TCP functionality into two part
   -  **congestion control**
      -  local phenomenon due to high contention for resources
   -  **end-to-reliability**
      -  end-to-end phenomenon

![split-tcp](https://i.imgur.com/opQoko0.png)

**Split TCP:** 

-  splits the connection into a set of concatenated TCP connections
   -  ![SPLIT-TCP-2](https://i.imgur.com/8zJ5w0g.png)

-  **proxy node** 
   -  terminating the connection from the sender/precessor proxy node;
   -  setting up a connection with receiver/successor node.
   -  are chosen using the distributed algorithm
      -  packet traversed n hops - behave as a proxy
-  **Transmission control at the TCP sender window is split**
   -  end-to-end CW
      -  updated according to arrival of end-to-end ACKs
   -  local CW: (local CW ≤ end-to-end CW)
      -  updated according to arrival of local ACKs (LACKs) from the next node. 
-  **Proxy node behaves**
   -   it maintains local CW governing transmission in a segment; 
   -  when packet arrives from predecessor the LACK is sent back; 
   -  arrived packet is buffered;

   -  the buffered packet is forwarded to the next node. 

![split-tcp-flow](https://i.imgur.com/eVyNi82.png)