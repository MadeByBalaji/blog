---
title: Mini-Camera using RaspberryPie-3 MODB+
description: Here in this Project I made a working mini-camera using RaspberryPie-3 MODB+
date: 2020-11-05 10:20:00 -0530
categories: [Hobbyist Haven]
tags: [python,raspberrypie]
image:
  path: /assets/img/blog/2020/camera-pi/overview.jpg
  lqip: /assets/img/blog/2020/camera-pi/overview.jpg
---

## Components:

1. RaspberryPi-3MODB [link](https://www.amazon.in/Raspberry-Pi-Model-RASP-PI-3-Motherboard/dp/B01CD5VC92/ref=sr_1_3?dchild=1&keywords=raspberry+pi+3&qid=1604323896&sr=8-3)

1. RaspberryPi Camera [link](https://www.amazon.in/Raspberry-Pi-Camera-Board/dp/B00L1FOIIS/ref=sr_1_2?dchild=1&keywords=raspberry+pi+camera&qid=1604324011&sr=8-2)

1. Push Button [link](https://www.amazon.in/switch-11x11x4-3MM-Tactile-Button-Self-Reset/dp/B07MDH66DN/ref=sr_1_1?dchild=1&keywords=button+for+arduino&qid=1604324082&sr=8-1)

1. Breadboard [link](https://www.amazon.in/Generic-Elementz-Solderless-Piecesb-Circuit/dp/B00MC1CCZQ/ref=sr_1_3?dchild=1&keywords=breadboard&qid=1604324184&sr=8-3&th=1)

1. Jumper wires [link](https://www.amazon.in/ApTechDeals-Jumper-Female-breadboard-jumper/dp/B074J9CPV3/ref=sr_1_2_mod_primary_lightning_deal?crid=25YR2Z8ZGWY72&dchild=1&keywords=jumper+wires+for+arduino&qid=1604324158&sbo=Tc8eqSFhUl4VwMzbE4fw%2Fw%3D%3D&smid=AT95IG9ONZD7S&sprefix=jumper%2Caps%2C434&sr=8-2)

## Working:

1. I used Debian OS for this project downloaded from [here](https://www.raspberrypi.com/software/s)

1. Flash the image to an SD Card above 4GB of size using [balena](https://etcher.balena.io/)

1. After Downloading, connect camera and button
 
1. Camera needs to be connected to CSI camera connector.
 
1. One terminal of the button is connected to GPIO21 and other to GND pin of RaspberryPi

1. Open ThonnyIDE in RaspberryPi

1. Write this code or get it from Github [here](https://github.com/MadeByBalaji/RaspberryPi/blob/main/Python/gpiozero/Camera/ButtonCapture/cam.py)

```python
from gpiozero import Button
from picamera import PiCamera
button=Button(21)
camera = PiCamera()
camera.start_preview()
frame=1
while True:
    button.wait_for_press()
    camera.capture('/home/pi/frame%03d.jpg'%frame)
    frame+=1Use this code 
```  

8. Preview of the Camera will appear on the display.

1. Press the Push Button to take photo

1. The photo will be saved in the location  

```text
/home/pi/
```

1. Some of the photos

![frame001](assets/img/blog/2020/camera-pi/frame001.jpg){: width="1360" height="768" }
_frame001_

![frame002](assets/img/blog/2020/camera-pi/frame002.jpg){: width="1360" height="768" }
_frame002_


Thanks...