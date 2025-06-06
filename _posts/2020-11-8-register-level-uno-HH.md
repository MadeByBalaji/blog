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

![ATMEGA 168 Pin Mapping](assets\lib\blog\2020\register-level-uno\Atmega168PinMap.png){: width="609" height="704" }
_ATMEGA 168 Pin Mapping_

There are three types of  register

1. *DDR register*, it determines whether the pin is an INPUT or OUTPUT. 
1. *PORT register*, it controls whether the pin is HIGH or LOW. 
1. *PIN register*, reads the state of INPUT pins set to input with pinMode().


Now we will code in ArduinoIDE

```c
void setup() {
  // put your setup code here, to run once:
 DDRB |= 0x20; //pinMode(13,OUTPUT);
  /*
  DDRB means Port B Data Direction Register, which is set to 0b100000
  Here I am setting PIN 13 as OUTPUT by writing 1 on DDRB register
  */
}

void loop() {
  // put your main code here, to run repeatedly:
 PORTB |= 0x20; //digitalWrite(13,HIGH);
  /*
  PORTB means Data Register, which is set to 0b100000
  Here I am setting PIN 13 as HIGH or High voltage(+5) is passed to  that PIN
  */
  delay(1000);
 PORTB &= ~(0x20); //digitalWrite(13,LOW);
  /*
  PORTB means Data Register, which is set to 0b000000, so that other PINs are not modified
  Here I am setting PIN 13 as LOW or LOW voltage(GND) is passed to  that PIN
  */
  delay(1000);
}
```

DDRB means Port B Data Direction Register, which is set to 100000(in binary)

Here I am setting PIN 13 of Arduino as OUTPUT by writing 1 on the DDRB register. As we are using the DDR register on Port B it becomes DDRB.


PORTB means Data Register, which is set to 100000(in binary)
Here I am setting PIN 13 of Arduino that is the pin that has inbuild LED as HIGH or High voltage(+5) is passed to that PIN. As we are using the PORT register on Port B it becomes PORTB.


You can also get this code from Github [here](https://github.com/MadeByBalaji/Arduino/blob/master/BareMetalCode/LedBlink.ino)


Thanks...