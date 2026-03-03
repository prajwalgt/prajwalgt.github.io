---
layout: page
title: Autonomous Humanoid Loco-Manipulation for Tote Logistics
description: CMU MRSD Capstone Project, sponsored by Nissan and Field AI
img: assets/img/capstone_uncompressed.gif
importance: 1
category: work
---

**CMU MRSD Capstone Project, sponsored by [Nissan](https://www.nissan-global.com/EN/INNOVATION/TECHNOLOGY/ADVANCED_TECH_CENTER/) and [Field AI](https://www.fieldai.com/)**  
**Advised by [Prof. Guanya Shi](https://www.gshi.me/)**  
View the [project website](https://mrsdprojects.ri.cmu.edu/2025teamf/)

## Skills

Computer Vision, Reinforcement Learning and Control, Motion Planning, Systems Engineering (Finite State Machine)  
**Frameworks:** Isaac Sim & Isaac Gym, PyTorch, MuJoCo, TensorRT, FastDDS

Developed the autonomy stack, specifically the perception for 6D pose estimation (NVIDIA FoundationPose) with motion-capture localization for precise perception and navigation. Combined the high-level planner with perception and humanoid control, trained in simulation with curriculum-based PPO.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/capstone_uncompressed.gif" title="Project demonstration" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Autonomous humanoid robot demonstrating tote manipulation capabilities.
</div>

## Project Poster

<div style="margin-top: 2rem; margin-bottom: 2rem;">
  <iframe src="{{ '/assets/pdf/TeamF_Poster.pdf' | relative_url }}" width="100%" height="800px" style="border: 1px solid #ddd; border-radius: 0.375rem; box-shadow: 0 2px 4px rgba(0,0,0,0.1);"></iframe>
  <div style="margin-top: 1rem; text-align: center;">
    <a href="{{ '/assets/pdf/TeamF_Poster.pdf' | relative_url }}" target="_blank" rel="noopener noreferrer" style="color: #0076df; text-decoration: none;">
      <i class="fa-solid fa-download"></i> Download PDF
    </a>
  </div>
</div>