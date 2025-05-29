---
title: Street Light Controller
description: In this project, I made a Street light controller using STM32F446RE.
date: 2022-11-02 11:33:00 -0530
categories: [Firmware Fortress]
tags: [embedded,stm32f446re]
pin: true
math: true
mermaid: true
image:
  path: assets\lib\blog\2022\street-light\overview.jpg
  lqip: assets\lib\blog\2022\street-light\overview.jpg
  #alt: Responsive rendering of Chirpy theme on multiple devices.
---

## Working:
1. Connect the LED's Positive terminal to D7 and negative terminal to 100ohms resistor and ground.

1. Connect the LDR to A0 and +5v port followed by 100ohms resistor and ground.

1. Using CubeMX generate the code in keil and flash it to the Board.

1. The Code Generated is here

1. Once if there is light on sensor, the LED turns Off

1. If there is dark the light turn ON.

[^footnote]: The footnote source
[^fn-nth-2]: The 2nd footnote source
