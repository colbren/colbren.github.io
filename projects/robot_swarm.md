---
layout: project
type: project
image: img/micromouse/micromouse-square.jpg
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
  <img width="200px" src="../img/micromouse/micromouse-robot.png" class="img-thumbnail" >
  <img width="200px" src="../img/micromouse/micromouse-robot-2.jpg" class="img-thumbnail" >
  <img width="200px" src="../img/micromouse/micromouse-circuit.png" class="img-thumbnail" >
</div>

I created a testbed using AlphaBot2-Pi robots to simulate autonomous satellite swarm coordination, enabling early-stage validation of swarm formation control algorithms. To get accurate movements, postional and orientation feedback, I implemented an AHRS with Madgwick filtering and sensor fused UWB and IMU data, enabling real-time orientation tracking within 10° and position accuracy within 10 cm.

The localization and control for AlphaBot2-Pi robots was developed in python while the swarm controller and formation control algorithm was developed in C++. Position and orientation feedback was sent back to the controller through UDP.

```

You can learn more at the [UH Micromouse News Announcement](https://manoa.hawaii.edu/news/article.php?aId=2857).
