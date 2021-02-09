# drone

1. [Application](hover-games-2-app.md)  
2. Title: Blockchain Witness.  
3. Synopsis: Tamper-resistant sufficient evidence of performed operations, involving secure randomized multi-route comm channel to the blockchain, in which packets are tagged with unique mission metadata, including GUID generators, two-way encryption keys, blockchain hashes, consensus-encoded unique environmental events, security hardware attributes, [GPSDO](https://en.wikipedia.org/wiki/GPS_disciplined_oscillator) & variants.  

## Comm channels

1. WiFi.  
2. SDR.  
3. Ham radio.  
4. Satellite.  
5. Mobile phone.  
6. Telemetry.  
7. LoRa.  
8. BLE.  
9. LoRaWAN.  

## Autonomous missions

1. Relief delivery.      (Deliver relief with strong proof.)  
2. Public-event witness. (Camera capture and real-time broadcast with strong proof.)  
3. Inclement weather.    (Maintain strong proof despite intermittent access to blockchain.)   

## Minimal application

1. NavQ has WiFi/Bluetooth.  
   1. How do they communicate?  
   2. What is the range?  
   3. Can I use the hotspot on my phone for field missions?  
2. Tag.
   1. GPS location and timestamp.  
   2. GPS constellation info.  
3. Path from sensor.  
   1. How to minimize tampering on the buses?  
3. Path to blockchain.
   1. Which blockchain can I use?  
   2. What libraries are there?  
4. Missions.  
   1. Autonomous flight. Fly to a GPS target location; land; generate delivery record (incl. image, possibly panorama); send to blockchain; fly back to origin.  
   2. Autonomous flight. Fly to a GPS target location; hover high and record tamper-proof and verifiable witness footage, send hooks to blockchain; fly back to origin; send full content to blockchain.  
   3. Autonomous flight. Fly to a GPS target location in high wind; generate target record + conditions report; put report in vault; fly back to origin; send to blockchain.  
5. Evidence presentation.
   1. Read the blockchain and present the evidence (mission log, witness footage, etc.). 
   2. Watch and monitor live (connectivity permitting.
   
## TODO

0. ~What does a submission look like?~
   1. Edit [here](https://www.hackster.io/projects/d0f902/edit).  
   2. Guidelines:
      1. [Tutorial](https://www.hackster.io/AlexWulff/how-to-create-a-high-quality-project-tutorial-e25feb).  
      2. [Guidelines](https://www.hackster.io/guidelines).  
   3. Compose cover image from [noun project](https://thenounproject.com/) icons.  
   4. Review and submit [here](https://www.hackster.io/contests/239/entries/12676/submit).  
1. Set up flight controller (Ground Control).  
   1. Can I develop on MacOS?  
2. Charge battery.  
3. Connect to WiFi network.  
4. Fly with RC.  
5. Dev environment, including PX4 clone.  
   1. Can I develop on MacOS?  
6. Round trip of minimal app.  
   1. Data from FC, esp. GPS.  
   2. Video from camera.  
7. Install NavQ and camera on top plate.  
8. Explore autonomous flight.  
9. 

