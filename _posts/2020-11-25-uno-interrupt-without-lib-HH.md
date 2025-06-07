---
title: Interrupt in Arduino without Library
description: In this project, I will make External Falling interrupt in Arduino UNO without a Library function.
date: 2020-11-25 10:20:00 -0530
categories: [Hobbyist Haven]
tags: [arduino,baremetal]
image:
  path: /assets/img/blog/2020/uno-interrupt/overview.png
  lqip: /assets/img/blog/2020/uno-interrupt/overview.png
---

## Boards and Digital PINs Usable for Interrupts

Uno, Nano, Mini, other 328-based - PIN 2, 3

Uno WiFi Rev.2, Nano 		 	- Every all digital pins

Mega, Mega2560, MegaADK 		- PIN 2, 3, 18, 19, 20, 21

## Circuit

![circuit](assets/img/blog/2020/uno-interrupt/Interrupt_bb_edited.jpg){: width="1383" height="792" }
_circuit_

## Summary

Interrupts in Arduino is a hidden feature, 

 1. In this project, I used PIN 2 (D2) as an interrupt PIN 

 2. The type of Interrupt used here is Falling Interrupt 

 3. You can get the code from here

 4. After uploading the code to board, when the button is pressed an interrupt occurs when 
	glows the in-built LED 


That's it for now..