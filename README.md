# ESP32-S3 Offline GPS Navigation System

A fully offline embedded navigation system built on ESP32-S3 with real-time GPS tracking, magnetometer heading, and LVGL-rendered OpenStreetMap tiles — zero network dependency.

## Demo

Prototype demonstration of the ESP32-S3 offline navigation system showcasing the touchscreen interface, offline map rendering, and navigation functionality:

https://github.com/user-attachments/assets/ac3ee49c-818b-4f88-b43a-9c3aa9d40c8d

## Overview

Unlike online navigation systems such as Google Maps, this project needs no internet connection during operation — all map data is stored locally on an SD card. It brings together GPS, IMU, SD card storage, an LVGL graphical interface, and touchscreen interaction in a single embedded system that displays live navigation on a round touch display.

The system boots to a welcome screen with two modes:
- **Map** — offline navigation view with a live position/heading arrow over locally stored OpenStreetMap tiles
- **Meter** — GPS-based speedometer built in SquareLine Studio

## Project Images

| Home Screen | GPS Speedometer |
|---|---|
| ![](welcome_img.png) | ![](speedometer_img_report.png) |

| Navigation View | Offline Map (Zoomed Out) |
|---|---|
| ![](map_img1.png) | ![](map_img2.png) |

| Hardware Setup |
|---|
| ![](gps+map_img_report.png) |

## Features

- Real-time GPS location and speed display (TinyGPS++ / NMEA)
- ~1,000 OpenStreetMap tiles across 3 zoom levels, stored on SD card
- Magnetometer-based compass heading, used to rotate the position arrow
- LVGL graphical interface on a 2.1" round touch display
- GPS-derived speedometer built with SquareLine Studio
- Fully offline — no WiFi, no cellular required

## Hardware

| Component | Details |
|---|---|
| Microcontroller | Waveshare ESP32-S3 Touch IPS LCD 2.1" (round) |
| GPS + IMU | BerryGPS-IMU v4 (GPS, accelerometer, gyroscope, magnetometer) |
| Storage | MicroSD card (~1,000 offline map tiles) |
| Display | ST7701 round touchscreen LCD |

## Connections

| Component | Interface | ESP32-S3 Bus |
|---|---|---|
| ST7701 Round Touch Display | Display + touch control | SPI |
| BerryGPS-IMU v4 — GPS | Serial NMEA output | UART |
| BerryGPS-IMU v4 — Magnetometer/IMU | Sensor register access | I²C |
| MicroSD Card | Map tile & asset storage | SPI |

*Pin-level mapping intentionally omitted here — module wiring follows the Waveshare ESP32-S3 Touch LCD board's default SPI/UART/I²C assignments.*

## How It Works

1. On boot, the ESP32-S3 initializes the display, touchscreen, LVGL engine, SD card, GPS (UART), and IMU (I²C).
2. The welcome screen offers **Map** or **Meter**.
3. **Map mode:** GPS provides latitude/longitude/speed (parsed via TinyGPS++); the magnetometer provides heading. The app loads only the required OpenStreetMap tiles from the SD card for the current position and zoom level, and renders a directional arrow that moves and rotates with the device.
4. **Meter mode:** A SquareLine Studio-designed speedometer UI displays live GPS-derived speed.

This project focuses on offline map visualization and live position/heading display — it does not implement route planning, SLAM, obstacle avoidance, sensor-fusion filters (Kalman/Madgwick), or autonomous navigation.

## Offline Map Preparation

The target area was downloaded from OpenStreetMap, split into smaller tiles (since the ESP32 can't handle large map images efficiently), converted to an embedded-compatible format, and organized by zoom level on the SD card. At runtime, only the tiles needed for the current view are loaded, keeping memory usage low and rendering smooth.

## Tech Stack

`ESP32-S3` `Embedded C++` `LVGL` `TinyGPS++` `OpenStreetMap` `I2C` `SPI` `UART` `SquareLine Studio` `Arduino Framework`

## Results

- Stable offline navigation with GPS fix across 10+ satellites
- Real-time map tile rendering with directional arrow overlay
- Speed display responsive to GPS HDOP-filtered velocity data

## Built During

Engineering Internship — i-WORKZ Automotive Pvt. Ltd., Bengaluru (Jan–Mar 2026)
