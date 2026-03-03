---
layout: page
title: Humanoid Manipulation with Vision-Language-Action Model
description: CMU MRSD Capstone Project (Fall 2025), sponsored by Nissan and Field AI
img: assets/img/groot.gif
importance: 1
category: work
---

**CMU MRSD Capstone Project (Fall 2025), sponsored by [Nissan](https://www.nissan-global.com/EN/INNOVATION/TECHNOLOGY/ADVANCED_TECH_CENTER/) and [Field AI](https://www.fieldai.com/)**  
**Advised by [Prof. Guanya Shi](https://www.gshi.me/)**  
View the [project website](https://mrsdprojects.ri.cmu.edu/2025teamf/)

## Skills

Computer Vision, Point Clouds, Robot Foundation Models, Vision-Language-Action Models  
**Frameworks:** PyTorch, PyTorch 3D, MuJoCo, PCL, Open3D, Apple Vision Pro, Rerun

Collected 800+ high-quality tele-operated manipulation data on the Unitree G1 robot using Apple Vision Pro and a custom built data teleoperation and collection pipeline. LoRA fine-tuned NVIDIA GR00T N1.5 and deployed the policy. Developed and benchmarked other diffusion policies with modality (point-cloud perception) and architecture (DDPM and ACT) changes with a focus on latency and reliability.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/groot.gif" title="Project demonstration" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    GR00T N1.5 VLA on the Unitree G1 performing box manipulation.
</div>

## Project Poster

<div style="margin-top: 2rem; margin-bottom: 2rem;">
  <style>
    .poster-iframe {
      width: 100%;
      height: 600px;
      border: 1px solid #ddd;
      border-radius: 0.375rem;
      box-shadow: 0 2px 4px rgba(0,0,0,0.1);
      max-width: 100%;
    }
    @media (max-width: 768px) {
      .poster-iframe {
        height: 400px;
      }
    }
    @media (max-width: 576px) {
      .poster-iframe {
        height: 300px;
      }
    }
  </style>
  <iframe src="{{ '/assets/pdf/TeamF_Poster.pdf' | relative_url }}" class="poster-iframe" allowfullscreen></iframe>
  <div style="margin-top: 1rem; text-align: center;">
    <a href="{{ '/assets/pdf/TeamF_Poster.pdf' | relative_url }}" target="_blank" rel="noopener noreferrer" style="color: #0076df; text-decoration: none;">
      <i class="fa-solid fa-download"></i> Download PDF
    </a>
  </div>
</div>