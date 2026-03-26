---
title: Automatic Guided Vehicle (AGV)
description: Autonomous material transport AGV for warehouse-to-production logistics.
cover_image: /pictures/agv.png
tags: [Pixy camera, NFC, Proximity Sensor, PID Control, Hoverboard Motors, Embedded System]
featured: true
demo_url: https://drive.google.com/file/d/1wfPRd6F6tgYcMVUB-KC_u0ycUEvOx157/view?usp=sharing
repo_url: 
date: 2023-05-01
---

## Project Overview

This AGV autonomously transports materials from the warehouse to the production area. The system is designed for efficient operation and safety in an indoor logistics environment.

<img src="/pictures/agv.png" alt="AGV" style="width:60%; max-width:520px; height:auto;">

## System Description

The AGV operation is built around three key sensing functions:

- **Line Navigation**: Uses a **Pixy Camera** to detect and follow floor guidance lines.
- **Station/Destination Identification**: Uses an **NFC module** to identify stations and trigger stop/operation logic.
- **Safety**: Uses a **proximity sensor** to detect obstacles and prevent collisions.

The system is driven by **hoverboard motors**, providing strong traction and torque suitable for carrying materials.

## Hardware Architecture

### Main Controller
- **Arduino Mega** as the **main controller**
  - Reads sensors (Pixy Camera, NFC, proximity)
  - Executes navigation and station/destination logic
  - Outputs motor command signals and control actions

### Remote Monitoring
- **ESP32** for **remote monitoring**
  - Sends system status information to a remote device/dashboard
  - Useful for operation tracking, debugging, and basic telemetry monitoring

### Sensors
- **Pixy Camera**: line detection and tracking
- **NFC module**: station/destination identification
- **Proximity sensor**: obstacle detection for safety control

### Actuation
- **Hoverboard motors** as the main drive actuators
- Motor control behavior optimized with **PID tuning** for smoother response and stability

## User Interface (HMI)

The AGV includes an on-device interface mounted on the panel:

- **Multiple buttons** for user input (e.g., selection / confirmation / navigation)
- A **small display** on the top area of the panel to **set the destination** before running

This interface allows the operator to quickly set the target station without needing a laptop.

## Mechanical Design

- **Trolley** as a platform to carry the materials to be delivered.
- **3D-printed mounting bracket for the NFC module**, ensuring stable alignment and reliable tag reading
- **Panel design** to house the interface components and wiring organization

<img src="/pictures/agv_circuit.jpg" alt="AGV" style="width:60%; max-width:520px; height:auto;">

## Control & Tuning

### PID Tuning

The AGV control performance was improved by iterative tuning of **PID parameters**, focusing on:

- More stable line-following behavior
- Better response to speed changes and load conditions
- Smooth station starting & stopping behavior

## Integration & Troubleshooting

During integration and testing, several issues were addressed to ensure stable operation:

- Sensor calibration for reliable navigation and consistent detection
- Wiring improvements to reduce noise and prevent intermittent connections
- Mechanical fixes to ensure alignment and stable sensor mounting
- Verification of destination selection workflow through the on-device interface

## Technologies Used

- **Arduino Mega** (main controller)
- **ESP32** (remote monitoring / telemetry)
- **Pixy Camera** (line navigation)
- **NFC module** (station/destination identification)
- **Proximity sensor** (safety)
- **Buttons + small display** (destination selection interface)
- **PID control** (motion/control tuning)
- **Hoverboard motors** (actuation)
- **Mechanical design** (trolley, NFC mount, panel)

## Jobdesk / Contributions

- Analyzed and calibrated the system to ensure proper AGV operation.
- Enhanced AGV features for optimal performance.
- Addressed wiring and mechanical issues during integration.
- Fine-tuned **PID parameters** to optimize control performance.
- Implemented/assisted **ESP32-based remote monitoring** for operational visibility.
- Contributed to **mechanical design** (rack, NFC mounting, and panel/interface layout).

## Video Demo

Video: https://bit.ly/demo_AGV
