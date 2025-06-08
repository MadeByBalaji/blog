---
title: RFID Based Music Player
description: In this project, I used Arduino UNO to make RFID based music player.
date: 2020-11-29 10:20:00 -0530
categories: [Hobbyist Haven]
tags: [bareMetalCode,arduino]
image:
  path: /assets/img/blog/2020/rfid-music/RfidMusicPlayer.jpg
  lqip: /assets/img/blog/2020/rfid-music/RfidMusicPlayer.jpg
---

## Components:

1. Arduino UNO  [link](https://www.amazon.in/Development-Board-ATmega328P-ATmega16U2-Arduino/dp/B00H1HR576/ref=sr_1_6?dchild=1&keywords=Arduino+UNO&qid=1606215944&sr=8-6)

1. Breadboard [link](https://www.amazon.in/Generic-Elementz-Solderless-Piecesb-Circuit/dp/B00MC1CCZQ/ref=sr_1_3?dchild=1&keywords=breadboard&qid=1604324184&sr=8-3&th=1)

1. Jumper wires [link](https://www.amazon.in/ApTechDeals-Jumper-Female-breadboard-jumper/dp/B074J9CPV3/ref=sr_1_2_mod_primary_lightning_deal?crid=25YR2Z8ZGWY72&dchild=1&keywords=jumper+wires+for+arduino&qid=1604324158&sbo=Tc8eqSFhUl4VwMzbE4fw%2Fw%3D%3D&smid=AT95IG9ONZD7S&sprefix=jumper%2Caps%2C434&sr=8-2)

1. 220 ohms Resistor  [link](https://www.amazon.in/INVENTO-Resistor-Resistance-Toleance-Quality/dp/B083CPQGGB/ref=sr_1_3?crid=8VBKZWQ7BV19&dchild=1&keywords=220+ohm+resistors&qid=1606215988&sprefix=220%2Caps%2C737&sr=8-3) 

1. RC-522 [link](https://www.amazon.in/REES52-MFRC-522-Antenna-Proximity-Arduino/dp/B018EUMKVE/ref=sr_1_1?dchild=1&keywords=RC522&qid=1606664065&sr=8-1)

1. RFID Card [link](https://www.amazon.in/Smart-iCards-Printable-Proximity-Attendance/dp/B078WCV8KJ/ref=sr_1_7?dchild=1&keywords=RFID%2Bcard&qid=1606664077&sr=8-7&th=1)

1. DFmini Player [link](https://robocraze.com/products/dfplayer-mini-mp3-module?variant=40193310720153&country=IN&currency=INR&utm_medium=product_sync&utm_source=google&utm_content=sag_organic&utm_campaign=sag_organic&campaignid=21593322920&adgroupid=&keyword=&device=c&gad_source=1&gad_campaignid=21586700133)

## Intro Video

{% include embed/youtube.html id='u6IKNNch2aY' %}

## Hardware Part:
1. RFID cards are read by  RC-522 which acts as an RFID reader it can read cards at a distance of 1-3cms

1. Songs are stored in an SD card and inserted in the allocated space for in DFmini layer.

1. Make sure you rename the songs as shown in the image below

![sdCardNaming](assets/img/blog/2020/rfid-music/sdCardNaming.jpg){: width="597" height="252" }
_SD Card Naming_

4.  Set the circuit as shown in the image below

## Software Part:
1. In this project, I used the Arduino IDE for programming Arduino UNO.

1. You can get the code from [here](https://github.com/MadeByBalaji/Arduino/blob/master/RfidMusicPlayer/RfidMusicPlayer.ino)

1. Swipe the RFID card at the reader, to play the required song.

## Complete Video

{% include embed/youtube.html id='LY3o8TtZg6U' %}

That's it for now...