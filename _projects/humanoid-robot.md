---
title: Balance Control System on ERISA Humanoid Dance Robot (GCoM-based Analysis)
description: Implemented a closed-loop balance controller for the 29-DoF ERISA humanoid dance robot using IMU-based pitch feedback, Five-Link GCoM analysis, and PD control. The system selects ankle or ankle–hip strategy based on a threshold to keep stability during walking, one-leg motions, and stepping onto small obstacles.
cover_image: /assets/images/projects/dynamic_walking_1.png
tags: [Humanoid Robot, ERISA, Balance Control, GCoM, Center of Mass, Five-Link Model, IMU, GY-952, PD Control, Ankle Strategy, Hip Strategy, STM32, Dynamixel, Robotics]
featured: true
project_type: Research
demo_url:
repo_url:
date: 2022-01-13
---

## Project Overview

This project focused on implementing a **balance control system** for the **ERISA humanoid dance robot** used in **Indonesian Dance Robot Contest (KRSTI)**. In KRSTI, robot stability is a key scoring factor because each zone contains different dance motions and transitions that can easily cause the robot to fall.

To stabilize ERISA during **dancing while walking**, **lifting one leg**, and **stepping onto an obstacle**, I implemented a **closed-loop PD controller** using **pitch feedback** from an IMU sensor, supported by a **Ground Projection of Center of Mass (GCoM)** analysis using a simplified **Five-Link model**.

---

## Robot Specifications (ERISA)

ERISA (EEPIS Robot Intelligent Sense of Art) is a full-body humanoid robot designed for traditional dance performance.

- **Degrees of Freedom**: **29 DoF**
- **Actuators** (4 types):
  - Dynamixel **MX-28**
  - Dynamixel **AX-12A**
  - Hitec **HS-85MG**
  - Hitec **HS-5055MG**
- **Main controller**: **STM32F407VGT6**
- **Balance sensor**: **IMU GY-952** (Euler angle output: roll/pitch/yaw)
- **Balance axis used**: **Pitch** (front–back), because ERISA most frequently falls forward/backward.

---

## System Architecture

### 1) IMU Measurement & Data Processing (GY-952)
- The IMU provides **Euler angles** (roll, pitch, yaw).
- Data is read via **UART/USART** and parsed from binary frames.
- The system performs **sensor calibration** at startup to set a stable reference.
- IMU accuracy testing showed low average error (≈ **1.88%** on positive tilt and **2.49%** on negative tilt), supporting its use for feedback control.

### 2) Stability Variable: GCoM (Ground Projection of CoM)
To represent robot stability with a simple but meaningful model, the humanoid body was simplified into a **Five-Link model** on the sagittal plane:

- trunk, left thigh, left calf, right thigh, right calf  
- each link has: length, mass, CoM location  
- **pitch angle** comes from IMU, while leg joint angles come from the current servo posture.

The control objective is to keep **GCoM inside the support polygon** to prevent falling.

---

## Mathematical Approach (Five-Link GCoM)

The GCoM is computed by projecting each link’s CoM onto the ground direction and taking a mass-weighted average:

\[
GCoM = \frac{\sum m_i x_i}{\sum m_i}
\]

Where each \(x_i\) is the projected position of each link’s CoM (computed from link geometry and joint angles). The pitch angle from IMU is included in the projection so the estimation reflects real body tilt, not only joint posture.

This GCoM value is used as a **stability indicator** and also as a basis for deciding which strategy should be applied.

---

## Balance Recovery Strategy

This project uses **two recovery strategies**:

### 1) Ankle Strategy (small disturbances)
Used when the disturbance is small. The controller mainly corrects posture through ankle-related joints to keep GCoM stable.

### 2) Ankle–Hip Strategy (large disturbances)
Used when the disturbance is larger (e.g., stepping onto an obstacle). This combines ankle correction with a hip-based reaction to generate stronger stabilization torque and reduce falling risk.

### Strategy Selection (Threshold-Based)
A threshold is determined empirically:
- If the stability variable (GCoM / pitch error) is within the “safe” range → **Ankle Strategy**
- If it exceeds the threshold → **Ankle–Hip Strategy**

This prevents overreacting to small disturbances while still handling large disturbances robustly.

---

## Control Design (Closed-Loop PD)

ERISA originally behaves like an open-loop motion robot (trajectory + servo commands). To improve stability, I implemented **closed-loop PD control**:

- **Error**: pitch deviation from IMU reference  
- **Controller**: PD (P for fast correction, D to damp oscillation)
- **Reason PD (not PID)**: motion disturbance during dance is fast/fluctuating; the integral term is not essential and can slow response.

### Tuned Gains (From Experiments)

**Ankle Strategy (best gains):**
- **Kp = 2.25**
- **Kd = 0.125**

**Hip Strategy (best gains in ankle–hip mode):**
- **Kp = 6**
- **Kd = 4**

These values were selected based on stability/oscillation comparisons across multiple tests.

---

## Experiments & Results

The system was evaluated under 3 challenging conditions:

1. **Dancing while walking**
2. **Dancing while lifting one leg**
3. **Dancing while stepping onto an obstacle (small height)**

### Key outcomes
- Without balance control, ERISA easily becomes unstable and can fall during transitions.
- **Ankle Strategy** improves stability for walking and one-leg motions, but can fail under larger disturbances.
- **Ankle–Hip Strategy** provides the most robust stabilization across all tested conditions, including obstacle stepping.

Overall, the balance controller successfully **expanded the motion boundary** of ERISA so it can complete dance motions more safely and consistently.

---

## Technologies Used
- **Embedded**: STM32F407VGT6, UART/USART, real-time parsing
- **Sensor**: IMU **GY-952** (Euler angle output)
- **Actuators**: Dynamixel MX-28 / AX-12A, Hitec servos
- **Control**: PD control, threshold-based strategy switching
- **Modeling**: Five-Link humanoid simplification, GCoM computation
- **Tools**: STM32CubeIDE

---