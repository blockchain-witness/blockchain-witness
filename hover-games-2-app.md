# Prove it happened: A secure mission log for drones operating in adverse conditions and under scrutiny by the public and authorities

[[URL](https://www.hackster.io/contests/hovergames2/hardware_applications/12825)]

## What problem are you going to solve?

Pandemics divide and break societies. The more evident disruptions of the latest pandemic, like retail, education, air travel, and health care, obscure deep fault lines in the fabric of society, which took months into the pandemic to gape open. The street protests, the violent reactions for and against, the strong polarization of every conversation, the extreme entrenchment of political groups into diametrically opposite visions for the future are fueled into overdrive by the inexorable rise in the numbers of infections, deaths, broken lives, overt racism, job loss and deepening poverty. 

To quote Tim Urban: "Here are four reasons this scares me:
1) We’re losing our ability to gain knowledge. ...
2) We’re losing our ability to think together. ....
3) We’re losing our ability to cooperate. ...
4) We’re doing that thing that people do before really, really awful things happen. ..." [1]

While the trends of polarization were not caused by the pandemic, the pandemic has exacerbated them, pushing society over the brink into social unrest and freelance violence. We have lost the desire to work toward consensus. Large swaths of society have become convinced that consensus is, in fact, unachievable. Rampant disinformation has eroded people's bedrock of values and truths, throwing everything once dear and sacred into the air in a free-for-all race for egotistic short-sighted oneupsmanship.

If drones are to make a difference not only in the immediate effects of the pandemic but the systematic unraveling of liberal values and democratic societies, they have to be unassailable in the climate of "alternative facts". I am proposing a full-stack technical solution to safeguard drone mission information from tampering, sabotage, and deep-faking so that it can be used as evidence in court and, perhaps, as a basis for consensus on "what really happened" in the large variety of missions in which they will soon be deployed.

[1] https://waitbutwhy.com/2020/01/sick-giant.html

## What are you going to build to solve this problem? How is it different from existing solutions? Why is it useful?

As drones become ubiquitous, strict norms of information security will be needed to ensure their reliable operation within tight mission parameters as well as their safe recovery in rapidly arising adverse situations. 

A pipeline, composed of both hardware and software components, will assemble packets of a large range of critical real-time mission data, from aircraft heartbeat to live capture of social upheaval, and transport it safely and securely to the blockchain, currently the only technology which, implementing decentralized consensus, removes the social barriers to mutual trust.

Information security is not a new concept. It has become a central concern and a primary design criterion for many domains, for example IoT, long-range trucking, and the military. This proposal aims to create an information security module for open-source drones.

Such a module will be useful in many scenarios, for example:
(1) Providing proof-of-mission in relief operations in remote regions, where its role can be questioned and contested by various interests.
(2) Providing detailed mission logs for flights in inclement atmospheric conditions and calamities, supplying deep provenance on concomitant attempts to sabotage utilities and public works.
(3) Providing court-level evidence of exact movements of groups and individuals during episodes of social unrest, clashes with police, or racially charged violence.

## How does your solution work? What are the main features? Please specify how you will use the HoverGames Drone Development Kit Coupon Code in your solution.

The critical feature of the security module is to generate globally unique data logs that are provably identified with the drone on which they were produced. In the absence of a off-the-shelf hardware device (say, a quantum dot) that can guarantee that, the solution approximates the feature, by:
(1) Utilizing all unique hardware codes of the drone's devices (e.g. MAC address) to generate unique randomized data sourcing patterns (much in the spirit of OS fingeprinting)
(2) Generating rich sensorium snapshots, especially of unique external events (e.g. atomic clock timestamps, configuration of positioning satellite constellations, range to expected landmarks along the flight path)
(3) Packaging the data payload with snapshots into encrypted packets until they can be logged to the blockchain

The NavQ application SoC is particularly well suited to this heavy computational burden with its multiple ARM cores, its security and crypto subsystems, system control, and on-core multi-media modules. Most of the work for securing the data logs, apart from sourcing from external components (like telemetry feedback, camera(s), GPS, WiFI, SDR, and sensorium) can be done inside the SoC.

The security module will expose an API to the mission developer to specify exactly what data is critical and/or sensitive per the mission objectives. The rest is done by the module in a tamper-proof manner.

The packets written to the blockchain can then be decrypted and read to support the mission objectives, defend the outcome, or otherwise be used as reliable evidence of the drone's actions.

## List the hardware and software you will use to build this.

1. Kit.  
2. NavQ.  
3. Camera with gimbal.  
4. GPS module, preferably 3-constellation and able to output raw signals.  
5. Situational awareness sensorium, including but not limited to altimeter, barometer, and ranging lasers.  
6. TensorFlow for autonomous flight.  
7. WiFi to connect to blockchain over the Internet.  
8. SDR to connect to blockchain over radio.  
9. Any hardware that is required to mount the extra components.  
10. PX4 stack.  
11. Open-source blockchain framework.  
12. Tamper-proof/resistant circuits/devices for critical steps in the secure data pipeline (TBD).  

## Tell us how you'd use your drone and NavQ to prevent and improve crisis management in the future

I will use the drone kit and the advanced application processor to test the operation of the security module and the drone's increased resilience in 3 different (simulated) crisis management scenarios, involving autonomous flight and BVLOS:
1. An emergency delivery of critical medicine at a remote location.  
2. Live recording of a civil unrest event.  
3. Operation in adverse weather conditions with limited connectivity. Drone which can survive or fail gracefully in the case of sabotage, and make reliable reports of their observations and mission parameters may one day be critical in, if not preventing a crisis, at least in not allowing it to escalate and/or propagate.  


## Tell us about yourself. What do you spend most of your time doing? What skills or experience do you have that will enable you to be successful in building this project?

I am Adjunct Professor of Computer Engineering at MSU Denver. I teach at both ends of the curriculum: introduction to the field and senior capstone. I design project-based learning progressions that span large parts of the required curriculum, using the latest developer boards and educational versions of professional computer design and systems development software. This year's senior capstone is building a quadcopter drone from scratch. In addition to the stated project activities and goals, I plan to use the NXP Drone Kit as an advanced testing and teaching platform for the capstone and establish a tradition of excellence in the computer engineering program's culminating experience.

Time commitment: 10
Estimated time required: 130
Purchased hardware: Some
