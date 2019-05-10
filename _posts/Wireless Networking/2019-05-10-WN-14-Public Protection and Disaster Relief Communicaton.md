---
layout: post
title: Chapter 14 - Public Protection and Disaster Relief Communications
category: Wireless Networking
description: PPDR
---

# Public Protection and Disaster Relief Communications

## Definition 

-  PPDR communications can be distinguished in those 
   -  used by agencies and organizations responsible for dealing with
      -   maintenance of law and order
      -   protection of life and property , and emergency situations
   -  and in those used by agencies and organisations dealing with 
      -   a serious disruption of the functioning of society,
      -  posing a significant, widespread threat to human life, health ,
      -  property or the environment 
   -  whether caused by 
      -  accident, human activity and ,
   -  whether developing suddenly or as a result of complex, long term processes



## Users and types communication

-  **Emergency response as multi-agent system**

   -  Public safety agency should be always (24/7) ready for emergency response 

   -  A multi-agent system is a system composed of multiple interacting intelligent agents. 

   -  Rescue teams are in fact multi-agent systems where coordination is critical 

      -  to improve coordination such missions often rely on coordination centers that needs to be provided information in real-time;
      -  the more information about the context of a mission is provided the more precise/efficient coordination is.

   -  Communication technologies is a significant factor of multi-agent systems’ performance 

-  **PPDR USERS** 

  -  Regular Police
  
-  Fire Brigades
  -  Emergency Medical Services (EMS)
  -  Part-time Fire
  -  Special police Functions 
  -  EMS civilian support
  -  Police Civilian support 
  -  Fire civilian Support
  -  Genreal Government Personnel
  
- **Types of communication** 
  
  -  human-to-human
     -  ![H2H](https://i.imgur.com/KsMefq8.png)
  -  humah-to-machine
     -  ![H2M](https://i.imgur.com/D487Jig.png)
  -  machine-to-machine
     -  ![M2M](https://i.imgur.com/yTHtUJ5.png)
  
    

## Application and services

-  **PPDR application**
   -  ![PPDR_APP1](https://i.imgur.com/A0cEtiL.png)
-  **PPDR application 2**
   -  ![PPDRAPP_2](https://i.imgur.com/P5Tgl6S.png)

-  **PPDR Broadband**
   -  ![PPDR_BROADBAND](https://i.imgur.com/AW07aJR.png)

-  **Capabilities provided under Localized Communication Services**
   -  ![LCS](https://i.imgur.com/uxalOwr.png)





## Obejctives according to ITU

| Objective                                                    |
| ------------------------------------------------------------ |
| **to support the integration** of voice, data, video and image communications as part of a multimedia capability; |
| **to provide additional level(s) of priority, availability and layered security** associated with the source, destination and type of information carried over the communication channels used by various PPDR applications and operations; |
| **to provide each PPDR agency and organization with user authentication (**e.g. public key cryptography) among PPDR agencies and organizations and for their devices prior to granting access to their applications or network resources; |
| to support operation in **extreme** or **adverse environments** (high mobility, heat, cold, dust, rain, water, noise, shock, vibration, extreme temperature, and extreme electromagnetics, etc.); |
| to suppor**t robust equipment** (e.g. hardware, software, operational and maintenance aspects, long battery life). Equipment (handheld or transportable) that functions while the user is in motion is also required. Equipment may also require unique accessories, which could include special microphones; |
| to **accommodate the use of repeaters for covering long distances between terminals and base stations** in rural and remote areas and also for intensive on- scene localized areas; |
| to provide **fast call set-up, one-touch broadcasting (PTT to group) and group call** features; |
| to provide for <u>emergency calls, one-touch emergency alert</u> (emphasizing that this function is used in life threatening situations and should receive the highest level of priority), emergency voice PTTs, and emergency data PTTs (e.g. sending images, real-time video) during PPDR events; |
| to support information **pull, push and subscription** with prioritization; |
| to provide for **strong multi-national/multi-agency** technical interoperability over multi-network and device technologies in a seamless fashion |
| to provide **Localized Communication Services (LCS),** **Relayed Device Mode Communications (RDM)** , **Direct Mode Operation (DMO**); |
| to provide for **the ability of PPDR communication systems to interface with other dedicated PPDR** and/or commercial systems; |
| to be **scalable in order to suit small and large agencies**, without sacrificing the ability to interoperate; |
| to provide for **quick deployment of temporary infrastructure** and services as well as recovery from failure; |
| to support **continuous use of basic PPDR services in case of infrastructure collapse or failur**e, e.g. loss of backhaul link between base station and core network; |
| to support **the need for high level of security** without compromising the response time; |
| to **provide audio quality** that ensures the listener is able to understand without repetition, identify the speaker, detect stress in a speaker’s voice, and hear background sounds without interfering with the primary voice communications. |
| **Low Latency –** very short call **set up times (< 500 ms)** and very limited end to end **voice/data transmission delay (< 1 s)**. |



## Spectrum requriements 

-  **How to calculate for it**
   -  Determine busy hour call attempts per PDDR user for each service in each environment
   -  Determine effective call/session duration
   -  Determine activity factor
   -  Calculate busy hour traffic per PPDR user
   -  Calculate offered traffic/cell for each service in each environment 

![](https://i.imgur.com/nALQjsP.png)



-  **Unique PPDR requirement** 
   -  Blocking = less than 1%
   -  Modularity= ~20 channels per cell per network 
   -  Frequency reuse cell format
      -  12 for like power mobile or personal stations 
      -  21 for mixture of high/low power mobile and personal stations. 
   -  Determine number of service channels needed for each service in each “service” environment (NB, WB, BB). 

## Existing and future PPDR communication 

-  **Exisiting PPDR communication**
   -  EU(380-400Mhz)
   -  The network deployment and relevant infrastructure is usually built for nationwide coverage and is owned by state agencies that permit network utilisation among public protection and disaster relief (public) organisations.
   -  These networks satisfy the security and reliability requirements. 
   -  However, they can support a limited number of multimedia services.

-  **Metrics of interest** 
   -  mean throughput per node
   -  fraction of time when at least one node is disconnected
   -  mean number of disconnected nodes

## Conclusion

-  Emerging PPDR applications utilize heavy-traffic services, which can not be served by existing PPDR communication systems 
-  Millimeter wave technologies may **address wireless demands of heavy traffic application**s, however, **the reliability of mmW** communication **doesn’t satisfy the reliability requirements** 
-  The reliability of mmW communication can be enhanced by using mesh technology and AI 
-  Development of technologies which improve the reliability of mmW is a relevant research challenge 

