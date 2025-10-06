---
layout: page
title: Autonomous Shelf Organizer
description: Autonomous In-place Sorting of Items On Shelves SO(n)RT
img: assets/img/mvp2.gif
importance: 1
category: work
related_publications: false
---

## Problem Statement

Devise an end-to-end robotic sortation system to identify shuffled colored physical objects (books, blocks) and sort them "in-place" according to a pre-defined sequence.

**Key Terms:**
- **In-place:** Identify and move objects to "intermediate" locations
- **Manipulate:** Grip objects securely  
- **Pre-defined sequence:** Color-based sorting algorithm

## Solution Overview

The Autonomous Shelf Organizer (SO(n)RT) addresses the challenge of automated organization in cluttered environments. This system combines computer vision, robotic manipulation, and intelligent path planning to autonomously sort and organize items on shelves without human intervention.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/mvp2.gif" title="Autonomous Shelf Organizer demonstration" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Autonomous robotic system demonstrating in-place sorting of colored objects on shelves.
</div>

## Technical Approach

The system employs a multi-stage approach combining:

- **Computer Vision**: Real-time object detection and color classification
- **Path Planning**: Optimal trajectory generation for in-place manipulation
- **Robotic Control**: Precise gripper control for secure object handling
- **State Estimation**: Continuous tracking of object positions and system state

## Key Features

- Autonomous operation without human intervention
- Real-time object recognition and classification
- In-place sorting to minimize workspace disruption
- Robust manipulation of various object shapes and sizes
- Scalable architecture for different shelf configurations
