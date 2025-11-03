---
layout: page
title: Autonomous Shelf Organizer
description: Autonomous In-place Sorting of Items On Shelves SO(n)RT
img: assets/img/mvp2.gif
importance: 1
category: work
related_publications: false
---

<div style="margin-bottom: 2rem; margin-top: 1rem;">
  <style>
    .project-pdf-btn {
      background-color: #0076df;
      color: white !important;
      border: 1px solid #0076df;
      padding: 0.625rem 1.5rem;
      border-radius: 0.375rem;
      text-decoration: none;
      display: inline-block;
      font-weight: 500;
      transition: all 0.2s ease;
      box-shadow: 0 2px 4px rgba(0, 118, 223, 0.2);
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
      margin-right: 0.5rem;
    }
  </style>
  <a href="{{ '/assets/pdf/Autonomy_Project_So_n_rt.pdf' | relative_url }}" target="_blank" rel="noopener noreferrer" class="project-pdf-btn">
    <i class="fa-solid fa-file-pdf"></i> View Full Project Report
  </a>
</div>

## Problem Statement

Develop an end-to-end robotic sortation system to identify shuffled objects (such as books, blocks) and sort them "in-place" without replacement.

**Key Terms:**
- **In-place:** Identify and move objects to intermediate or buffer locations
- **Manipulate:** Grip objects securely and move them safely considering virtual walls and shelf model 
- **Pre-defined sequence:** Color-based sorting algorithm (blue, green, red) → (red, green, blue)

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

## System Architecture

The SO(n)RT system is built on **ROS (Robot Operating System)** and **MoveIt!** for motion planning and control. The architecture integrates multiple subsystems working in harmony:

- **Perception Module**: RGBD camera-based vision system for object detection and localization, updates sequence state in intermediate image retrieval positions
- **Planning Module**: Motion planning using MoveIt! for collision-free trajectory generation from index to index
- **Sortation Module**: Real-time min-swap sortation algorithm 
- **Finite State Machine**: Moves between planning, robot control and sortation states

## Technical Implementation

### Computer Vision

Real-time object detection and segmentation is performed using an RGBD camera mounted on the end-effector. The vision pipeline utilizes **OpenCV** and **HSV color space thresholding** to identify and classify objects by color:

- Input: RGBD camera frames from end-effector camera
- Processing: HSV calibration and thresholding for color-based segmentation
- Output: Centroid information in camera frame for each detected color class 
- Frame Transformation: Camera coordinates transformed to robot base frame for manipulation

The system subscribes to camera frames, processes them in real-time, and provides centroid coordinates for objects of each detected color (blue, green, red) in the camera coordinate frame.

### Sortation Algorithm

- Is a min-swap, cyclic-sort algorithm for any predefined sequence
- Outputs a sequence of move instructions (pick and place indexes) for the control
- Checks camera frame after placing and updates the state of the sequence

### Motion Planning and Control

The system employs **MoveIt!** RRT-Connect for optimal trajectory generation:
- Takes input indexes from the sortation algorithm
- Collision detection considering virtual walls, shelf model and the **books themselves**
- Path planning for reaching, grasping, and placing objects
- **Dynamic replanning** when obstacles are detected
- Grasp objects with simple open/close commands for the Franka
- Defaults to a go-to-pose operation if an optimal plan is not found in upper-bound time

<!-- 
## Results & Achievements

The SO(n)RT system successfully demonstrates:

- Accurate color-based object detection and classification
- Reliable in-place sorting of objects according to pre-defined sequences
- Robust manipulation in constrained shelf environments
- Real-time replanning
- An end-to-end integration of perception, planning, and control subsystems -->

## Technologies & Tools

- **ROS**: Robot Operating System for middleware and communication
- **MoveIt!**: Motion planning framework for trajectory generation
- **OpenCV**: Computer vision library for image processing
- **RGBD Camera**: Depth-enabled vision sensor for 3D perception
- **Python/C++**: Programming languages for system implementation
