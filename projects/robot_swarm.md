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

I designed and implemented a testbed using AlphaBot2-Pi robots to simulate autonomous satellite swarm coordination, providing a low-cost and flexible platform for validating swarm formation control algorithms before deployment in higher-risk environments. The primary objective of this project was to replicate the challenges of multi-agent coordination—such as maintaining formations, adapting to disturbances, and achieving consensus behaviors—using small ground robots as proxies for satellites. To enable precise real-time tracking, I implemented an Attitude and Heading Reference System (AHRS) with Madgwick filtering and fused Ultra-Wideband (UWB) and IMU data. This approach achieved orientation tracking within 10° and position accuracy within 10 cm, making the platform sufficiently accurate to evaluate swarm control strategies at scale.

My role was to design and program the core localization and control architecture for the robots. I developed the localization stack in Python, handling sensor integration, filtering, and data synchronization, while implementing the swarm controller and formation control algorithm in C++. The system communicated through lightweight UDP protocols, with each robot sending its position and orientation feedback to the central controller for coordinated decision-making. I was responsible for the full software stack—from sensor calibration and data fusion pipelines to control logic and inter-robot communication—ensuring the testbed operated as an integrated, real-time system.

Through this project, I gained firsthand experience in building an end-to-end robotic system that combined perception, communication, and multi-agent control. I learned how to balance accuracy and efficiency in sensor fusion, how to manage distributed system communication with low latency, and how to translate high-level swarm coordination algorithms into real-world implementations. Beyond the technical aspects, the project also taught me the importance of system reliability and repeatability in experimental robotics, as well as the value of designing scalable platforms that can accelerate research in swarm autonomy and cooperative robotics.

You can check out my poster at the [2025 SmallSat Proceedings](https://digitalcommons.usu.edu/smallsat/2025/all2025/73/).
