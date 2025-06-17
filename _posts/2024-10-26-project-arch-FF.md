---
title: Understanding the Project Architecture
description:  A Deep Dive into the LedBlink Project
date: 2024-09-09 11:33:00 -0530
categories: [Firmware Fortress]
tags: [linkerscript,stm,cubeide,arch]
image:
  path: /assets/img/blog/2024/stm-project/arch.jpg
  lqip: /assets/img/blog/2024/stm-project/arch.jpg
---

# Understanding the LedBlink Project in STM32CubeIDE

In this post, we'll explore the **LedBlink project** — a simple LED blinking application using the **HAL library** on an STM32F4 microcontroller. Along the way, we’ll cover the **project architecture**, **build process**, and the **role of linker scripts**, giving you a full tour of how everything comes together to build the final firmware.

---

## LedBlink Project Overview

The project lives in this path:

```
STM32F446RE/WorkSpace/LedBlink
```

It is designed to blink the User Green LED (LD2) connected to **PA5** on the STM32F4 board. The HAL library abstracts the low-level details of pin control.

---

## Source Code Logic

At its core, the code toggles a GPIO pin (PA5) inside an infinite `while(1)` loop. A delay is added between each toggle to create the blinking effect.

---

## Project Architecture

Once the project is cleaned, you’ll notice **four folders and four files** remain. Let’s break them down:

### 1. Includes

Not a real folder, but a virtual group in STM32CubeIDE. It lists all include paths configured here:

```
Project Properties → C/C++ Build → Settings → Tool Settings → MCU GCC Compiler → Include Paths
```

These paths are critical for locating header files during compilation.

### 2. Core

Contains:

* `main.c` and `main.h`
* Assembly startup file that handles the MCU’s boot process

### 3. Drivers

Holds both:

* **HAL (Hardware Abstraction Layer)** drivers
* **CMSIS** core drivers

These drivers handle GPIO, clock config, interrupts, and peripheral management.

### 4. Debug

Generated during builds. Contains:

* Temporary object files: `.o`, `.d`, `.su`
* Output binaries: `.elf`, `.hex`, `.bin`, `.list`
* The `Makefile` used for building

---

## Cleaning the Project

Cleaning removes all temporary build artifacts and is useful for starting fresh.

### What happens during clean:

1. The `make clean` target is triggered.
2. It deletes `.o`, `.d`, `.cyclo`, `.hex`, `.elf`, etc.
3. Use **Git Bash** instead of Windows CMD to run these UNIX-style commands smoothly.

---

## Build Process Breakdown

### 1. The Compiler

The compiler used is `arm-none-eabi-gcc`. Since the Makefile uses UNIX-like syntax, running it in **Windows CMD** might fail. Use **Git Bash** or **MSYS2** for a smoother experience.

### 2. Include Paths

STM32CubeIDE handles them automatically. But if you're building manually, make sure to pass the correct `-I` include flags (these are shown under the "Includes" section inside the IDE).

### 3. Makefile Flow

When you hit **Build**, here’s what happens:

* The `all` target is invoked.
* It depends on `main-build`.
* `main-build` builds `LedBlink.elf` and triggers `secondary-outputs`.

### 4. Building the ELF File

`LedBlink.elf` is the main firmware image. Once it’s built, you’ll see:

```
Finished building target: LedBlink.elf
```

### 5. Memory Size Display

The `arm-none-eabi-size` tool prints memory usage:

```
text	   data	    bss	    dec	    hex	  filename
10216	     20	   1708	  11944	   2ea8	LedBlink.elf
```

* `.text` = Flash usage
* `.data` and `.bss` = RAM usage

### 6. Generating Secondary Outputs

Once ELF is built, more outputs are generated:

* `LedBlink.hex`: for flashing
* `LedBlink.list`: disassembly
* `default.size.stdout`: size report

---

## What Are Secondary Outputs?

The `secondary-outputs` target in the Makefile is responsible for:

* Calling `arm-none-eabi-size`
* Ensuring size metrics are reported
* Building extra file formats from the `.elf`

This step helps developers keep track of memory usage and binary sizes — critical in resource-constrained environments.

---

## Conclusion

The **LedBlink project** is a great entry point into STM32 development with HAL and STM32CubeIDE. It teaches you:

* Basic HAL usage
* How project architecture is laid out
* How cleaning and building works under the hood
* Where the linker script fits in

Understanding this pipeline gives you a strong foundation to tackle more advanced embedded firmware tasks.

---

Want to go deeper into linker scripts or how startup files work?
Check out my post on:

[Understanding the Linker Script: A Deep Dive into the LedBlink Project](https://balajimail9.wixsite.com/blog/post/understanding-the-linker-script-a-deep-dive-into-the-ledblink-project)

Or hit me up with your next embedded topic idea — I’m always building, always blinking!
