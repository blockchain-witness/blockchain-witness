# Blockchain Witness Design

_Based on [Hover Games 2 submission](https://www.hackster.io/ivogeorg/blockchain-witness-d0f902) on Hackster.io._ 

## Abstract

A randomized multi-channel tamper-proof path to the blockchain for transforming critical drone mission data into indisputable evidence.

**[IMAGE - Cover]**

Table of Contents
=================

* [Blockchain Witness](#blockchain-witness)
  * [Abstract](#abstract)
  * [Story](#story)
    * [Blockchain Witness](#blockchain-witness-1)
    * [Exemplary Missions](#exemplary-missions)
    * [System Overview](#system-overview)
    * [Satellite connection](#satellite-connection)
    * [LoRa communication](#lora-communication)
    * [NavQ](#navq)
    * [Vault-to-drone transfer](#drone-to-vault-transfer)
      * [Notes](#notes)
    * [Schematic](#schematic)

## Story

### Blockchain Witness

The central idea of the project is to enable drone mission data to be used as _indisputable evidence_. There are two factors that create the problem that I want to solve. First, _disinformation_ has become rampant, with various players aiming to distort reality in ways that are advantageous to their current interests. Second, drones are set to become ubiquitous technological participants in social life. As drones expand their capabilities and are employed increasingly widely across a whole range of domains, the need arises to be able to ensure and certify the results and products of work done by drones. Thus, mission data becomes critical evidence and it should be made maximally unassailable when brought up in support of solving disputes and properly, fairly, and specifically apportioning responsibility.

The pandemic has exasperated a number of fundamental problems, most importantly including general distrust in and disregard of evidence. If drones are to participate in critical missions during these critical times, they need a tamper-proof and sabotage-resistant technological safeguard of their mission evidence.

This project is a proof-of-concept for such a technology.

### Exemplary Missions

The application proposed three exemplary types of missions as a sufficient set of technological challenges to be solved:

  1. Remote delivery. For example, a small package of essential medication is delivered by a drone to a person otherwise unable to obtain it.  
  2. Public witness. For example, video footage of the attack on the Capitol is recorded by a drone and later used as evidence in court.  
  3. Adverse conditions. For example, a drone finds itself in adverse environmental situation (e.g. a sudden bout of inclement weather) and has to make a best attempt to complete the mission.  

**[IMAGE - Sketch]**

### System Overview

The hand sketch above shows the general components of the system in the second scenario, namely making a video recording of a public disturbance with potentially dire consequences. The sketch can be read clockwise, starting from the bottom left:

  1. The public event is represented by a street crowd with slogans and guns.  
  2. The drone is above, capturing footage.  
  3. The drone is keeping an active connection with available LoRaWAN gateways (requires horizontal connection and can be done in bad weather), as well as a heartbeat with the Iridium satellite network (requires clear skies).  
  4. The drone is processing the video frames in a secure hardware domain, watermarking them with the location data and encrypting them with newly generated keys. The video is stored in an encrypted format.  
  5. The drone sends over an Iridium connection a sequence of encrypted packets containing the video encryption keys and matched-time positioning-and-environmental metadata to a secure web service which commits them to the blockchain and returns over the Iridium connection blockchain fingerprint data to the drone, which stores them securely.  
  6. Upon landing or, in the case of a drone capable of live multimedia communications, the drone uploads the encrypted video footage to a secure web service, which holds it until subpoenaed. The drone also uploads the fingerprint data to a different branch of the service, also under strict access control.  
  7. The web service holding the scrambled data and the blockchain fingerprint issues credentials to officials with the need-to-know, although the access list is help public-record. The original footage is only shown to credentialed officials a set number of times and only through the eyes-only channel managed by the web service.  
 
For the other two scenarios, instead of video footage, the strongly-encrypted and authenticated data can contain trajectory compliance and proof-of-delivery data. The blockchain serves as proof-of-work and compliance certification.

### Satellite connection

Drone missions are likely to take the craft outside of Bluetooth, WiFi, GSM, and LTE range. For this reason, the application requires global two-way satellite messaging. The RockBLOCK by Rock7 provides messaging using the Iridium satellite constellation.

**[IMAGE - RockBLOCK & Package]**

The application only sends and receives textual data and does not rely on a satellite connection for video footage or other heavy data transfer. Instead, it uses the NavQ security features to keep the data tamper-free on the NavQ until the data can be uploaded to a secure online vault. The application uses the satellite connection to securely log mission evidence and obtain blockchain fingerprints for the encrypted local data bound for the vault.

**[IMAGE - RockBLOCK on wood block]**

The RockBLOCK sends messages to the Rock7 Core system, which can then forward to the vault service.

The RockBLOCK takes 5V of power and communicates over 3.3V serial. It just fits next to the NavQ on the standoff plate, though it might need to be moved in the future for better load balancing.

**[IMAGE - RockBLOCK & NavQ on addon plate]**

### LoRa communication

LoRa is quickly becoming the go-to choice for low-power long-distance radio communication for the Internet of Things. A recent product by SparkFun, the expLoRaBLE is a LoRa transceiver as well as an otherwise very versatile low-footprint low-power module. It contains a Bluetooth Low Energy module, a ultra low-power Apollo3 MCU and a I2C connector for daisy-chaining any number of sensors that can generate integrated evidence of obtained drone mission objectives.

**[IMAGE - expLoRaBLE]**

The image shows an environmental, human presence, spectral, and IR sensors. The module can easily be mounted on the front plate, even if a camera gimbal will be installed in the future.

**[IMAGE - expLoRaBLE on front plate]**

The expLoRaBLE requires an antenna. The ordered antenna has a long enough cable to allow for mounting on the top plate, so the position of the module on the front plate will not be a problem.

### NavQ

The NavQ is the nerve center of the application, both in software and hardware terms. The RDDRONE-FMUK66 flight controller, the GPS (via the flight controller), the the LTE modem, RockBLOCK, expLoRaBLE, and the camera all connect to it over serial interfaces. In addition, it houses the WiFi and Bluetooth 5 connectivity of the drone.

The NavQ's main features that make it ideal for this application are:

A lot of memory. A several-minute video of sufficient resolution can be stored in encrypted format until the drone returns to base.
Multi-core processors. Encryption of a real-time video stream will require a lot of burst computation
Machine learning. As every other security application, the Blockchain Witness has to adapt quickly to both new kinds of threats and new use cases. Machine learning will be the basis for developing a "smart witness", which maximizes the strength of its mission evidence protection policies while at the same time increasing the efficiency of service.
Security. NavQ has an impressive security stack which will be critical in closing all the loops within the application in a manner to withstand sabotage, scrutiny, and challenge.
Connectivity. The wide connectivity of the NavQ will be critical in capturing enough environmental and instantaneous information that can be verified and included into the secure mission log.
The interference among the various communication devices, even if they work on different bands, might become a large enough issue.

### Drone-to-vault transfer

#### Notes

1. [CAN](https://www.csselectronics.com/screen/page/simple-intro-to-can-bus/language/en) [logger](https://www.csselectronics.com/screen/page/can-logger-products) to sD card, possibly itself written in a tamper-proof manner based on blockchain fingerprints. _Requires manual step and a second device to read and transfer to vault._ 
2. No-touch version where drone hardware is plugged in directly to Ethernet/Internet and does a secure transfer to vault. After successful transfer, can scramble-overwrite the sD card to leave no trace of evidence.  
3. Secure CAN?  

### Schematic

**[IMAGE - Block schematic]**

