---
title: From 0x0. To main()
description: Overview of where the MCU starts running.
date: 2024-09-09 11:33:00 -0530
categories: [Firmware Fortress]
tags: [linkerscript,startup]
image:
  path: /assets/img/blog/2024/from-main/letter.jpg
  lqip: /assets/img/blog/2024/from-main/letter.jpg
---

In a typical embedded system, after the device powers on or resets, the process that takes the firmware execution from address `0x0` to the `main()` function involves several stages, including initialization and setting up the runtime environment.

Here's an overview of the sequence:

---

## 1. Reset Vector (Entry Point at 0x0)

When a microcontroller powers up or resets, the Program Counter (PC) is set to the reset vector, which is typically the memory location `0x0`. On ARM Cortex-M microcontrollers, this is the start of the vector table.

The vector table begins with the initial stack pointer value at address `0x0` and the reset handler address at address `0x4`.

---

## 2. Reset Handler

The reset handler is a function specified by the vector table (stored at address `0x4`).

The reset handler is typically written in assembly or C. It sets up essential configurations, like:

- Initializing the stack pointer.
- Copying the initialized data section from Flash to SRAM (for global/static variables initialized with values).
- Zeroing out the BSS section (uninitialized global/static variables).
- Calling system-specific hardware initialization routines (if necessary).

---

## 3. System Initialization (Optional)

The reset handler might call additional system startup routines to configure:

- Hardware peripherals
- Clock systems
- Interrupt systems (if needed)

It might also perform basic system checks (such as testing memory regions).

---

## 4. Calling `main()`

Once the system is initialized, the reset handler typically jumps to the `main()` function.

This is where the actual application code starts executing.

---

## High-Level Steps

- **Address 0x0**: Initial stack pointer value (for managing the stack).
- **Address 0x4**: Reset handler address (entry point for initialization).
- **Reset handler**: Initializes memory (stack, BSS, data sections), calls necessary system setup routines.
- **Jump to `main()`**: Once setup is complete, the `main()` function is invoked, and the application starts running.

---

## Example Code Overview

A typical startup sequence might look like this (simplified):

### Vector Table (Cortex-M)

```c
__attribute__((section(".isr_vector")))
const uint32_t vector_table[] = {

    (uint32_t)&_initial_stack_pointer,  // Stack pointer ( MSP ) at address 0x0

    (uint32_t)&Reset_Handler            // Reset handler at address 0x4

    // Other interrupt handlers...

};
```

## Reset Handler

```c
void Reset_Handler(void)
{
    // 1. Initialize data section
    extern uint32_t _sdata, _edata, _la_data;

    for (uint32_t *pDest = &_sdata, *pSrc = &_la_data; pDest < &_edata;) {
        *pDest++ = *pSrc++;
    }

    // 2. Zero out BSS section
    extern uint32_t _sbss, _ebss;

    for (uint32_t *pDest = &_sbss; pDest < &_ebss;) {
        *pDest++ = 0;
    }

    // 3. Call the system initialization functions (optional)
    SystemInit();

    // 4. Call main
    main();  // Now jumps to the main() function
}
```


## Recap

The firmware execution starts from address 0x0, proceeds to the reset handler, where system initialization happens, and finally jumps to the main() function where the magic happens.

The entire process is set up by the linker script and startup code provided for the specific microcontroller architecture—many times by the manufacturer itself.