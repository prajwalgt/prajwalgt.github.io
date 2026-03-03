---
layout: page
title: Steerable Imitation Learning Under Perturbations
description: Generate smooth walking motions for the robot to mimic and use it to steer it in any direction and under forces!
img: assets/img/mimic_main.gif
importance: 3
category: work
giscus_comments: false
---

## Skills

Reinforcement Learning, Adversarial Imitation Learning, Deep Learning, Curriculum Learning, Motion Retargeting  
**Frameworks:** Isaac Gym, PyTorch 
**Methods:** AMP, ADD, Humanoid Control, Force Robustness

## Summary

Can adversarial motion imitation methods produce humanoid locomotion policies that remain stable under external force perturbations? What if there is an additional reward for tracking user input velocity vector? This project focuses on answering these questions. Using the Unitree G1 in Isaac Gym, we compared Adversarial Motion Priors (AMP) and Adversarial Differential Discriminators (ADD) under curriculum-based wrist forces simulating box carrying. ADD is further extended with steering objectives to enable directional control. Results reveal a clear trade-off: ADD learns faster and is more force-robust, while AMP produces higher motion fidelity but degrades under sustained disturbance.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/mimic_main.gif" title="Steerable Imitation Learning demonstration" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Humanoid locomotion policy demonstrating robust motion under external forces and steerable control.
</div>

<div style="margin-top: 2rem; margin-bottom: 2rem; text-align: center;">
  <style>
    .project-pdf-btn {
      background-color: #0076df;
      color: white !important;
      border: 1px solid #0076df;
      padding: 0.4rem 1rem;
      border-radius: 0.375rem;
      text-decoration: none;
      display: inline-block;
      font-weight: 500;
      font-size: 0.875rem;
      transition: all 0.2s ease;
      box-shadow: 0 2px 4px rgba(0, 118, 223, 0.2);
      margin-right: 0.75rem;
    }
    .project-pdf-btn:hover {
      background-color: #0056b3;
      border-color: #0056b3;
      color: white !important;
      text-decoration: none;
      box-shadow: 0 4px 8px rgba(0, 118, 223, 0.3);
      transform: translateY(-1px);
    }
    .project-pdf-btn i {
      margin-right: 0.4rem;
    }
    .project-slides-btn {
      background-color: #28a745;
      color: white !important;
      border: 1px solid #28a745;
      padding: 0.4rem 1rem;
      border-radius: 0.375rem;
      text-decoration: none;
      display: inline-block;
      font-weight: 500;
      font-size: 0.875rem;
      transition: all 0.2s ease;
      box-shadow: 0 2px 4px rgba(40, 167, 69, 0.2);
    }
    .project-slides-btn:hover {
      background-color: #218838;
      border-color: #218838;
      color: white !important;
      text-decoration: none;
      box-shadow: 0 4px 8px rgba(40, 167, 69, 0.3);
      transform: translateY(-1px);
    }
    .project-slides-btn i {
      margin-right: 0.4rem;
    }
    .project-github-btn {
      background-color: #24292e;
      color: white !important;
      border: 1px solid #24292e;
      padding: 0.4rem 1rem;
      border-radius: 0.375rem;
      text-decoration: none;
      display: inline-block;
      font-weight: 500;
      font-size: 0.875rem;
      transition: all 0.2s ease;
      box-shadow: 0 2px 4px rgba(36, 41, 46, 0.2);
      margin-left: 0.75rem;
    }
    .project-github-btn:hover {
      background-color: #1a1e22;
      border-color: #1a1e22;
      color: white !important;
      text-decoration: none;
      box-shadow: 0 4px 8px rgba(36, 41, 46, 0.3);
      transform: translateY(-1px);
    }
    .project-github-btn i {
      margin-right: 0.4rem;
    }
  </style>
  <a href="{{ '/assets/pdf/DRL_Final_Report.pdf' | relative_url }}" target="_blank" rel="noopener noreferrer" class="project-pdf-btn">
    <i class="fa-solid fa-file-pdf"></i> Project Report
  </a>
  <a href="https://docs.google.com/presentation/d/1KYFqbJqRxeiqFmAPC8PQSfPxVrWBsPSLfSmQA5c-EeM/edit?usp=sharing" target="_blank" rel="noopener noreferrer" class="project-slides-btn">
    <i class="fa-solid fa-file-powerpoint"></i> Slides
  </a>
  <a href="https://github.com/mhon-emma/MimicKit_CMU_MAP/tree/emma" target="_blank" rel="noopener noreferrer" class="project-github-btn">
    <i class="fa-brands fa-github"></i> GitHub
  </a>
</div>

## Problem Motivation

Motion imitation produces impressive gaits in simulation, but reward tuning is tedious to achieve this smoothness. Moreover, policies need to be robust under real-world forces.

## Contribution

- Motion retargeting pipeline (AMASS, LAFAN → Unitree G1 kinematics)
- Custom box-carrying dataset generation with force
- Force curriculum learning framework
- AMP vs ADD adversarial discriminator comparison
- Steerable ADD policy with velocity and heading rewards
- PPO training with 4096 parallel Isaac Gym environments

**Scale:** 2–3B samples, RTX 4090, 15–20 GPU hours per training run.

## Key Technical Insights

### Insight: ADD vs AMP Tradeoff

ADD optimizes faster and tolerates disturbance better due to differential discrimination, while AMP preserves motion style but struggles with root drift under sustained perturbations. This fundamental difference stems from ADD's explicit tracking of pose differences rather than absolute pose matching.

## Quantitative Results

| Method | Force Curriculum | Episode Length | Body Pos Error |
|--------|-----------------|----------------|----------------|
| ADD    | [10,10,30]      | 260.5s         | 0.015          |
| AMP    | [10,10,30]      | 265.2s         | 0.045          |

ADD maintains lower body position error under force due to explicit differential tracking, enabling longer stable rollouts.

## Steerable Policy Extension

We extended ADD with velocity and heading rewards for directional control. The policy successfully tracked commanded velocities but required some reward balancing to preserve motion style. This demonstrates the challenge of multi-objective optimization in imitation learning, where style preservation and task performance must be carefully balanced.

## Engineering Takeaways

This project demonstrates:

- **Systems Design:** Built force curriculum learning framework with progressive difficulty scheduling
- **Algorithm Analysis:** Diagnosed discriminator behavior differences between AMP and ADD architectures
- **Scalable Infrastructure:** Implemented RL pipeline in Isaac Gym with 4096 parallel environments
- **Failure Analysis:** Identified overcompensation failure modes through qualitative analysis
- **Problem Solving:** Proposed curriculum and objective scheduling fixes based on empirical findings
