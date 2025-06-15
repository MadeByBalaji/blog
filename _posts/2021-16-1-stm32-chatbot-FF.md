---
title: Terminal based Chat Bot using STM32
description: In this post, DS1307 is used as RTC and it is connected to STM32F446RE using I2C.
date: 2021-01-16 11:33:00 -0530
categories: [Firmware Fortress]
tags: [chatbot,uart,stm32f446re]
image:
  path: /assets/img/blog/2021/stm-bot/overview.jpg
  lqip: /assets/img/blog/2021/stm-bot/overview.jpg
---

## Components:
1. STM32F446RE as controller [link](https://www.amazon.in/NUCLEO-F446RE-STM32F446RET6-development-integrates-XYG-Study/dp/B014IXUB1M/ref=sr_1_1?crid=3FAQAJN6X1FWI&dchild=1&keywords=stm32f446re&qid=1604331292&sprefix=stm32f446%2Caps%2C707&sr=8-1)

## Hardware Part:

1. Here I used STM32F446RE as the main controller and using USART2 for Read and Write in the Terminal

1. There is no external circuit in this project

![Begin](assets/img/blog/2021/stm-bot/begin.png){: width="372" height="110" }
_Chat overview 1_

## Software Part:

1. After connecting the  STM32F446RE with the target now, connect to the computer where Keil uVision v5 is installed.

1. You can get the code from here

1. Using TeraTerm software you can find the messages, by giving the correct Port.

![End](assets/img/blog/2021/stm-bot/end.png){: width="382" height="204" }
_Chat overview 2_