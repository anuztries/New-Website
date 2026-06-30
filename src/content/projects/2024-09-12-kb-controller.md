---
title: "Custom Mechanical Keyboard Controller"
description: "A programmable keyboard controller built with RP2040, featuring QMK/VIA support and custom PCB design for a 75% layout."
date: 2024-09-12
draft: false
tech: ["RP2040", "KiCad", "QMK", "C++", "USB HID"]
github: "https://github.com/yourusername/kb-controller"
---

# Custom Mechanical Keyboard Controller

## Overview

A fully customizable keyboard controller based on the Raspberry Pi RP2040 microcontroller. This project includes both hardware (PCB design) and firmware (QMK-based) for building custom mechanical keyboards.

## Features

- RP2040 dual-core ARM Cortex-M0+ processor
- Native USB support with QMK/VIA compatibility
- Hot-swappable MX switch sockets
- RGB underglow with WS2812B LEDs
- OLED display for layer indication
- Rotary encoder support

## Hardware Specifications

- MCU: RP2040 (264KB SRAM, 2MB Flash)
- Matrix size: Up to 90 keys
- GPIO pins: 26 available for customization
- USB-C connector with ESD protection
- Reset button for bootloader access

## PCB Design Highlights

- 1.6mm FR-4 substrate, 2-layer design
- Cherry MX hot-swap footprints
- In-switch and underglow LED placement
- I2C header for daughter boards
- SWD programming header

## Firmware Features

```c
const uint16_t PROGMEM keymaps[][MATRIX_ROWS][MATRIX_COLS] = {
    [0] = LAYOUT_75_pct(
        KC_ESC,  KC_1,    KC_2,    KC_3,    // ... etc
    ),
    [1] = LAYOUT_75_pct(
        KC_GRV,  KC_F1,   KC_F2,   KC_F3,   // ... etc
    ),
};
```

- Full QMK feature set
- VIA real-time configuration
- Multiple layers with tap-dance
- Macro recording capability
- RGB lighting effects

## Build Process

1. Schematic capture in KiCad
2. PCB layout with impedance control
3. JLCPCB fabrication
4. Hand soldering of components
5. Firmware compilation and flashing

## Lessons Learned

- Importance of decoupling capacitor placement
- USB differential pair routing techniques
- Switch matrix optimization
- Power consumption management

## Future Iterations

- Wireless version with nRF52840
- Per-key RGB instead of underglow
- Integrated display for status info
- Gasket mount compatibility
