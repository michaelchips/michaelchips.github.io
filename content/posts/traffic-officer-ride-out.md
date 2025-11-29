---
title: My Ride-Out with a National Highways Traffic Officer
date: 2025-11-27
draft: false
tags:
---
![Police park-up point on the M25 by Junction 9](/images/to-rideout/m25-j09-police-parkup.jpg)
I work in the Cyber Security team at National Highways in the UK, I'm enjoying it and everything is going great. However, working for a business that's responsible for critical national infrastructure brings some unexpected benefits, including interesting site visits and experiences! 

This post is about an experience I had recently, which is going on a ride-out with a National Highways Traffic Officer. It's seriously one of the coolest experiences I've had in a long time, so I needed to write about it!
<!--more-->
**_All registrations in images have been redacted to preserve anonymity_**
# What do Traffic Officers do?
The job of a traffic officer is fundamentally to keep the motorways safe and traffic flowing, and to intervene in anything interfering with either or both of those goals. 

Tasks can be dangerous and widely vary, from responding to car crashes and breakdowns, to removing debris or animals in the road and abandoned vehicles, and sometimes even a dark, tragic side of responding to suicidal people in life-threatening situations. They're unique in the way that they are not law enforcement, but possess some powers under the Traffic Management Act 2004 and can exercise them on England's motorways and A roads, in the name of traffic management or road safety. 

They are sometimes mistaken for police, since their vehicles have a similar green checker pattern; my uncle certainly thought they were police when I talked to him about it! Traffic officers are certainly not police though, they can't arrest you or drive faster than the speed limit. They can pull you over, but it's instead called a "safety intervention" and they will only do so for safety reasons (e.g. you're driving for a long time without lights, or something's loose and about to fall off your vehicle into the live lane). They cannot detain you, search you, or issue you fixed penalties. TOs can also direct and stop traffic completely, and it's a criminal offence to disobey their instructions.
# My experience
![Me with a TO vehicle!](/images/to-rideout/self-1.jpg)
I arranged my TO ride-out with the Weatherhill outstation, which is right by junction 9 to Gatwick Airport on the M23. Above is a photo of me standing next to a TO vehicle with a slightly goofy pose because the jacket was too big on me (but very comfy!).

The shift initially starts with patrolling the motorways for anything abnormal. In our patrols, we noticed increased traffic and tried to understand why, reported standing water in live lanes to the control room in the South-East Regional Operations Centre (it was raining heavily that day!), and reported abnormally low speed limits when there wasn't congestion, so that the control room operators could override and reset the signals.

Our first incident we were dispatched to was a vehicle reported to be broken down in lane 4, which is a seriously dangerous position to be in; you're the furthest away from the hard shoulder that you can possibly be! We had to get to this as quickly as possible, so in heavy traffic conditions, we would drive on the hard shoulder with the roof lights on **if it was quicker - _we didn't if it wasn't_**. It's an extremely weird sensation driving normally on the hard shoulder, it's not something you normally do _ever_. The TOs usually keep to a slower speed too rather than going the speed limit, as the hard shoulder is more bumpy than live lanes and people have thrown sharp objects into it such as forks, which can puncture the tyres.

Just before we arrived at the scene, we engaged a rolling road block, which is used to gradually slow traffic in all lanes on a motorway to a stop. The TO waits until the right moment, then switches on a sign on the back of the vehicle that flashes **DON'T PASS**, then starts swerving left to right across all four lanes to stop cars passing while very gradually slowing down. Sitting in the car for this was so weird, it'd be illegal to do this normally! 
![Rolling roadblock in place](/images/to-rideout/m25-rolling-roadblock-1.jpg)
Once traffic comes to a stop, cones are placed down in front of all lanes to prevent traffic from moving forwards and the TO quickly speaks to the vehicles at the front to tell them what's going on. Then the TO drove over to the broken down vehicle and pushed it over to the hard shoulder, so that it was out of a live lane.
![Helping the broken down vehicle](/images/to-rideout/m25-rolling-roadblock-2.jpg)
Once this was done, the TO reversed back to the cones (also very weird to watch, and normally illegal!) and released the traffic one lane at a time. The man with the broken down car arranged his own recovery, so we left him and went on our way.

Next, we had a report from the public of pedestrians walking their dogs right next to where we were on the M25. **Yes, seriously.** I can't believe someone would do that either, but we went to investigate and we found 2 men with 2 large dogs on a walk at the side of the motorway! 

TOs are not obligated to stop and get out and start talking to people, since they are civilians and could be putting themselves into a dangerous situation by doing so. Their job is to confirm the report and continue, then the control rooms will contact the police to deal with it. In this case we pulled over, but stayed inside the car and rolled the window down. This was enough to deter the dog-walkers to start walking up to the bridge and off the motorway, so we left it at that and went on our way. There were no more reports of walking dogs on the motorway afterwards, so we can assume they never returned.

We had a while without any reports, so we positioned ourselves strategically in the middle of the M25 junction 10 roundabout, where we can very quickly rejoin the motorway clockwise or anti-clockwise. I took some more photos here, as not many people have the opportunity to stand where I was!
![M25 Junction 10](/images/to-rideout/m25-j10.jpg)
# Operational Technology
While we were waiting for jobs to come through, I learned more about the different OT systems that National Highways uses on the motorways. I knew about OT from taking IY3612 Critical Infrastructure Security at university, but I had no idea most of these systems on the motorway even existed! OT is an interesting area and could be a whole long blog post in itself, but I'll save that for another day.

