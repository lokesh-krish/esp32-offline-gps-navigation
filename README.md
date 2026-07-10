# ESP32-S3 Offline GPS Navigation System

A fully offline embedded navigation system built on ESP32-S3 with 
real-time GPS tracking, magnetometer heading, and LVGL-rendered 
OpenStreetMap tiles — zero network dependency.

## 🎥 Prototype demonstration of the ESP32-S3 offline navigation system showcasing the touchscreen interface, offline map rendering, and navigation functionality:

https://github.com/user-attachments/assets/ac3ee49c-818b-4f88-b43a-9c3aa9d40c8d

## Project Images

| Home Screen | GPS Speedometer |
|------------|-------------|
| ![](welcome_img.png) | ![](speedometer_img_report.png) |

| Navigation View | Offline Map(Zoomed out view) |
|------------|-------------|
| ![](map_img1.png) | ![](map_img2.png) |

| Hardware setup |
|-------------|
| ![](gps+map_img_report.png) |

## Features
- Real-time GPS location and speed display (TinyGPS++ / NMEA)
- ~1,000 OpenStreetMap tiles stored on SD card
- Magnetometer-based compass heading
- LVGL graphical interface on 2.1" round touch display
- GPS-derived speedometer (SquareLine Studio UI)
- Fully offline — no WiFi, no cellular required

## Hardware
| Component | Details |
|---|---|
| Microcontroller | Waveshare ESP32-S3 Touch IPS LCD 2.1" |
| GPS + IMU | BerryGPS-IMU v4 |
| Storage | MicroSD card (~1,000 map tiles) |
| Display | ST7701 round touch LCD |

## Tech Stack
`ESP32-S3` `Embedded C++` `LVGL` `TinyGPS++` `OpenStreetMap` 
`I2C` `SPI` `UART` `SquareLine Studio` `Arduino framework`

## Results
- Stable offline navigation with GPS fix across 10+ satellites
- Real-time map tile rendering with directional arrow overlay
- Speed display responsive to GPS HDOP-filtered velocity data

## Built During
Engineering Internship — i-WORKZ Automotive Pvt. Ltd., Bengaluru (Jan–Mar 2026)
