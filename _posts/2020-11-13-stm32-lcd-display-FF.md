---
title: LCD Display controller using STM32 with no Library Function
description: In this Project, I controlled the LCD display using STM32F446RE on the Register level with no library function.
date: 2020-11-13 11:33:00 -0530
categories: [Firmware Fortress]
tags: [baremetal,stm32f446re]
image:
  path: /assets/img/blog/2020/stm-lcd/overview.jpg
  lqip: /assets/img/blog/2020/stm-lcd/overview.jpg
---

## Components:

1. STM32F446RE as controller [link](https://www.amazon.in/NUCLEO-F446RE-STM32F446RET6-development-integrates-XYG-Study/dp/B014IXUB1M/ref=sr_1_1?crid=3FAQAJN6X1FWI&dchild=1&keywords=stm32f446re&qid=1604331292&sprefix=stm32f446%2Caps%2C707&sr=8-1)

1. 16x2 LCD Display [link](https://www.amazon.in/Robodo-MO7-Display-Arduino-Project/dp/B073Q2X41N/ref=sr_1_5?dchild=1&keywords=lcd+16x2+display&qid=1605279563&sr=8-5&tag=duc21-21)

1. Potentiometer [link](https://www.amazon.in/Vertical-Variable-Resistor-Trimmer-Potentiometer/dp/B08BW72XGV/ref=sr_1_4?crid=29OVXCNGVEEBY&dchild=1&keywords=potentiometer&qid=1605280951&sprefix=poten%2Caps%2C388&sr=8-4)

1. 100 ohms Resistor [link](https://www.amazon.in/SEMICOMP-100-OHM-Tolerance-Resistance-Pieces/dp/B08GQ61KY2/ref=sr_1_1?crid=1UWXI2AC1OHGJ&dchild=1&keywords=100+oms+resistance&qid=1604331586&sprefix=100+oms%2Caps%2C341&sr=8-1)

1. Breadboard [link](https://www.amazon.in/Generic-Elementz-Solderless-Piecesb-Circuit/dp/B00MC1CCZQ/ref=sr_1_3?dchild=1&keywords=breadboard&qid=1604324184&sr=8-3)

1. Jumper wires [link](https://www.amazon.in/ApTechDeals-Jumper-Female-breadboard-jumper/dp/B074J9CPV3/ref=sr_1_2_mod_primary_lightning_deal?crid=25YR2Z8ZGWY72&dchild=1&keywords=jumper+wires+for+arduino&qid=1604324158&sbo=Tc8eqSFhUl4VwMzbE4fw%2Fw%3D%3D&smid=AT95IG9ONZD7S&sprefix=jumper%2Caps%2C434&sr=8-2)

![Circuit](assets/img/blog/2020/stm-lcd/view.jpeg){: width="585" height="1040" }
_Circuit_

## Hardware Part:

1. Place the LCD display in the BreadBoard.

1. Connect the Supply and Gnd PIN to the controllers +5v and Gnd respectively.

1. A potentiometer can be used if required to control the contrast of the Display.

1. We will connect the RS(Reset) pin of LCD to the PB5 of the controller

1. Then the R/W(Read/Write) pin of LCD to the PB6 of the controller

1. Next, the EN(Enable) pin of the LCD to the PB7 of the controller

1. At last the data pins(D0 to D7) of the LCD to the PC0 to PC7 of the controller

![LCD Display](assets/img/blog/2020/stm-lcd/pin.jpg){: width="834" height="453" }
_LCD Display_

## Software Part:

1. Install Keil software

1. Connect the STM32F446RE controller and update the driver

1. You can get the code from [here](https://github.com/MadeByBalaji/STM32F446RE/tree/main/BareMetal/LCD_Display)

1. You can change the contrast by varying the potentiometer. 

![End Result](assets/img/blog/2020/stm-lcd/display.jpeg){: width="585" height="1040" }
_End Result_