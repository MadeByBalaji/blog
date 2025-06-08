---
title: Read and Write using ThingSpeak
description: In this post, I will be doing a simple IoT project using ThingSpeak.
date: 2020-12-20 10:20:00 -0530
categories: [Hobbyist Haven]
tags: [nodemcu,thingspeak,iot]
image:
  path: /assets/img/blog/2020/node-thing-speak/readWrite.png
  lqip: /assets/img/blog/2020/node-thing-speak/readWrite.png
---

## Components:

1. NODE MCU [link](https://www.amazon.in/gp/product/B010O1G1ES/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1)

1. 100 ohms Resister[link](https://www.amazon.in/ELECTROBOT-100-PCS-OHM-RESISTORS/dp/B0713N6HYM/ref=sr_1_2?dchild=1&keywords=100+ohm+resistor&qid=1608481534&sr=8-2)

1. Breadboard [link](https://www.amazon.in/Generic-Elementz-Solderless-Piecesb-Circuit/dp/B00MC1CCZQ/ref=sr_1_3?dchild=1&keywords=breadboard&qid=1604324184&sr=8-3&th=1)

1. Jumper wires [link](https://www.amazon.in/ApTechDeals-Jumper-Female-breadboard-jumper/dp/B074J9CPV3/ref=sr_1_2_mod_primary_lightning_deal?crid=25YR2Z8ZGWY72&dchild=1&keywords=jumper+wires+for+arduino&qid=1604324158&sbo=Tc8eqSFhUl4VwMzbE4fw%2Fw%3D%3D&smid=AT95IG9ONZD7S&sprefix=jumper%2Caps%2C434&sr=8-2)

1. Push Button [link](https://www.amazon.in/switch-11x11x4-3MM-Tactile-Button-Self-Reset/dp/B07MDH66DN/ref=sr_1_1?dchild=1&keywords=button+for+arduino&qid=1604324082&sr=8-1)

1. LED [link](https://www.amazon.in/5mm-red-Led-Set-25/dp/B07CRYP6Y8/ref=sr_1_12?dchild=1&keywords=red+led&qid=1604331356&replacementKeywords=led&sr=8-12&vehicle=Vespa%3ARED)

## Hardware Part:

1. You can set the circuit as shown in the figure above

1. Here I have used 2 different boards make sure you name them as Read and Write separately

![circuit](assets/img/blog/2020/node-thing-speak/CircuitThingSpeakIoT.jpg){: width="1280" height="745" }
_circuit_

## Software Part:

In this project, I used the Arduino IDE for programming NODE-MCU.

1. I have written 2 separate code files

1. This is the code for Node-MCU with LED [here](https://github.com/MadeByBalaji/Arduino/blob/master/ThingSpeak/ThingSpeakLED/ThingSpeakLED.ino)

1. This is the code for Node-MCU with button [here](https://github.com/MadeByBalaji/Arduino/blob/master/ThingSpeak/ThingSpeakButton/ThingSpeakButton.ino)

1. You can view the dashboard [here](https://thingspeak.mathworks.com/channels/1270625)

![Dashboard](assets/img/blog/2020/node-thing-speak/ThingSpeak.jpg){: width="1117" height="475" }
_Dashboard_

That's it for now..

assets\img\blog\2020\\ThingSpeak.jpg
assets\img\blog\2020\node-thing-speak\