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

**Project overview:** I designed and implemented a testbed using AlphaBot2-Pi robots to simulate autonomous satellite swarm coordination, providing a low-cost and flexible platform for validating swarm formation control algorithms prior to deployment in higher-risk environments. The system was intended to replicate multi-agent coordination challenges—such as maintaining geometric formations, adapting to disturbances, and achieving consensus behaviors—using ground robots as stand-ins for spacecraft. To achieve reliable localization, I implemented an Attitude and Heading Reference System (AHRS) with Madgwick filtering and fused Ultra-Wideband (UWB) and IMU data. This approach enabled orientation tracking within 10° and position accuracy within 10 cm, making the testbed sufficiently accurate for evaluating swarm strategies at scale.

**My role & responsibilities:** I was responsible for the design and implementation of the entire software stack that powered the testbed. On the perception side, I developed the localization stack in Python, integrating sensor calibration, fusion, and synchronization pipelines. For control, I programmed the swarm coordination and formation control algorithms in C++, enabling the robots to maintain and adjust formations dynamically. Communication between robots and the central controller was handled via lightweight UDP protocols, with each robot transmitting real-time position and orientation feedback to enable coordinated decision-making. In addition to system integration, I optimized the control loops for responsiveness and robustness, ensuring the swarm could reliably execute formation maneuvers.

**What I learned:** This project gave me end-to-end experience in building a distributed robotic system that combined localization, communication, and multi-agent control. I learned how to design scalable architectures that balance precision and efficiency in sensor fusion, while also managing the challenges of low-latency communication in a multi-robot setup. More broadly, I gained insight into how abstract swarm coordination algorithms can be translated into reliable real-world implementations. The experience reinforced the importance of repeatability and robustness in experimental robotics, while also demonstrating how small-scale testbeds can accelerate research in swarm autonomy and cooperative control for space and terrestrial applications.

You can check out my poster at the [2025 SmallSat Proceedings](https://digitalcommons.usu.edu/smallsat/2025/all2025/73/).
[Source code](https://github.com/interstel-tech/alphabot_swarm).
