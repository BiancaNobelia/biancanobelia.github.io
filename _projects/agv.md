---
title: Automatic Guided Vehicle (AGV)
description: Autonomous material transport AGV for warehouse-to-production logistics.
cover_image: /pictures/agv.png
tags: [Pixy camera, NFC, Proximity Sensor, PID Control, Hoverboard Motors, Embedded System]
featured: true
project_type: full-time
demo_url: https://drive.google.com/file/d/1wfPRd6F6tgYcMVUB-KC_u0ycUEvOx157/view?usp=sharing
repo_url: 
date: 2023-05-01
gallery:
  - image: /pictures/agv.png
    caption: AGV Unit
  - image: /pictures/agv_circuit.jpg
    caption: Electrical Panel & Wiring
---

## Project Overview

This AGV autonomously transports materials from the warehouse to the production area. The system is designed for efficient operation and safety in an indoor logistics environment.

---

## System Description

The AGV is built around three core sensing functions:

<table class="project-table">
  <thead>
    <tr>
      <th>Function</th>
      <th>Sensor</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Line Navigation</td>
      <td>Pixy Camera</td>
      <td>Detects and follows floor guidance lines</td>
    </tr>
    <tr>
      <td>Station Identification</td>
      <td>NFC Module</td>
      <td>Identifies stations and triggers stop/operation logic</td>
    </tr>
    <tr>
      <td>Obstacle Safety</td>
      <td>Proximity Sensor</td>
      <td>Detects obstacles and prevents collisions</td>
    </tr>
  </tbody>
</table>

The system is driven by **hoverboard motors**, providing strong traction and torque suitable for carrying materials.

---

## Hardware Architecture

<table class="project-table">
  <thead>
    <tr>
      <th>Component</th>
      <th>Role</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Arduino Mega</td>
      <td>Main controller</td>
    </tr>
    <tr>
      <td>ESP32</td>
      <td>Remote monitoring</td>
    </tr>
    <tr>
      <td>Pixy Camera</td>
      <td>Line detection and tracking</td>
    </tr>
    <tr>
      <td>NFC Module</td>
      <td>Station/destination identification</td>
    </tr>
    <tr>
      <td>Proximity Sensor</td>
      <td>Obstacle detection</td>
    </tr>
    <tr>
      <td>LiPo Battery</td>
      <td>Power supply</td>
    </tr>
    <tr>
      <td>Hoverboard Motors</td>
      <td>Main drive actuators</td>
    </tr>
  </tbody>
</table>

---

## User Interface

The AGV includes an on-device interface mounted on the panel:
- **Buttons** for user input (selection, confirmation, navigation)
- **Small display** to set the destination before running

---

## Mechanical Design

- **Trolley** platform for carrying delivered materials
- **3D-printed NFC mounting bracket** for stable alignment and reliable tag reading
- **Panel design** to organize interface components and wiring

---

## Control & Tuning

PID parameters were iteratively tuned to achieve:
- Stable line-following behavior
- Smooth response to speed changes and load conditions
- Consistent station start/stop behavior

---

## Integration & Troubleshooting

During integration and testing, the following were addressed:
- Sensor calibration for reliable navigation and detection
- Wiring improvements to reduce noise and intermittent connections
- Mechanical fixes for stable sensor alignment and mounting
- Destination selection workflow verification via the on-device interface

---

## Key Responsibilities

- Analyzed and calibrated the system for proper AGV operation.
- Enhanced AGV features for optimal performance.
- Fine-tuned **PID parameters** to optimize control performance.
- Implemented **ESP32-based remote monitoring** for operational visibility.
- Addressed wiring and mechanical issues during integration.
- Contributed to **mechanical design** (trolley, NFC mount, panel layout).

---

## Technologies Used
- **Controllers**: Arduino Mega (main), ESP32 (monitoring)
- **Sensors**: Pixy Camera, NFC module, proximity sensor
- **Actuation**: Hoverboard motors
- **Control**: PID tuning
- **Interface**: Push buttons, small display
- **Mechanical**: 3D-printed parts, trolley, panel

---
