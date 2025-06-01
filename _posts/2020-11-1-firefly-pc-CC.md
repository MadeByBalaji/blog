---
title: Firefly's Credit Card sized PC with Six-Core
description: Firefly's 120mm Credit card sized PC with Six-Core 64-Bit High Performance RK3399 Processor without cooling Fan..
date: 2020-11-01 10:20:00 -0530
categories: [Chip Chat]
tags: [news,minipc]
pin: true
math: true
mermaid: true
image:
  path: assets\lib\blog\2020\fire-pc\overview.jpg
  lqip: assets\lib\blog\2020\fire-pc\overview.jpg
  #alt: Responsive rendering of Chirpy theme on multiple devices.
---

## Overview:

**ROCKCHIP RK3399** had multiple power supply ports:

1. DC12V Power Supply,

1. PoE (Power Over Ethernet),

### Network Capability:

1. Gigabit	Ethernet

1. 2.4 GHz Wifi

1. Bluetooth 4.2

### Expansion Board Combination:

  Expansion Boards can be used to improve the performance greatly.

### Camera:

  Has 2xMIPI-CSI. RK3399 can support dual-8MegaPixel or Single-13MegaPixel Camera.


1. Connect the LED's Positive terminal to D7 and negative terminal to 100ohms resistor and ground.

1. Connect the LDR to A0 and +5v port followed by 100ohms resistor and ground.

1. Using CubeMX generate the code in keil and flash it to the Board.

1. The Code Generated is here

1. Once if there is light on sensor, the LED turns Off

1. If there is dark the light turn ON.

<!-- [^footnote]: The footnote source -->
<!-- [^fn-nth-2]: The 2nd footnote source -->
