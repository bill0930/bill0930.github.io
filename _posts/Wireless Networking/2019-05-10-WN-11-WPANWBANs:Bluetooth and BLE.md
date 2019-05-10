---
layout: post
title: Chapter 11 - WPANWBANs:Bluetooth and BLE
category: Wireless Networking
description: WPANWBANs:Bluetooth and BLE
---



# WPANWBANs:Bluetooth and BLE

## PAN/BAN

![PAN/BAN](https://i.imgur.com/4r8hX15.png)

![range](https://i.imgur.com/3latrrV.png)

![Usage Scenarios of ban/pan](https://i.imgur.com/E17GF0L.png)

## IEEE 802.15 

Discussed in Chapter10



## BAN/PAN technical challenges and design issues

### Technical challenges

| Problems                           | Detail                                                       |
| ---------------------------------- | ------------------------------------------------------------ |
| Address is not a physical location | The station is not always stationary. The address does not give an information about location |
| Dynamically changed topology       | The network connectivity is partial at times                 |
| Medium boundaries are soft         | The communication range cannot be determined precisely.      |
| Erroneous medium                   | BER in wireless network is about 10<sup>-4</sup>compared to 10<sup>-9</sup> in fixed networks |
| Hidden terminal problem            | Some nodes should (not) be allowed to communicate at a certain time |

### Design Issues

| Ceriteria to be meet                | Detail                                                       |
| ----------------------------------- | ------------------------------------------------------------ |
| Operational simplicity: BAN/PAN     | Mobile use MUST be able to quickly set up and access network services in a SIMPLE manner |
| Power efficienct operation: BAN/PAN | The main resource of MT is the power: power saving features  |
| Licence-free operation: PAN         | Lost cost installation is required for widespread usage, e.g., ISM band |
| Tolerance to interference: BAN/PAN  | There are a lot of technologies operating in ISM band causing interference between them. |
| Security: PAN                       | PAN is vulnerable to different attacks                       |
| Compatibility: BAN/PAN              | Compatibility with other technologies and applications is required for a commercial success. |

## Bluetooth general description

### What bluetooth appears?

-  the need for personal services to communicate directly without infrastructure
-  PAN/BAN paradigms have appeared
-  Bluetooth is the most successful standard for BAN/PAN

### Bluetooth specifications

-  **Basic structure**
   -  **Core specifications** : DL and PHY PROTOCOLS
   -  **Profiles** : applications
-  **Functions performed by the stack**
   -  locating/connecting devices,exchanging data
-  **Functions Logically divided into three groups**
   -  **transport protocol group**
      -  RF: radio and antenna;
      -  baseband sublayer
      -  ling mangager, logical link control and adaptation sublayers
      -  host controller interface
   -  **middleware protocol group**
      -  RFCOMM, SDP, TCS
   -  **application group**
      -  profiles
-  ![Protocol stack of Bluetooth ](https://i.imgur.com/9ndvvPL.png)

## Network Topologies

### Transport Protocol Group(TPG)

-  locating services: allows devices to locate each other
-  creating, configuring, and managing wireless link
-  TPG aims
   -  low power consumption
   -  simplicity of operation
   -  low cost of the communicating entity
-  Three genreral choices were made for bluetooth
   -  master-slave architecture (simplicity)
   -  frequency hopping communication (tolerence to interference)
   -  gateway-based large newtorking (extensions)

### Piconet

-  consists of the master and slaves, initiator of the formation: master;
-  can have up to seven active(!!!) slaves at any time
-  each active slave of the piconet is a unique active member address BD_ADDR.

![A typical Bluetooth Piconet Â ](https://www.researchgate.net/profile/Farhat_Saleemi2/publication/228990705/figure/fig1/AS:393606675353600@1470854552026/A-typical-Bluetooth-Piconet.png)

### Scatternets

-  **Piconet may operate spatially**
   -  piconets can operate in the same area in the same time
   -  each piconet is characterized by a unique master;
   -  piconets hop independently with its own hopping sequences.
   -  with more piconets added, probability of collision increases (frequency hopping).
-  **Only a few active devices in Piconet**
   -  Bluetooth unit may operate as a slave in different piconets
   -  Bluetooth unit may operate as a master in only one piconet!

**DEFINITION**: A group of piconets between which connections exist is called a *scatternet*.



![A Bluetooth scatternet](https://www.researchgate.net/profile/Xu_Cheng23/publication/4162479/figure/fig2/AS:667607342538754@1536181402464/A-Bluetooth-scatternet.png)

## Transport Protocol Group

-  It deals with 
   -  PHY layer
   -  data-link layer
-  Bluetooth radio
   -  in ISM frequency 
   -  a variance of frequency modulation, GFSK
   -  64Kbps voice channel
   -  asynchronous data channel with peak rate of 1Mbps
   -  FHSS(*Frequency-hopping spread spectrum*) operating over the set of m = 79 channels each of width of 1MHz;
   -  hops are made across all channels starting at 2.402GHz and stopping at 2.480GHz;
   -  the transmit power of 1mW, extension to 100mW;
   -  the nominal link range is up to 10m (1mW), can be extended to 100m (100mW).

### Baseband sublayer

-  functions 

   -  hop selection
   -  connection setup
   -  medium access control

-  **Creating and maintaining piconets**

   -  **the address of a device**
      -  three part 48 bit address
         -  lower address part (LAP): used in piconet ID, error, security checking
         -  reamining two parts are addresses assigned by manufacturer
   -  **the clock associated with a device** 
      -  native clock : 28 bit clock
      -  3200 times persecond (interval is 312.5 us)
      -  3200 is twice the hopping rate (1600 hops/s)

   

### Organization of the communication channel

-  Basic

   -  the channel is divided into time slots of 625 μs
   -  TDD *(Time-division Duplex )*scheme is used where master and slave alternatively transmits
   -  packet transmission is aligned with the beginning of the slot
   -  slots are numbered according to the clock of the master
   -  master starts its transmission in even-numbered slots, slave in odd-numbered slots only
   -  slave is allowed to transmit only if in the preceding slot it received a packet from the master

   ![Channel Organization](https://i.imgur.com/4W1tE9b.png)

### State operations in Bluetooth

![State operations](https://i.imgur.com/vDlLRJ5.png)

### Selection of frequency hopping sequence

-  **Hopping sequence: FSM**
   -  clock value
   -  address
-  **Clock and address are different in different modes**
   -  **Connected State:**
      -  The clock value of unknown
      -  the address of the device is known
   -  **Inquiry State**
      -  address input to FSM is a inquiry address
      -  at the time of inquiry, no device has information about the hopping sequence
   -  **Paging State**
      -  The address of the paged device is entered in FSM

### Inquiry State

-  Essential state for bluetooth
   -  any device which is initially in the *standby state* enters the i*nquiry state*
   -  to collect *information* about other Bluetooth devices in its neighborhood
      -  infomration includes address and clock value of the master
-  The Inquiry proceeds as follows
   -  master sends an inquiry packet on the inquiry hop sequence of frequencies
      -  the common address is fed to the FSM
   -  a device that wants to be discovered enters the inquiry state and listens for these packets
   -  when inquiry message is received, responses with packet containing the device address.

![inquiry state](https://i.imgur.com/2GJgFAg.png)

### Page State

-  **Why to enter and from which state**

   -  to invite other devices to join a piconet
   -  to inquiry operation precedes this state

-  **Three substates**

   -  **Page sub-state**(master)

      -  the master estimates the slave clock value
      -  determines the hop sequence where the slave might be listening in the page scan mode 
      -  transmits the page message in preceding, estimated and following hop sequences 

   -  **Page scan sub-state**(slave)

      -  slave listens the channel for a page message
      -  upon receiving the page message the salve enters the salve page response sub-state
      -  slave sends page response message

   -  **Page response sub-state**

      -  the master informs the salve about its clock and address
      -  the salve calculates an offset to sychronize with the master clock

      ![page-operation](https://i.imgur.com/TNY482j.png)

### Connected State

![connceted state](https://i.imgur.com/N1Ty0bD.png)

### Packet-based communication

-  Access code
   -  contains the address of the piconet master
   -  all packets exchanged on the channel are identified by the master’s identity
   
-  Header
   -  **three bit active slave number**
      -  the maximum number of slaves in the piconet is 7;
   -  **a one bit ACK/NACK field**
      -   to retransmit erroneously received frames;
   -  **four bit packet type field:**
      -  to distinguish between payload types
   -  **eight bit header error check**
      -  to detect errors in the header
   
-  Payload
  
-  Depending on the payload size ONE, THREE, OR FIVE slots can be used for packet
  
   ![Multiple slot](https://i.imgur.com/l7wUAmZ.png)
   
-  Above

   -  single slots are used to transmits packets
   -  frequencies are F(k), F(k+2), F(k+4), F(k+6) for transmission slots.
   
- Middle
  
  -  two slots are used to transmit a first packet
  -  requency F(k+4), not F(k+3) is used for transmitting a packet

-  Links in a piconet
   -  **asynchronous connectionless link (ACL)**
      -  default link that exists once the connection established
      -  whenever a master would like to communicate, it does so
      -  slave can only respond after the master’s transmission
   -  **syncrhonous connection-oriented link(SCO)**
      -  SCO link is a symmetric between master and a slave with *reserved bandwidth*
         -  *reserved bandwidth*: just reserved time slots at regular intervals;
      -  *why*: high-priority and time-bound information such as video and audio.
-  Communication in a piconet
   -  only between master and its slaves
   -  is not possible between slaves
   -  master does not route packets of its slaves

### Link Management Protocol

-  Functions

   -  setting and maintaining the properties of the Bluetooth link
   -  power management
   -  security management
-  Power Management

   -  **Active mode**
      -  actively participates in the piconet
   -  **Sniff mode**
      -  listen only certain slots
      -  master commands the source to go to this mode
   -  **Hold mode**
      -  slave temporarily does not support ACL packets on the channel
      -  capacity is made available for paging, inquiring, or attending another piconets
   -  **Park Mode**
      -  very low-power mode allowing master to have more than 7 slaves
      -  slave is given an eight bit parked member address, remains synchronized, no active address
      -  a message to the parked station is sent over broadcast channel
-  Security

   -  **key management** : to share and distribute keys
   -  **authentication** : to know the communicating entity
   -  **encryption**: performed for packet payloads
- Error detection and correction
  -  detect : checksum is added to a packet
  -  correct: FEC  with two rates (1/2,1/3): flexible for payload, strict (1/3) for header;
  -  correct: ARQ with ACKs and NACKs

![ARQ](https://i.imgur.com/a7F1TgJ.png)

### Host controller interface

-  Functionality

   -  interface layer between the layers above LMP and lower layers
   -  provides access to Bluetooth hardware capabilities

### Logical Link control and adaptation protocol (L2CAP)

-  Functionality
   -  abstraction of higher layer protocols via multiplexing of protocols
   -  segments and resembles packets to combot BER

![L2CAP](https://i.imgur.com/t6mwrYI.png)

## Middleware protocols

-  provides standard interface to applications

   -  **Service discovery protocol**(SDP)
      -  Fully automatic of request-response type
   -  **RFCOMM**
      -  virtual serial port, any application that use serial port can work seamlessly
   -  **IrDA interoperability protocols**
      -  *IrDA object exchange (IrOBEX)* used for exchanging objects between two devices;
      -  *Infrared Mobile Communication protocol (IrMC*) used for synchronization
   -  **Telephony control specification** (TCS)
      -  audio signal are carried out over SCO at 64kbps
      -  defines
         -  call control
         -  group management
         -  connectionless TCS

   

## Bluetooth Profiles

-  What and Why
   -  provides standard to implement a specifc user function
   -  to allow interoperability between different Bluetooth implementations

-  13 profiles are calssifiled into
   -  **Generic Profiles**
   -  **Telephony Profiles**
   -  **Networking Profiles**
   -  **Serial and object exchange profiles**

## Advantage and shortcoming of BT

| Advantage                                              | Shortcomings                                         |
| ------------------------------------------------------ | ---------------------------------------------------- |
| fill the gap in networking on scales shorter than WLAN | Does not provide support for routing                 |
| exceptionally well standardized                        | No support of handover                               |
|                                                        | Master is a bottleneck                               |
|                                                        | Bluetooth has operates in ISM band like 802.11b WLAN |
|                                                        | Complexity grows                                     |
|                                                        |                                                      |

## Bluetooth low energy(BLE)

### why BLE 

-  bluetooth is doing extremely well
-  bluetooth is good for industry
-  very robust to interference , frequency hopping
-  compete with Zigbee

### Definiition and benefits

-  definition
   -  open, low energy and short range wireless technology

-  benefits (good for small, discrete data transfers)
   -  low power consumption
   -  small size 
   -  connectivity to mobile phone
   -  low cost, robust, efficient 
   -  multi-vendor interoperability
   -  global availability, license free

-  temperature, time, pressure, speed sensing
-  2mAh per day

### Constraints

-  **Imposed constraints**
   -  **reuse as much Bluetooth RF as possible** 
      -  only need 60% RF silicon area compared to Bluetooth
      -  can use the same antenna as Bluetooth
      -  can TDM with BT
   -  **reuse as much BluetoothL2CAP as possible** 
   -  **reuse as much Bluetooth hHCI as possible** 
      -  same HCI physicial interfaces
      -  same HCI packet formats 
      -  same HCI drivers in OS
-  **Design Goals**
   -  **lowest possible power operation**
      -  turning radio off for as much of the time as possible
      -  reducing the ***complexity*** of a single mode device to almost nothing
         -  reduced memeory requirement
            -  reduced leackage current
               -  battery lifetimes !
      -  80% to 60% of traditional BT chips
      -  designing a connectionless data model
   -  **lowest possible latency**
   -  **widest possible range of interoperable devices and application**

### Acheiving low power

-  **By keeping the radio off**

   -  lower standby time
   -  faster connection
   -  lower peak power

-  **BLE only use 3 advertising channels(vs. 16-32channlels)**

   -  RF is on for 1.2ms  vs 22.5ms

-  **Idle current is dominated by deep sleep current**

   -  sensor type send data less often (0.5 to 4s)
   -  RF current is neligible due to low duty cycles
   -  Protocols 

-  **Faster connections**

   -  a device that is advertising is able to connect to a scanning device
   -   The devices can connect and sendand acknowledge data in *3 ms* 
      -  vs classic BT 100ms

-  **Lower Peak Power** 

   -  BLE uses relaxed RF parameters
      -  GFSK modulation index increased(From 0.35 to 0.55)
   -  Packet length restricted
      -  Together with GFSK gives lowest complexity transmitter / recevier
      -  This results in a lower peak power

   

### Data rate and throughput

-  **NOT ABOUT data rate/ throughput**
   -  about 260kbps maximum data rate
   -  concentrates more on lowest possible poewr consumption
-  **ABOUT transferring state**
   -  small, infrequent bits of data
   -  owest possible poewr consumption
   -  lowest latency

### PHY Layer

-  **Split the 2.4Ghz ISM band into 40 channels**

   -  3 Advertising Channels
   -  37 Data channels
   -  $f_n = 2402+2n$Mhz

-  **GFSK Modulation**

   -  Modulation index 0.5, better range than the classic
      -  allows use of fewer advertising channels
      -  reduces power consumption
      -  increases connection speeds
   -  Can reuse existing RF parts in BTchip
      -  minimal additional cost in dual-mode chips

### Master/ slave topology

-  Master is typically the central device
-  Salve is typically the peripheral device
-  Slave is very VEry power sensitive
   -  power consumption
-  Master is time sensitive
   -  latency

### Separate adveritisng dand data channels

-  **Data channels**
   -  used to transfer reliable data robustly
   -  adaptive frequency hopping over *37 channles*
   -  fast acknowledgement scheme
   -  if data doesnt get through, resent on next freqeuncy
-  **Advertising channels**
   -  402, 2426, 2480Mhz. 
      -  it would avoid interference with Wi-Fi traffic
   -  Used by peripherals to advertise presence
      -  when first power on
      -  why they have data to send - central devices connect and get data
      -  just to broadcast data to anybody scanning



### Security

-  uses AES-128 with CCM encryption engine
-  **Use Key Distribution to share various keys**
   -  Identity Resolving Key is used for privacy
   -  Signing Resolving Key provides fast authentication without encryption
   -  Long Term Key is used for encryption
-  **Pairing encrypts the link using a Temporary Key**
   -  derived from passkey, NFC pairing, public key exchange (v1.1);
   -   then distribute keys.
-  **Asymmetric key model:**
   -  slave gives keys to master with a diversifier
   -  slave can then recover keys from the diversifier



### Encryption

-  **RFC 3610 based AES-128 encryption:**
   -  Counter Mode Cipher Block Chaining Message Authentication Code
      -  Counter mode CBC-MAC = CCM.
-  **Each new data packet has a Message Integrity Check:**
   -  39 bit counter, 1 direction bit;
   -  64 bit Initialization Vector 32 bits contributed by each device;
   -  MIC is 32 bits in length
-  **MIC is separate from the CRC**
   -  CRC can allow immediate acknowledgment;
   -  packet is only sent to host after MIC checked
   -  lowest peak power

### Survaviblity

-  **Robustness to Vital for Bluetooth**
   -  it must be robust against 2.4 GHz ISM band interference
   -  Wi-Fi, 802.15.4, X-10, proprietary, etc
-  **Coexistence is Vital**
   -  should not interfere with existing Wi-Fi infrastructure/ad-hoc network;
   -  Adaptive Frequency Hopping is needed
   -  FCC recognizes this as the best way to avoid interference;
   -  Discovering devices / connecting devices should not break Wi-Fi
   -  It must not affect Bluetooth headsets

### Power Consumption

-  **Relative consumption**

   -  Sleep time is way more longer
   -  power mode 1 : 3us wake up time consuming 235uA;
   -  power mode 2: wake up via sleep timer consuming 0.9uA
   -  power mode 3: via external interrupt consuming 0.4uA

   

-  **Power consumption during the connection event:**
   -  between connection events: power mode 2
   -  turning off: voltage regulator, processor, oscillator
   -   active: sleep timer, RAM and registers retained
   -   going active: via I/O interrupt or expiring sleep timer