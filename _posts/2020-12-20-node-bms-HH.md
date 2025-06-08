---
title: BMS for Electric Vehicles using NODE MCU
description: In this project, We will get the Battery percentage of Electric Vehicle on the web.
date: 2020-12-20 10:20:00 -0530
categories: [Hobbyist Haven]
tags: [nodemcu,ev,bms,iot]
image:
  path: /assets/img/blog/2020/node-bms/analogMeter.jpg
  lqip: /assets/img/blog/2020/node-bms/analogMeter.jpg
---

## Components:

1. NODE MCU [link](https://www.amazon.in/gp/product/B010O1G1ES/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1)

1. 12V Battery [link](https://www.amazon.in/AmazonBasics-A23-Alkaline-Batteries-4-Pack/dp/B07GNMFLKH/ref=sr_1_14?dchild=1&keywords=12v+battery&qid=1608481406&sr=8-14)

1. 300 ohms Resister[link](https://www.amazon.in/300-Ohm-Watt-Resistor-Tolerance/dp/B0D575D1MS/ref=sr_1_1?crid=1KJT4KTMNHR7Y&dib=eyJ2IjoiMSJ9.1RADmy1_9-qSWs9RGeZYkNXChUdaf23lcbb61avxJUjhLw780ctlHnZBgy-t0XknKE5B3-nsOJ97CiGRPEOTDuF0QkV7-mSE9IA4Qp9t8a-WXI-PDXqXjwqu38TsCKtTTpL4bADY_UTCm3-3aLzEwHd-ImEQGVp4ThhJsnH_beZpObYUwoWEBlx6UWLHlJQjkOBWNFxgVUBCbCFATRp5LZiQDCtLJVKoMDNH4HOy30IA6urQLyw_Z-boM7X0QYbc5ipwm1r2xbv036rjSpiY45hmhQSZNQU7y2BrwyPD1qI.65gC9tIq1stav143eRo0Fbt7EF9lb6ERcVD9seXJHEI&dib_tag=se&keywords=300+ohm+resistor&qid=1749395901&sprefix=00+ohm+resistor%2Caps%2C417&sr=8-1)

1. 100 ohms Resister[link](https://www.amazon.in/ELECTROBOT-100-PCS-OHM-RESISTORS/dp/B0713N6HYM/ref=sr_1_2?dchild=1&keywords=100+ohm+resistor&qid=1608481534&sr=8-2)

## Hardware Part:

1. I connected the Battery via a Voltage Divider to the NODE-MCU.

1. Used 300 ohms and 100 ohms resistor for the Voltage Divider.

1. You can set the circuit as shown in the figure above.

![circuit](assets/img/blog/2020/node-bms/circuit.jpg){: width="643" height="356" }
_circuit_

## Software Part:

In this project, I used the Arduino IDE for programming Arduino UNO.

1. I generated API using [ThinkSpeak](https://thingspeak.mathworks.com/)

1. You can see the code from [here](https://github.com/MadeByBalaji/Arduino/blob/master/BMSusingNODEmcu/BMSusingNODEmcu.ino)

1. You can view the dashboard [here](https://thingspeak.mathworks.com/channels/1265159#.X983E3EpA5k.linkedin)

![Battery Percentage](assets/img/blog/2020/node-bms/bat.jpg){: width="388" height="209" }
_Battery Percentage_

That's it for now..