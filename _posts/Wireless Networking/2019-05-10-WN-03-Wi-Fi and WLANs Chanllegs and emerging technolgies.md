---
layout: post
title: Chapter 3 - Wi-Fi and WLANs Challenges and emerging technolgies
category: Wireless Networking
description: challenges and emerging technologies
---



# Wi-Fi and WLANs Challenges and emerging technolgies  

(WLANs: enhancements 11e/n/ac/ad)

 

### Evaluation of IEEE 802.11

-  IEEE 802.11–1997(legacy)
   -  PHY layers
      -  1 Mbits/s over infrared frequencies
      -  1 and 2 Mbits/ over 2.4 Ghz unlicensed iSM band
      -  1 Gbit/s in 802.3z-98 (fibre optics)
      -  100 Mbit/s 8023y-98 (Ehternet)
      -  2Mbits/s 802.11-97 (Wifi)
-  IEEE 802.11b
   -  Improved PHY Layers
      -  DSS(Direct-sequence spread spectrum)
      -  22 Mhz channel
      -  Enhanced modualtion and cding
      -  5.5Mbit/s and11 Mbit/s
-  IEEE 802.11g
   -  one more PHY layer 
      -  for enhanced modulation and OFDM
   -  20 Mhz channel
   -  54 Mbits Data rates
-  IEEE 80.211e
   -  MAC layer improvement
      -  **Enhanced Distributed Channel Access (EDCA)**
         -  QoS(Voice over WLAN,Streaming)
         -   enhances the DCF and the PCF
         -  With EDCA, high-priority traffic has a higher chance of being sent than low-priority traffic
            -  Vocie > Video > Best-effort > background



### Othe enhancemet 

| IEEE 802.11        |                                                              |
| ------------------ | ------------------------------------------------------------ |
| IEEE 802.11a-1999  | OFDM, 54 Mbit/s, 5 GHz band                                  |
| IEEE 802.11d-2001  | make signaling (e.g. beacons) flexible to different countries regulations |
| IEEE 802.11h-2003: | Solving interference of IEEE 802.11a with satellites /radar using 5 GHz band |
| IEEE 802.11i-2004  | Improved WPA2 security mechanism for authentication and data encrypEon |
| IEEE 802.11j-2004  | Adaptation to 4.9-5GHz band according to Japanese spectrum regulaEons |



### Unified Approach (IEEE802.11-2007)

-  By 2007, 10 approach, difficult to maintain ,follow and support 

-  IEEE802.11-2007
   -  Unifield solution
   -  Three frequency band(Infrared, 2.4Ghz, 5Ghz)
   -  Three major PHY layers
      -  Legacy: 1,2, Mbit/s
      -  DSSS: 5.5 Mbit/s, and 11Mbit/s
      -  OFDM: 6,9,12,18,36,48,54 Mbits/s
   -  Basic(WEP) and enhanced (WPA/WPA2) scurity 
   -  20 Mhz-wide channels, Up to 54Mbit/s data rates
      -  Phy-Layer 
         -   close-to-optimal OFDM, hard to improve
      -  MAC- Layer
         -  low-weight signaling, hard to improve access scheme
-  By that time
   -  802.aq-2006 : 10 Gbit/s (multimode filter)
   -  802.3an-2006: 10Gbits/(medium-cost cable)



### Improvement on WIfi
- Appoaches

   - Extend the *channel bandwidth*
   - Exploit the *space domain*
   - Increase the channel utilization at MAC LAYER
      - BY extending the DATA frame duration
      - $Utilization=\frac{data.transmission.time}{cycle.time}$
      - There might be no content to feed such a long frame with data from a single application
         - audio frame MUST BE SHORT
         - Frame aggregation(增長術)![CWAP-Frame Aggregation-01](https://mrncciew.files.wordpress.com/2014/11/cwap-frame-aggregation-01.png?w=529&h=348)

   #### IEEE 802.11n

   - amendment to the 802.11-2007
   - PHY LAYER

      - 20Mhz(802.11-2007) to 40Mhz channels
      - Reduced guard interval (GI) from 800ns to 400ns
         -  Guard Interval : time interval between symbols
         -  Better electronic allows, have evolved since 1997
      - Introudction of up to 4x4 multi-antenna transmissions (multiple-input multiple-output)(MIMO).
   - MAC Layers

      - Frame aggregation
         - Reusing the same channel access procedure to transmit multiple frames
            - PHY-layers unit aggregation(A-MSDU)
            - MAC-layers units aggregation(A-MPDU)
   - Theorectical PHY-Layer throughput

      - 54Mbit/s of 11.g (20Mhz channel) -> 58.5 Mbit/s and 65Mbit/s (Reduced GI)
      - Single Stream Data rate is up to 72.2 Mbit/s(20Mhz)
         - 40 Mhz (150Mbit/s)
         - MIMO (600Mbit/s in theory)
    - Why NO 600Mbit/s Wi-Fi
      - Declared data rate is the raw PHY-layer data rate(Single user mode, no channel access)
       - Possible errors in the channel 
      - Channel access scheme(utilization is realistically around 50%)
       - IP and higher layers overheads (20-30% efficiency reduction)
       - MIMO data rate increase is far from linear
       - Channels is shared with other users
       - Interferaence 

- #### IEEE- 802.11ac
  
  - amendment to the 802.11-2012
  - Features
     - 80Mhz channels + 160Mhz optional channel
     - More aggressive moudulation techniques (QAM-256,non-standard implementation of QAM-1024)
     - UP TO 8 MIMO
     - DOWN LINK (from AP to clients) multi-user MIMO(MU-MIMO)
  

 IEEE - 802.11ad

  - 60Ghz band (mmWave), 2.16Ghz channels
  - up to 7Gbit/s, Typically cannot penetrate walls
  - Highly-directional transmissions, large-scale antenna arrays
  - Mac signaling revised from AC
  - Appilcations
     - Wireless display, connectivity for UHD deplolyment, VR,AR

### Chanllenges for WLAN

-  Increasing data rate,
   -  limited bandwidth , low distance
-  High dense deployment, 
   -  many devices per AP, collisions
-  Multi-cell ,
   -  inter-cell interference
-  IoT and M2M communications
-  User mobility between different cells, 
   -  Transparent connecEvity between the cells



