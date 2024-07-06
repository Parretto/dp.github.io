---
layout: page
title: Overview
permalink: /overview/
nav_order: 1
---

# Overview

### Introduction
The DisplayPort IP-core is a DisplayPort solution for FPGA implementation. 
It has a resource optimized footprint and it is written in SystemVerilog. 
A thin host driver is provided with the IP-core. The application software controls the IP-core using this driver.  

### Features
- DisplayPort 1.4a 
- RBR, HBR, HBR2 and HBR3 line rates
- Support for 1, 2 and 4 DP lanes
- Native video and AXI stream interfaces
- Single Stream transport mode (SST)
- Multi Stream transport mode (MST)
- Dual and quad pixels per clock (PPC)
- Color depth: 8 & 10-bits (BPC)
- Color space: RGB 4:4:4 & YUV 4:4:4

### Resources

The following FPGA vendors are supported;

- AMD 
- Intel FPGA 
- Lattice Semiconductor

The tables below show the device utilization for the various FPGA devices. 

---

**AMD Ultrascale+**

| Module | LUT | FF | BRAM | DSP |
|--------|-----|----|------|-----|
| DisplayPort TX (DPTX) - SST | 4566 | 3289 | 5 | 0 |
| DisplayPort TX (DPTX) - MST | 5866 | 4993 | 8.5 | 0 |
| DisplayPort RX (DPRX) | 4688 | 3506 | 5 | 0 |
| Video Toolbox (VTB) | 1157 | 2289 | 1.5 | 2 |

- Device XCZU9EG
- Vivado software v2023.1
- Dual pixel datapath
- Date: January 14, 2024

---

**AMD Artix-7**

| Module | LUT | FF | BRAM | DSP |
|--------|-----|----|------|-----|
| DisplayPort TX (DPTX) - SST | 6163 | 3933 | 5 | 0 |
| DisplayPort RX (DPRX) | 6619 | 4199 | 5 | 0 |
| Video Toolbox (VTB) | 1243 | 2340 | 3 | 2 |

- Device XC7A200TFFG1156-2
- Vivado software v2023.1
- Quad pixel datapath
- Date: January 14, 2024

---

**Intel Cyclone 10GX**

| Module | ALM | REG | M20K | DSP | 
|--------|-----|-----|------|-----|
| DisplayPort TX (DPTX) - SST | 3580.8 | 3458 | 8 | 0 |
| DisplayPort TX (DPTX) - MST | 4853.2 | 5279 | 17 | 0 |
| DisplayPort RX (DPRX) | 3909.1 | 3854 | 8 | 0 |
| Video Toolbox (VTB) | 881.9 | 2631 | 3 | 1 |

- Device 10CX220YF780E5G
- Quartus Prime Pro software 23.2.0
- Dual pixel datapath
- Date: January 14, 2024

---

**Intel Arria 10GX**

| Module | ALM | REG | M20K | DSP | 
|--------|-----|-----|------|-----|
| DisplayPort TX (DPTX) - SST | 3588.3 | 3470 | 8 | 0 |
| DisplayPort TX (DPTX) - MST | 4862.0 | 5248 | 17 | 0 |
| DisplayPort RX (DPRX) | 3958.4 | 3833 | 8 | 0 |
| Video Toolbox (VTB) | 881.0 | 2628 | 3 | 1 |

- Device 10AX115S2F45I1SG
- Quartus Prime Pro software 23.2.0
- Dual pixel datapath
- Date: January 14, 2024

---

**Lattice CertusPro-NX**

| Module | LUT | FF | EBR | DSP | 
|--------|-----|----|-----|-----|
| DisplayPort TX (DPTX) - SST | 9729 | 4121 | 10 | 0 |
| DisplayPort TX (DPTX) - MST | 12706 | 6399 | 17 | 0 |
| DisplayPort RX (DPRX) | 12120 | 4295 | 10 | 0 |
| Video Toolbox (VTB) | 2031 | 2463 | 6 | 5.5 |

- Device LFCPNX-100
- Radiant software 2023.2.0.38.1
- Quad pixel datapath
- Date: January 14, 2024

---

### Known Limitations


**DPTX / DPRX**
- The horizontal video timing must be dividable by the number of pixels per clock (PPC). 
- Any video resolution is supported, however only video resolutions tested are 720p50/60, 1080p50/60, 1440p50/60 and 4kp50/60. 


**VTB**
- At start of the video the screen might flicker while the clock recovery module is locking to the incoming video stream. 
