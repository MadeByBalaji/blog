---
title: Register Level Coding in Arduino UNO
description: In this blog post, I will be doing register level coding using Arduino UNO.
date: 2020-11-08 10:20:00 -0530
categories: [Hobbyist Haven]
tags: [bareMetalCode,arduino]
pin: true
math: true
mermaid: true
image:
  path: /assets/lib/blog/2020/register-level-uno/arduino.jpg
  lqip: /assets/lib/blog/2020/register-level-uno/arduino.jpg
  #alt: Responsive rendering of Chirpy theme on multiple devices.
---

## Overview:

Arduino is commonly programmed using ArduinoIDE although there are many other IDEs like platformIO (another blog on this later) are not preferred by users due to the complex and additional software, Change of PATH variable, Environment variable like that stuff.


Due to this many users have been using ArduinoIDE and programming on that language only

we can also program Arduino using the same IDE you have been using, but this time using Register.

Ya!, no more pinMode and digitalWrite instead we will enable and disable the ports at the register level.


Based on the PIN definition, there are three ports in Arduino's microcontroller ATmega168

1. PORT-B (digital pin 8 - 13 )

1. PORT-C (analog pin A0 - A5)

1. PORT-D (digital pin 0- 7)

<!-- [^footnote]: The footnote source -->
<!-- [^fn-nth-2]: The 2nd footnote source -->
