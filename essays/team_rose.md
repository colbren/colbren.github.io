---
layout: essay
type: essay
title: "New Mars Rover on the Way!"
date: 2025-05-09
published: True
labels:
  - Embedded Systems
  - ROS
  - Robotics
---

## The Mission: Build a Better Rover  

Every robotics project starts with a bold promise, and for Team Robotic Space Exploration (RoSE), it’s the dream of building a rover that could one day survive the Red Planet. Of course, before you conquer Mars, you need to conquer the field outside the engineering building. This semester, I was deep in the trenches of the Guidance, Navigation, and Control (GNC) subteam, tackling everything from localization and real-time data fusion to software lifecycle management. My job was to make sure our rover not only knew where it was, but could also talk to us clearly, start up cleanly, and keep us in the loop when things went wrong.  

The challenge? Robots don’t like uncertainty, but the real world is full of it. GNSS dropouts, IMU drift, processes that don’t shut down when you tell them to — they all conspire against you. My semester became about finding ways to make the rover more precise, more robust, and a whole lot friendlier to the humans operating it.  

<img width="200px" class="rounded float-start pe-4" src="../img/zed_f9p.png">
<img width="200px" class="rounded float-start pe-4" src="../img/BNO0855_imu.png">
<img width="220px" class="rounded float-start pe-4" src="../img/GNSS_L1L2_Antenna.png">
## When GPS Isn’t Enough  

We started with localization. On paper, RTK GNSS (using the ZED-F9P modules and L1/L2 antennas) promised centimeter-level accuracy — a dream for rover navigation. In practice, satellites hide behind trees, multipath reflections scramble your signals, and suddenly your “precise” position is off by a meter or more. That’s when we realized the rover needed more than just GPS; it needed a second set of eyes.  

Enter the IMU. I fused the ZED-F9P data with readings from our BNO055 IMU using an Extended Kalman Filter running inside ROS2. This was not plug-and-play — it meant carefully tuning process noise, measurement noise, and covariance matrices until the rover’s estimates stopped “drifting into the void.” After a few late nights of field testing (and watching the rover zigzag around like it had too much coffee), we got the fusion working. The result: reliable orientation within ~10° and position accuracy within 10 cm, even during RTK hiccups.  

<img width="200px" class="rounded float-start pe-4" src="../img/lifecycle_flow_model.png">
## Herding ROS2 Nodes  

But localization was just one part of the battle. Our software system had grown into a jungle of ROS2 nodes, each with its own quirks. Shutting them down often meant playing “Ctrl+C roulette,” hoping nothing locked up or corrupted logs. That’s when I discovered ROS2 lifecycle nodes.  

Think of lifecycle nodes as giving your code a set of manners. Instead of barging in and crashing out, they move gracefully between states: unconfigured, inactive, active, and finalized. I refactored some of our most problematic nodes, like the usb_camera running on a Pi, into lifecycle nodes. Now, instead of yanking the plug, we could politely tell a node to pause, restart, or bow out completely. This wasn’t just cleaner — it saved us from countless headaches in the field.  

<img width="200px" class="rounded float-start pe-4" src="../img/ground_station_gui.png">
## A Ground Station That Actually Helps  

Of course, all this backend work doesn’t matter if the human operators are fighting the interface. Our ground station GUI, which I’ve been building in Qt, became my personal playground for usability. This semester, I gave it a launch manager — one button could now spin up an entire ROS2 package instead of forcing students to copy-paste launch commands from a wiki.  

I also added SSH remote launches, letting us control rover-mounted Pis from the GUI. With a couple clicks, we could start camera streams, navigation stacks, or sensor drivers without ever opening a terminal. During testing, this meant less time typing and more time watching the rover actually explore.  

<img width="200px" class="rounded float-start pe-4" src="../img/foxglove_studio.png">
## Seeing Through Foxglove  

Finally, I integrated Foxglove Studio. If RViz feels like old-school cockpit gauges, Foxglove is like slipping on a VR headset: polished, real-time, and built for exploration. By bridging ROS2 topics into Foxglove, we could visualize live camera feeds, GNSS fixes, IMU orientation, and EKF estimates in one dashboard. Debugging went from staring at raw numbers to watching a slick visual replay of the rover’s every move.  

## What I Took Away  

Looking back, this semester was less about any single feature and more about building resilience — for the rover and for myself as an engineer. I learned that real robots don’t care about your perfect simulations; they’ll happily break your assumptions until you design for the messy, unpredictable world they live in.  

I also learned the value of good interfaces, both for humans and machines. A rover that gracefully shuts down its nodes, keeps its operators informed, and delivers trustworthy localization isn’t just technically impressive — it’s usable. And that’s what matters when you’re trying to get a team of stressed-out students through a field test at 2 a.m.  

Next up? Expanding our mission control framework so lifecycle nodes, parameter servers, and the GUI work together like a true ground-to-space system. Because one day, this rover might not just be rolling across a lawn in Hawai‘i — it could be part of something that rolls across Mars.  