Operational Technology, or simply OT, are large-scale systems that are built using technology and interface physically with the real-world in some way; whether that's reading data from sensors, or driving actuators to cause an effect (e.g. change a road sign, open a water dam, spin a nuclear centrifuge, etc). OT is not exclusive to the transport sector and is used in most other critical national infrastructure sectors across the world, including energy, food, water, defence, civil nuclear, space and more, as well as outside of CNI sectors in factories and such. 

You might be thinking OT sounds similar to IT and that they're probably just the same thing. While it's true that they have quite a bit of overlap, particularly that they're technology-driven digital systems with lots of interconnected devices, **OT is a whole different beast to IT**. 

Whereas IT is commonly used in businesses and datacentres, depends on software, servers and TCP/IP networks, and is driven by lots and lots of data; OT is commonly used in factories and critical national infrastucture, depends on **Industrial Control Systems** (ICS) that are made up of **Programmable Logic Controllers** (PLCs), **Supervisory Control and Data Acquisition** (SCADA) systems, **sensors & actuators**, **Distributed Control Systems** (DCS), **Remote Terminal Units** (RTUs) & more, and are important in driving robotics while maintaining safety of human life. 

If all of that sounds completely alien to you, these are just the basics of OT, but they're never taught in schools until you go into working in that industry! 

Anyway, like I said, that's all a post for a different day.

National Highways use a lot of OT in their motorways and the only part of it we notice is the signals & variable message signs. Here's a few (but not all) of the other OT systems that they use:
- **MIDAS | Motorway Incident Detection and Automatic Signalling**  
This system is inside each lane of the road itself and counts the number of vehicles driving over, as well as their speed and length of wheelbase _(so that it can tell the difference between a car and a truck)_, then automatically sets signals to reduce the speed limits if there's heavy traffic, as well as sending information of average speed on that road to the National Traffic Operations Centre (NTOC) so it can be displayed live on [Traffic England](https://www.trafficengland.com/traffic-report). On the road, it looks like a black square inside a black square when driving over it
- **DYNAC**  
This system is an Advanced Traffic Management System (ATMS), which acts as the middleman of all communications between different systems and the control room. It allows operators to view and control the angle & zoom CCTV cameras, as well as view data from MIDAS and weather sensors, set signals to reduce speed limits or divert/close lanes, set messages on variable message signs and more.
- **SVD | Stopped Vehicle Detection**  
This system uses thousands of radars along all the motorways in England to immediately detect stopped vehicles in live lanes and on hard shoulders, alerting operators in control rooms so that they can dispatch a traffic officer if assistance is required

**Quick note on the security angle of OT:** OT is totally hackable and vulnerable to attacks, but requires very different methods to conventional hacking, such as interfering with sensors by physically blocking them or messing with how they're calibrated to read data, or interfering with actuators physically or through signals to make them do unsafe things. Usually these sensors and actuators are physically in difficult-to-reach places, making attacks impractical, but not impossible. Malware is the other alternative, but this isn't straightforward since OT environments usually aren't connected to the Internet, and the malware author will require in-depth knowledge of different industrial controllers to be able to send the right signals through the right busses and channels to achieve their goals.

If you're interested in learning more about cyber attacks on OT (for educational purposes), I'd recommend you to listen to Darknet Diaries Episode 29: Stuxnet for the notorious Stuxnet attack on Iran's nuclear facilities, and Episode 68: Triton, for the crazy hack that targeted disabling the safety systems in a Saudi Arabian chemical plant to allow hazardous conditions that could lead to explosions or loss of human life. It's worth a listen!
# My experience (continued)
After deterring the dog-walkers to leave the motorway and then parking up for a while, we were waiting for a bit and no new jobs were coming in, so we went to visit the control room at the South-East Regional Operations Centre (SE ROC) in South Godstone. This is where the operators view the CCTV cameras, check out alerts generated by SVD when a car stops in a live lane, dispatch traffic officers, answer calls from the SOS telephones and more. Speaking to some of the operators and watching what they do was interesting, however since the weather conditions were pretty bad, I was watching emergency services live dealing with a 4-car collision and a flipped over vehicle on two of the CCTV cameras. This wasn't nice to see, but that feeling pales in comparison to being involved in either of the incidents.

On the CCTV cameras, we also saw multiple trucks parked on the hard shoulder right before Clackett's Lane services (between Junction 5 and 6 on the M25), which is a super dangerous place to park. So, we spoke with the bronze commander of the control room and decided we would drive over, since we were so close already. 

We headed over and instructed them to leave, which all of them were on their break and were hesitant. My guess is they parked on the hard shoulder rather than the services because they wanted to avoid paying for parking, which I appreciate is expensive, but equally the hard shoulder is really unsafe! 

Traffic officers cannot force them to move off the hard shoulder, but they can involve the police if the truck drivers don't move. In the end, they all moved off the hard shoulder, and we went back to patrolling. No other jobs came through for the rest of the evening, but I was shown some of the police park-up points while we patrolled around, which was cool, since they're normally illegal to be in, but we were allowed in them! The photo at the top of this post was taken at the park-up point by the Leatherhead Junction 9 slip road, but we also visited the turn-around point at the end of the M23, shown below. It felt very weird to be standing here on the motorway!
![M23 Turnaround Point](/images/to-rideout/m23-j7-turnaround-point.jpg)
This was the end of my experience of going out on a ride-out with a traffic officer. A big thank you to Madeline for allowing me to join her on a shift and making the ride-out really interesting, and to the Weatherhill outstation for accommodating me. I really enjoyed this experience and learned a lot, and I hope you found this post an interesting read!