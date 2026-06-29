---
title: "FPGA Video Processing Pipeline"
description: "Real-time video effects processor implemented on FPGA using Verilog, featuring multiple filter algorithms and HDMI output."
date: 2024-11-20
draft: false
tech: ["Verilog", "FPGA", "HDMI", "Digital Signal Processing", "Vivado"]
github: "https://github.com/yourusername/fpga-video-pipeline"
---

# FPGA Video Processing Pipeline

## Overview
A hardware-accelerated video processing system implemented on a Xilinx Artix-7 FPGA. This project demonstrates real-time video manipulation capabilities including filters, color adjustments, and frame buffering.

## Features
- 720p60 HDMI input/output
- Multiple real-time video filters:
  - Grayscale conversion
  - Edge detection (Sobel operator)
  - Color inversion
  - Brightness/contrast adjustment
- Frame buffer for video freeze functionality
- DIP switch control for filter selection

## Hardware Platform
- Xilinx Artix-7 XC7A35T FPGA
- ADV7611 HDMI receiver
- ADV7511 HDMI transmitter
- 128Mb DDR2 SDRAM for frame buffering

## Implementation Details

### Video Timing Controller
```verilog
module video_timing (
    input wire clk,
    input wire reset,
    output wire hsync,
    output wire vsync,
    output wire de,
    output wire [10:0] pixel_x,
    output wire [10:0] pixel_y
);
```

### Filter Architecture
The processing pipeline uses a line buffer approach with three-row storage for convolution operations. Each filter is implemented as a separate module that can be dynamically selected.

## Challenges Overcome
- Managing clock domain crossings between HDMI clocks and system clock
- Optimizing memory bandwidth for real-time processing
- Meeting timing constraints at 74.25 MHz pixel clock

## Results
- Latency: < 2 frames
- Resource utilization: 65% LUTs, 40% BRAM
- Power consumption: 1.2W typical

## Future Work
- Add OSD (On-Screen Display) menu
- Implement more advanced filters (blur, sharpen)
- Support for 1080p resolution
