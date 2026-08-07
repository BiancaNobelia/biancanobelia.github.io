---
title: Passive Haptic Force Display Using Redundant Brake System
description: Developed control strategies for a passive-type haptic device with redundant brakes to improve the quality of force feedback in human–machine interaction.
cover_image: /pictures/plemo_photo_r.jpg
tags: [Haptics, Virtual Reality, Force Control, Kinematics, Brake System, Embedded System]
featured: true
project_type: research
demo_url:
repo_url:
date: 2024-10-01
---

## Research Overview

This research focuses on the development and control of a passive-type planar haptic device using redundant brakes. Unlike motor-driven haptic systems, this device does not actively move the user’s hand. Instead, the user voluntarily moves the handle, while the brakes generate resistive forces to guide the motion.

The main objective of this research is to improve the force-display performance of a passive haptic system, especially in terms of tracking accuracy, force direction accuracy, reaction-force capability, and interaction smoothness.

Because passive systems only dissipate energy, they are generally safer for physical human–robot interaction. This makes the system suitable for applications such as upper-limb rehabilitation, surgical simulation training, and teleoperation.

---

## System Specifications

The system is a 2-DOF planar parallel-link haptic device operated on a tabletop. The handle moves in the X–Y plane, and the user receives force feedback through passive braking resistance.

Key specifications:
- 2-DOF planar parallel-link mechanism
- Passive actuation using 2 powder brakes and 2 powder clutches
- Actuators mounted under the table
- Force sensor mounted at the handle
- 2 encoders used for joint angle measurement
- Real-time control loop at 500 Hz
- Integrated with Unity for virtual environment interaction

The parallel-link mechanism allows the actuators to be mounted under the table while keeping the handle workspace unobstructed and reduce moving inertia

---

## System Architecture

The system consists of three main parts: the mechanical system, the measurement and control system, and the virtual environment.

The mechanical system includes the planar parallel-link mechanism, handle, brakes, clutches, and transmission mechanism. The measurement system uses encoders to calculate the handle position and a force sensor to measure the interaction force. The control system selects the appropriate brake direction and calculates the torque command based on the target trajectory.

The system can also exchange data with Unity in real time, allowing the haptic device to interact with a virtual environment displayed on a monitor or VR headset.

---

## Control Strategies

The main challenge of a passive haptic system is that brakes can only resist motion. Therefore, the displayable force direction is limited compared with motor-driven systems.

To address this issue, this research evaluates several brake activation strategies.

First, a single-brake activation method is used as the baseline. In this method, only one brake direction is selected based on the target motion direction.

Then, dual-brake activation strategies are introduced. Instead of activating only one brake, two brake directions are selected simultaneously. This allows the system to generate a resultant force direction closer to the desired direction.

---

## Unity-Based VR Integration

A Unity-based virtual environment was developed as a proof-of-concept implementation. The haptic device exchanges data with Unity in real time, allowing the virtual object or game environment to respond to the user’s handle motion.

The virtual environment can be displayed on either a monitor or a VR headset. This integration demonstrates the potential of the system for more immersive haptic applications, such as rehabilitation training, simulation, and interactive virtual tasks.

---

## Publication

This work was presented at the **26th Society of Instrument and Control Engineers (SICE) System Integration Division Conference (SI2025)**:

<div class="publication-card">
  <p class="pub-citation"><strong>Surya Nobelia B.</strong>, N. Takesue, and J. Furusho. <strong>Path Following with Passive Haptic Force Display Using Redundant Brake System</strong> — Presented at the 26th SICE System Integration Division Conference (SI2025).</p>
</div>
<div class="publication-card">
  <p class="pub-citation"><strong>Surya Nobelia B.</strong>, N. Takesue, and J. Furusho. <strong>Comparative Evaluation of Single- and Dual-Brake Activation in a Redundant Passive-Type Force Display System</strong> — 2026 IEEE/ASME International Conference on Advanced Intelligent Mechatronics (AIM 2026), Genova, Italy.</p>
</div>
