---
title: Chiller Monitoring (IoT)
description: IoT-based monitoring system for a chiller. Monitors chiller input/output temperatures using thermocouple sensors, observes chiller status, compressor, and water pump, and displays data on a website via Wi-Fi. 
cover_image: /pictures/chiller.png
tags: [IoT, ESP32, Temperature Sensing, Wi-Fi, Web Dashboard]
featured: false
project_type: full-time
demo_url: 
repo_url:
date: 2023-02-01
gallery:
  - image: /pictures/chiller.png
    caption: Chiller Unit
  - image: /pictures/chiller_circuit.png
    caption: Electrical Panel & Wiring
---

## Project Overview

This project develops an **IoT monitoring system** for a **chiller**. The system measures the **input and output temperatures** and monitors the **on/off status** of key components. All data is transmitted over **Wi-Fi** and displayed on a **web dashboard** for remote monitoring.

---

## System Description

<table class="project-table">
  <thead>
    <tr>
      <th>Parameter</th>
      <th>Details</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Temperature</td>
      <td>Chiller inlet &amp; outlet via thermocouple sensors</td>
    </tr>
    <tr>
      <td>Status</td>
      <td>On/off state of chiller, compressor, and water pump</td>
    </tr>
    <tr>
      <td>Connectivity</td>
      <td>Wi-Fi data transmission to web dashboard</td>
    </tr>
  </tbody>
</table>

---

## Hardware & Implementation

- **Microcontroller**: ESP32 / ESP8266
- **Sensors**: Thermocouple sensors for inlet/outlet temperature measurement
- **Switching**: SSR + relay for safe load-side signal interfacing
- **Connectivity**: Wi-Fi data transmission to a web-based dashboard
- **Electrical Panel**: Full wiring and component integration inside a control panel

---

## Key Responsibilities

- Designed and developed the full IoT monitoring system.
- Wrote the embedded firmware using ESP32/ESP8266.
- Performed soldering, component installation, and electrical panel wiring.
- Implemented Wi-Fi data transmission to the web dashboard.
- Conducted troubleshooting and system maintenance.

---

## Technologies Used
- **Microcontroller**: ESP32 / ESP8266
- **Sensors**: Thermocouple (temperature), relay/SSR (status detection)
- **Communication**: Wi-Fi
- **Interface**: Web dashboard

---
