---
layout: post
title: Chapter 6 - 5G Cellular and New Radio
category: Wireless Networking
description: 5G Cellular and New Radio
---

# 5G Cellular and New Radio

## Satisying growing traffic demands 

### Is 4G enough 

-  1000Mbps for all subscribers in a cell
   -  Cell radius ~500m to 2Km
   -  Density of users : city centre -0.1 to 0.1 humans/m<sup>2</sup>
-  The traffic growth is so huge
   -  ![Global mobile data traffic (EB per month)](https://www.ericsson.com/assets/global/scaled/global-mobile-data-traffic-eb-per-month-101165crop0031251758resize1500844autoorientquality90stripbackground23ffffffextensionjpgid8_970x546_90_329667.jpg)

-  Performance metrics
   -  Shannon Channel capacity 
      -  $C=Blog_2(1+S)$
      -  B is  the bandwidth
      -  S is the SINR(signal-to-interference plus noise ratio)
         -  $S=\frac{P_R}{BN+I} $
         -  $P_R$ is the signal power at the receiver
         -  $N$ is the thermal noise, constant
         -  I is the aggregated interference
   -  Signal power at the receiver
      -  $P_r = P_TAd^{-Y}$
      -  $P_T$ is the emitter power at the transmier
      -  A is the constant that depends on antennas/frequency
      -  Y is the "path loss exponent" deponds on environment
-  FINAL VERISON = $C=Blog_2{(1+\frac{P_R}{BN+I})}$
   -  PHY Layer mechanisms
      -  FEC,MIMO,ARQ, 90% to shannon
   -  Increse emitted power  
      -  may increase interference
   -  Decrease thermal noise
      -  Constant up to 0.6Thz
      -  may use superconductor
   -  **Decrease interference** 
      -  Logarithmic increase of C
   -  **Increase bandwidth**
      -  Almost linear increase of C
   -  **Network Mechanisms**
      -  Better Spatial frequency reuse

### Increasing bandwidth 

-  buy more licenced frequencies
   -  Commercial netwoks(cellular networks)
   -  Exclusive access
   -  Ablity to use higher transmission power >1mW
   -  High costs and risks
   -  Less than 100-500Mhz overall in a country(less than 3Ghz )
-  Use the unlicensed spectrum
   -  ISM bands (Industrial, scientific, medical bands)
   -  Extreme interference from Wi-Fi-s
-  Spectral Efficiency
   -  the information rate that can be transmitted over a given bandwidth in a specific communication system
-  Quadrature Amplitude Modulation
   -  PSK+ASK :S(t)= $Acos(wt+\phi)$, modulating $w $and $\phi$
   -   ![img](https://upload.wikimedia.org/wikipedia/commons/9/90/QAM16_Demonstration.gif)
-  Higher frequency then more bandwidth available
-  5G: millimeter wave (mmWave)
   -  28Ghz
   -  60Ghz(802.11ad)
   -  72Ghz
	- ![img](https://cdn.everythingrf.com/live/Millimeter%20waves%20img_636793577330675858.jpg)
	- Postives
   	-  Highly directional antennas
	-  Negative
      -  	Blockage by humans
      -  	Large propagation losses
      -  	Realistically up to 100m
-  B5G,6G: teraherz(sub-mmWave)
   -  275-325 GHz: 50Ghz of bandwidth
   -  IEEE 802.15 3d"100Gbps wireless"
   -  Positive
      -  Even more directivity
      -  Hugh channel capacity
   -  Negative
      -  Atmospheric absorption（大氣吸收）
      -  Blockage by Human
      -  Extreme propagation losses
   -  up to 10-20m realstically
## 5G and New Radio Interface

### 5G/5G+ systems as enablers

-  Resembles properties of *CPS*
   -  CPS is Technological systems where physical and cyber components are tightly integrated(smartphone)
-  Moves us closer to tactile Internet（觸覺互聯網） conecpt， next IoT
-  Has to be supoorted by 5G/5G+ mobile cellular systems
-  At least two of the following are required
   -  High throughput
   -  High reliability
   -  Low latency
-  Reliable service over inherently unreliable medium



### Envisioned 3GPP 5G services

-  **Enhanced mobile broadband(eMBB)**
   -  data-driven use cases requiring high data rates across a wide coverage area.
-  **Massive machine-type communications(mMTC)**
   -  NB-IoT technology
-  **Ultra-reliable low-latency services (URLLC)**
   -  Not yet available and no dates annouced 

![img](https://www.2cm.com.tw/upload/news/N171013000720171013165542.png)



### 5G evolution or revolution 

-  5G/5G+ systems are heterogeneous(同質) in nature
   -  New Radio(NR) RAT(28,38,72GHz) 
      -  RAT (Radio Access Technology)
   -  Multi Rat support,,BT,WIFI,3G,4G,LTE
   -  Advanced features: D2D, relays, femto/micro BSs.
      -  D2D : Device to Device
   -  SDN/NFV capabilities for control plane
      -  SDN: Software Defined Networking
      -  NVF: Network Virtualization Function
-  NR is expected to support URLLC service
-  delivery up to 10Gps per AP
-  upper bound latency
-  provide reliability



### Propagation in mmWave band

-  Highly complex compared to microwaves
   -  Multiple paths
   -  Material dependent
   -  Spatial correlation
      -  the channels between different antennas are often correlated and therefore the potential multi antenna gains may not always be obtainable
   -  Temporal correlation

### Path blockage phenomenon

-  Very small wavelengths
   -  30Ghz ~1mm
      -  Cannot penetrate through objects
      -  Cannot travel around
-  Blockage happens at sub-second scales
   -  Models for various environments needed

### Beam tracking（波束追蹤）

-  Massive MIMO to form directional radiation patterns
   -  Linear arrays HPBW～102/N

-  ![directional radiation patterns](https://i.imgur.com/XiZsbjr.png)

-  Positive effects
   -  Much less interference
   -  Noise-limited regime?
-  Negative effects
   -  Beam alignment needed
   -  Array swtiching time ~2us
   -  Exhaustive vs hierarchical 
   -  Delay and loss in capacity ？

### Extreme and complex path loss 

-  ![pathloss](https://i.imgur.com/NPiXhiv.png)

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

 - Bloackage may or may not lead to outage(中斷)
    - Case 1: blockage leads to lower MSC scheme
      	- MSC: Mobile Switching Service Centre
   	- Case 2: bloackage leads to outage
- Solution
   - Case 1: provide more resources
      - Bandwidth reservation
      - Isolated deployments
   - Case 2: find a new path
      - 3GPP multi-connectivity
      - Dense deployments