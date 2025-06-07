---
title: LCD Display controller using UNO with no Library Function
description: In this Project, I controlled the LCD display using Arduino UNO  with no library function.
date: 2020-11-24 10:20:00 -0530
categories: [Hobbyist Haven]
tags: [arduino,baremetal,lcd]
image:
  path: /assets/img/blog/2020/uno-lcd/ArduinoLCD.jpeg
  lqip: /assets/img/blog/2020/uno-lcd/ArduinoLCD.jpeg
---

## Components:
1. Arduino UNO [link](https://www.amazon.in/Development-Board-ATmega328P-ATmega16U2-Arduino/dp/B00H1HR576/ref=sr_1_6?dchild=1&keywords=Arduino%2BUNO&qid=1606215944&sr=8-6&th=1)

1. 16x2 LCD Display [link](https://www.amazon.in/Robodo-MO7-Display-Arduino-Project/dp/B073Q2X41N/ref=sr_1_5?dchild=1&keywords=lcd+16x2+display&qid=1605279563&sr=8-5&tag=duc21-21)

1. Breadboard [link](https://www.amazon.in/Generic-Elementz-Solderless-Piecesb-Circuit/dp/B00MC1CCZQ/ref=sr_1_3?dchild=1&keywords=breadboard&qid=1604324184&sr=8-3&th=1)

1. Jumper wires [link](https://www.amazon.in/ApTechDeals-Jumper-Female-breadboard-jumper/dp/B074J9CPV3/ref=sr_1_2_mod_primary_lightning_deal?crid=25YR2Z8ZGWY72&dchild=1&keywords=jumper+wires+for+arduino&qid=1604324158&sbo=Tc8eqSFhUl4VwMzbE4fw%2Fw%3D%3D&smid=AT95IG9ONZD7S&sprefix=jumper%2Caps%2C434&sr=8-2)

1. Potentiometer [link](https://www.amazon.in/Vertical-Variable-Resistor-Trimmer-Potentiometer/dp/B08BW72XGV/ref=sr_1_4?crid=29OVXCNGVEEBY&dchild=1&keywords=potentiometer&qid=1605280951&sprefix=poten%2Caps%2C388&sr=8-4)

1. 220 ohms Resistor  [link](https://www.amazon.in/INVENTO-Resistor-Resistance-Toleance-Quality/dp/B083CPQGGB/ref=sr_1_3?crid=8VBKZWQ7BV19&dchild=1&keywords=220+ohm+resistors&qid=1606215988&sprefix=220%2Caps%2C737&sr=8-3) 

assets\img\blog\2020\
![Top View](assets/img/blog/2020/uno-lcd/TotalViewLCDArduino.jpg){: width="536" height="628" }
_Top View_

## Hardware Part:

1. I connected the Potentiometer(10k ohms) to control the contrast of the display.

1. Used 220ohms resister for the LED backlight.

1. You can set the circuit as shown in the figure below

## Circuit

![circuit](assets/img/blog/2020/uno-lcd/circuit.jpg){: width="1944" height="1815" }
_circuit_

## Software Part:

1. In this project I used Arduino IDE for programming Arduino UNO.

1. You can get the code from [here](https://github.com/MadeByBalaji/Arduino/blob/master/LCD/LCD.ino)

1. After uploading the code adjust the potentiometer to change the contrast of the LCD display

![TotalViewLCDArduino](assets/img/blog/2020/uno-lcd/TotalViewLCDArduino.jpg){: width="585" height="701" }
_Total View LCD and Arduino_

That's it for now..