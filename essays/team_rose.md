---
layout: essay
type: essay
title: "New Mars Rover on the Way!"
date: 2025-05-09
published: False
labels:
  - Embedded Systems
  - ROS
  - Robotics
---

## The Mission: Build a Better Rover  

Every project starts with a bold promise, and for Team Robotic Space Exploration (RoSE), we planned on building a rover that could simulate real Mars missions. This semester, I was deep in the trenches of the Guidance, Navigation, and Control (GNC) subteam, tackling everything from localization and real-time data fusion to software lifecycle management. My job was to make sure our rover not only knew where it was, but could also talk to us clearly, start up cleanly, and keep us in the loop when things went wrong. 

Our main challenge was to deal with all the issues associated with the uncertainty of the real world. When testing whether it be GNSS dropouts, IMU drift, processes that don’t shut down, caued this semester to become about finding ways to make the rover more precise, more robust for those operating it.  

<img width="200px" class="rounded float-start pe-4" src="../img/zed_f9p.png">
<img width="200px" class="rounded float-start pe-4" src="../img/BNO0855_imu.png">
<img width="220px" class="rounded float-start pe-4" src="../img/GNSS_L1L2_Antenna.png">
## When GPS Isn’t Enough  

We started with localization. On paper, RTK GNSS (using the ZED-F9P modules and L1/L2 antennas) promised centimeter-level accuracy which would be critical for rover navigation. In practice, satellites can be obscured casuing a scramble your signals, and suddenly your “precise” position is off by a meter or more. That’s when we realized the rover needed more than just GPS.  

Enter the IMU. I fused the ZED-F9P data with readings from our BNO055 IMU using an Extended Kalman Filter running inside ROS2. Through carefully tuning process noise, measurement noise, and covariance matrices until the rover’s estimates stopped drifting significantly. After a few late nights of field testing, we got the fusion working leading to reliable orientation and position accuracy within 10 cm.  

<img width="200px" class="rounded float-start pe-4" src="../img/lifecycle_flow_model.png">
## Herding ROS2 Nodes  

Localization was just one part of the battle. Our software system had grown into a plentiful number of ROS2 nodes, each with its own purpose. Shutting them down often meant pressing Ctrl+C on every terminal, hoping nothing locked up or corrupted logs. That’s when I discovered ROS2 lifecycle nodes.  

Think of lifecycle nodes as giving your code a state to be in causing graceful movement between states: unconfigured, inactive, active, and finalized. I refactored most of our nodes, like the usb_camera running on a Pi, into lifecycle nodes. Now, instead of having dead nodes alive publishing no data, we could easily tell a node to pause, restart, or turn off completely to make our data cleaner and easier to manage.  

<img width="200px" class="rounded float-start pe-4" src="../img/ground_station_gui.png">
## A Ground Station That Actually Helps  

Of course, all this backend work doesn’t matter if the human operators did not know how to properly use the software. Our ground station GUI, which I’ve been building in Qt, became my personal playground. This semester, I gave it a launch manager which was just one button that could launch all ROS2 packages instead of having to copy-paste launch commands off a doc.  

I also added SSH remote launches, letting us control rover-mounted Pis from the GUI which was used for some of our hardware like our cameras. With a couple clicks, we could start camera streams, navigation stacks, or sensor drivers without ever opening a terminal. During testing, this meant less time typing and more time watching the rover actually explore. We could easily tell our rovers state and what needed fixing on the software side. 

<img width="200px" class="rounded float-start pe-4" src="../img/foxglove_studio.png">
## Seeing Through Foxglove  

Finally, I integrated Foxglove Studio. Foxglove Studio allowed me to bridge ROS2 topics, allowing us to visualize live camera feeds, GNSS fixes, IMU orientation, and EKF estimates in one dashboard. It was an easy implementation to have live data in another application to declutter the actual ground station interface.

## What I Took Away  

Looking back, this semester was less about any single feature and more about building resilience for the rover and for myself as an engineer. I learned that you will inevitably run into countless issues when working on complex engineering projects. I could not count the amount of times I thought software implementations ran into issues that set back development by weeks and even months.

I also learned the value of good interfaces and communication, both for humans and machines. A rover that gracefully shuts down its nodes, knows exactly what state it is in, and properly gets data using dual band antennas allows for trustworthy localization. As an engineer, working on a project forces you to bounce back ideas with others and often communicate issues between subteams. Failure to do so will not only make the project set further back, but will also demotivate your team. I hope to expand our mission control framework and improve out localization and path planning for better autonomous navigation. 
