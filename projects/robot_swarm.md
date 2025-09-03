---
layout: project
type: project
image: img/robot_swarm.JPG
title: "Robot Swarm"
date: 2025-01-13
published: true
labels:
  - Robotics
  - Python
  - Raspberry Pi
  - C++
summary: "I developed a test platform using physical robots to test swarm satellite formation control algorithms that was published at the 2025 Small Satellite Conference."
---

<div class="text-center p-4">
  <img width="1000px" src="../img/robot_swarm_poster.jpg" class="img-thumbnail" >
</div>

I created a testbed using AlphaBot2-Pi robots to simulate autonomous satellite swarm coordination, enabling early-stage validation of swarm formation control algorithms. To get accurate movements, postional and orientation feedback, I implemented an AHRS with Madgwick filtering and sensor fused UWB and IMU data, enabling real-time orientation tracking within 10° and position accuracy within 10 cm.

The localization and control for AlphaBot2-Pi robots was developed in python while the swarm controller and formation control algorithm was developed in C++. Position and orientation feedback was sent back to the controller through UDP.

You can check out my poster at the [2025 SmallSat Proceedings](https://digitalcommons.usu.edu/smallsat/2025/all2025/73/).
