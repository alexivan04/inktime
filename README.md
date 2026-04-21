
# InkTime – Open Source Smartwatch Hardware Project

## Overview
InkTime is an open-source, low-cost smartwatch hardware platform designed for mass production.  
This repository contains the complete hardware, manufacturing, and mechanical design files for the device.

The project includes:
- electronic schematic and PCB layout
- manufacturing outputs (Gerber, BOM, Pick & Place)
- complete 3D mechanical assembly
- documentation and design decisions
- validation and review updates


## Repository Structure

```text
InkTime/
│
├── Hardware/
│   ├── inktime.sch
│   ├── inktime.brd
│   └── schematic.pdf
│
├── Manufacturing/
│   ├── gerbers.zip
│   ├── bom.csv
│   └── pick_and_place.csv
│
├── Mechanical/
│   ├── inktime_assembly.step
│   └── inktime_assembly.f3d
│
├── Images/
│   ├── pcb_top.png
│   ├── pcb_bottom.png
│   ├── render_front.png
│   └── exploded_view.png
│
├── LICENSE
└── README.md
````

---

## Block Diagram

```text
Battery
   │
   ▼
Power Management (charger + regulation)
   │
   ▼
nRF52840 Microcontroller
   ├── IMU Sensor (I2C / SPI)
   ├── E-paper Display (SPI)
   ├── Buttons (GPIO)
   ├── USB-C Interface
   ├── Vibration Motor / Shaker
   └── Debug / Test Pads
```

---

## Hardware Architecture

The smartwatch is built around the **nRF52840** microcontroller, selected for:

* low power consumption
* integrated BLE support
* sufficient GPIO availability
* embedded ARM Cortex-M4 core

### Main Modules

* **Microcontroller:** nRF52840
* **Display:** e-paper display connected via SPI
* **Motion Sensor:** IMU connected via I2C/SPI
* **Power Supply:** Li-Po battery with charging IC and voltage regulation
* **User Input:** 3 push buttons
* **Feedback:** vibration motor (shaker)
* **Communication:** USB-C + BLE
* **Programming/Test:** dedicated test pads

---

## PCB Design Notes

### Stack-up

* **4-layer PCB**
* components placed **TOP layer only**
* routing on both TOP and BOTTOM
* GND planes on 1 and 3 layers

### Routing Rules

* power traces: **0.30 mm**
* signal traces: **minimum 0.15 mm**
* no right-angle routing
* minimized vias on power lines
* decoupling capacitors placed near IC supply pins

### RF Requirements

* antenna positioned at PCB edge
* no copper under antenna
* no signal traces below antenna
* board cutout included below antenna region

---

## Mechanical Integration

The PCB is designed to fit inside the provided smartwatch enclosure.


## Design Decisions / Notes

* accepted minor dimension warnings for button and USB alignment per project instructions
* battery connected directly to test pads to save internal volume
* all decoupling capacitors placed as close as possible to supply pins
* RF section isolated with stitched ground vias

---

## License

This project is released under the **Apache 2.0 License**.
