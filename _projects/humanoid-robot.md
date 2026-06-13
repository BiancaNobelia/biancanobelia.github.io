---
title: Balance Control System on Humanoid Dance Robot
description: Implemented a closed-loop balance controller for the 29-DoF ERISA humanoid dance robot using IMU-based pitch feedback, Five-Link GCoM analysis, and PD control. 
cover_image: /pictures/erisa.png
tags: [Humanoid Robot, Balance Control, Center of Mass, Five-Link Model, IMU, PD Control]
featured: true
project_type: research
demo_url: https://drive.google.com/file/d/1drUpkeuI3ltxFOQcgkm4NRpHqynZThlo/view?usp=sharing
repo_url:
date: 2022-01-13
---

## Research Overview

This research focused on implementing a **balance control system** for the **ERISA humanoid dance robot**, used in the **Indonesian Dance Robot Contest (KRSTI)**. In KRSTI, robot stability is a key scoring factor — each zone involves different dance motions and transitions that can easily cause a robot to fall.

To stabilize ERISA under dynamic conditions, I implemented a **closed-loop PD controller** using **pitch feedback** from an IMU sensor, supported by a **Ground Projection of Center of Mass (GCoM)** analysis based on a simplified **Five-Link model**.

---

## Robot Specifications

ERISA (EEPIS Robot Intelligent Sense of Art) is a full-body humanoid robot designed for Indonesian traditional dance performance.

- **Degrees of Freedom**: 29 DoF
- **Actuators** (4 types):
  - Dynamixel **MX-28** & **AX-12A**
  - Hitec **HS-85MG** & **HS-5055MG**
- **Main Controller**: STM32F407VGT6
- **Balance Sensor**: IMU GY-952

---

## System Architecture

### 1) IMU Measurement & Data Processing (GY-952)
- Provides **Euler angles** (roll, pitch, yaw) via **UART/USART**, parsed from binary frames.
- **Sensor calibration** is performed at startup to establish a stable reference.
- Accuracy testing showed low average error (≈ **1.88%** on positive tilt, **2.49%** on negative tilt), confirming suitability for feedback control.

### 2) Motion Planning
- **Forward Kinematics** is used for hand motion — computing end-effector positions from joint angles to generate expressive arm movements.
- **Inverse Kinematics** is used for leg motion — computing the required joint angles from desired foot positions to achieve stable and coordinated steps.

### 3) Stability Variable: GCoM (Ground Projection of CoM)
The humanoid body is simplified into a **Five-Link model** on the sagittal plane — trunk, left thigh, left calf, right thigh, and right calf — where each link has a defined length, mass, and CoM location. Pitch angle comes from the IMU; leg joint angles come from the current servo posture.

The control objective is to keep the **GCoM inside the support polygon** to prevent the robot from falling.

---

## Balance Recovery Strategy

Two recovery strategies are used depending on the magnitude of the disturbance:

### 1) Ankle Strategy (small disturbances)
Corrects posture through ankle-related joints to maintain GCoM stability. Used when the disturbance is small.

### 2) Ankle–Hip Strategy (large disturbances)
Combines ankle correction with a hip-based reaction to generate stronger stabilization torque. Used when stepping onto an obstacle or during large perturbations.

### Strategy Selection (Threshold-Based)
A threshold determined empirically decides the active strategy:
- GCoM / pitch error **within safe range** → Ankle Strategy
- GCoM / pitch error **exceeds threshold** → Ankle–Hip Strategy

This prevents overreacting to small disturbances while still handling large ones robustly.

---

## Control Design (Closed-Loop PD)

ERISA originally operates as an open-loop motion robot (trajectory + servo commands). To improve stability, I added a **closed-loop PD controller**:

- **Error**: pitch deviation from the IMU reference
- **P term**: fast correction toward the reference
- **D term**: damps oscillation and overshooting

---

## Experiments & Results

The system was evaluated under three challenging conditions:

1. **Dancing while walking**
2. **Dancing while lifting one leg**
3. **Dancing while stepping onto a small obstacle**

### Key Outcomes
- Without balance control, ERISA becomes unstable and can fall during transitions.
- The **Ankle Strategy** improves stability for walking and single-leg motions but may fail under larger disturbances.
- The **Ankle–Hip Strategy** provides the most robust stabilization across all tested conditions, including obstacle stepping.
- Forward and inverse kinematics enable **smooth, coordinated dance motion** across all limbs.

Overall, the balance controller successfully **expanded the motion boundary** of ERISA, allowing it to complete dance motions more safely and consistently.

---

## Technologies Used
- **Embedded**: STM32F407VGT6, UART/USART, real-time frame parsing
- **Sensor**: IMU GY-952 (Euler angle output)
- **CAD / Design**: Autodesk Inventor
- **Actuators**: Dynamixel MX-28 / AX-12A, Hitec servos
- **Control**: PD control, threshold-based strategy switching
- **Kinematics**: Forward kinematics (hand motion), Inverse kinematics (leg motion)
- **Modeling**: Five-Link humanoid simplification, GCoM computation
- **Tools**: STM32CubeIDE

---

## Video Demo

<div class="video-embed">
  <iframe src="https://drive.google.com/file/d/1NcwU1lSWGeTwTKeA4bzw9BXevBlp87dB/preview" allowfullscreen></iframe>
</div>

---

## Publication

This work was published at the **5th International Conference on Applied Science and Technology on Engineering Science (iCAST-ES 2022)**:

<div class="publication-card">
  <p class="pub-citation">Surya Nobelia B., Satria N., Henfri Binugroho E. and Fatahillah T. (2022). <strong>Analysis of Stability on the ERISA Humanoid Dance Robot.</strong> In <em>Proceedings of the 5th International Conference on Applied Science and Technology on Engineering Science</em>, Volume 1: iCAST-ES. SciTePress, pages 182–187.</p>
  <a class="pub-doi" href="https://doi.org/10.5220/0011738400003575" target="_blank" rel="noopener">DOI: 10.5220/0011738400003575 →</a>
</div>