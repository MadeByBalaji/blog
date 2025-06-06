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
  path: /assets/img/blog/2022/street-light/overview.jpg
  lqip: /assets/img/blog/2022/street-light/overview.jpg
  #alt: Responsive rendering of Chirpy theme on multiple devices.
---

## Components:
1. STM32F446RE as controller [link](https://www.amazon.in/NUCLEO-F446RE-STM32F446RET6-development-integrates-XYG-Study/dp/B014IXUB1M/ref=sr_1_1?crid=3FAQAJN6X1FWI&dchild=1&keywords=stm32f446re&qid=1604331292&sprefix=stm32f446%2Caps%2C707&sr=8-1)
1. Light Dependent Resistor [link](https://www.amazon.in/Component7-LDR-Dependent-Register-Resistor/dp/B01BADCLH0/ref=sr_1_1?dchild=1&keywords=LDR&qid=1604331235&sr=8-1&tag=duc21-21)
1. Red LED [link](https://www.amazon.in/5mm-red-Led-Set-25/dp/B07CRYP6Y8/ref=sr_1_12?dchild=1&keywords=red+led&qid=1604331356&replacementKeywords=led&sr=8-12&vehicle=Vespa%3ARED)
1. 100 ohms Resistor [link](https://www.amazon.in/SEMICOMP-100-OHM-Tolerance-Resistance-Pieces/dp/B08GQ61KY2/ref=sr_1_1?crid=1UWXI2AC1OHGJ&dchild=1&keywords=100+oms+resistance&qid=1604331586&sprefix=100+oms%2Caps%2C341&sr=8-1)
1. Breadboard [link](https://www.amazon.in/Generic-Elementz-Solderless-Piecesb-Circuit/dp/B00MC1CCZQ/ref=sr_1_3?dchild=1&keywords=breadboard&qid=1604324184&sr=8-3)
1. Jumper wires [link](https://www.amazon.in/ApTechDeals-Jumper-Female-breadboard-jumper/dp/B074J9CPV3/ref=sr_1_2_mod_primary_lightning_deal?crid=25YR2Z8ZGWY72&dchild=1&keywords=jumper+wires+for+arduino&qid=1604324158&sbo=Tc8eqSFhUl4VwMzbE4fw%2Fw%3D%3D&smid=AT95IG9ONZD7S&sprefix=jumper%2Caps%2C434&sr=8-2)


## Working:
1. Connect the LED's Positive terminal to D7 and negative terminal to 100ohms resistor and ground.

1. Connect the LDR to A0 and +5v port followed by 100ohms resistor and ground.

1. Using CubeMX generate the code in keil and flash it to the Board.

1. The Code Generated is [here](https://github.com/MadeByBalaji/STM32F446RE/blob/main/KeilWorkSpace/Product/StreetProject/Src/main.c)

1. Once if there is light on sensor, the LED turns Off

1. If there is dark the light turn ON.

## Video

{% include embed/youtube.html id='RFV882PcUmo' %}
