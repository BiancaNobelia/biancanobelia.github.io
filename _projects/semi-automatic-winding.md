---
title: Semi-automatic Winding Machine
description: Semi-automatic machine that combines winding and insulation stripping to improve production output and reduce labor costs. 
cover_image: /pictures/winding.jpg
tags: [Automation Winding, Insulation Stripping, Pneumatic, Servo Drive, Double Acting Cylinder, HMI]
featured: true
project_type: full-time
demo_url: https://drive.google.com/file/d/1VqkIWIbYmHRotvpB-isZLK6dTZoTA6W-/view?usp=drive_link
repo_url:
date: 2023-08-01
gallery:
  - image: /pictures/winding.jpg
    caption: Semi-automatic Winding Machine
  - image: /pictures/winding_circuit.jpg
    caption: Electrical Panel & Wiring
---

## Project Overview

This project is a **semi-automatic winding machine** designed to combine two production processes — **winding** and **insulation stripping** — into a single machine to increase production output and reduce labor costs. The system integrates servo motion control and pneumatic actuation, supported by an HMI for operator control and parameter configuration.

---

## System Description

The machine performs two main operations:

<table class="project-table">
  <thead>
    <tr>
      <th>Operation</th>
      <th>Actuator</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Winding</td>
      <td>Panasonic Servo Motor</td>
      <td>Drives the winding process with controllable speed and position</td>
    </tr>
    <tr>
      <td>Insulation Stripping</td>
      <td>Festo Double-Acting Cylinder</td>
      <td>Performs the stripping motion via pneumatic actuation</td>
    </tr>
  </tbody>
</table>

A **Weintek HMI** is used for operator control and monitoring. Communication between the **servo drive** and **HMI** is established via **RS232/RS485**, enabling command handling, parameter configuration, and operational status monitoring.

---

## Hardware Components

<table class="project-table">
  <thead>
    <tr>
      <th>Component</th>
      <th>Role</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Panasonic Servo Motor + Drive</td>
      <td>Winding actuation</td>
    </tr>
    <tr>
      <td>Festo Double-Acting Cylinder</td>
      <td>Insulation stripping actuation</td>
    </tr>
    <tr>
      <td>Weintek HMI</td>
      <td>Operator interface</td>
    </tr>
    <tr>
      <td>RS232 / RS485</td>
      <td>Servo drive ↔ HMI communication</td>
    </tr>
    <tr>
      <td>Electrical Control Panel</td>
      <td>Wiring, protection, and component integration</td>
    </tr>
  </tbody>
</table>

---

## Key Responsibilities

- Analyzed, calculated, and configured parameters for the **Panasonic servo drive**.
- Established **RS232/RS485 communication** between the servo drive and Weintek HMI.
- Diagnosed and resolved mechanical and system failures during commissioning.
- Replicated the system using a **Festo servo drive and motor** as an alternative setup.

---

## Technologies Used
- **Servo System**: Panasonic servo motor + drive
- **Pneumatics**: Festo double-acting cylinder
- **HMI**: Weintek
- **Communication**: RS232 / RS485
- **Electrical**: Control panel wiring and integration

---
