---
title: Frame format of 3-Important protocol
description: There are 3 important protocol in embedded systems, this blog explains them
date: 2025-10-07 15:21:00 -0530
categories: [Geeky Gossip]
tags: [protocol,interview,revision]
image:
  path: /assets/img/blog/2025/3Protocol.png
  lqip: /assets/img/blog/2025/3Protocol.png
---

These three — UART, I²C, and SPI — are the most commonly asked in embedded interviews. Let’s go step by step and focus on frame format for each:

---

## UART (Universal Asynchronous Receiver Transmitter)

### Frame Format

```
| Start bit (0) | Data bits (5–9) | Optional Parity bit | Stop bit (1 or 2) |
```

So, one byte of user data takes around **10 bits** to transmit.

---

### Speed

| Parameter         | Typical Value                          |
| ----------------- | -------------------------------------- |
| Baud Rate         | 9600 – 115200 bps (standard)           |
| Max (practically) | ~1 Mbps (depends on MCU, cable, noise) |

* UART is **asynchronous** → needs precise baud rate match between TX and RX.
* Slower compared to SPI and I²C.

---

### Data Amount

* Data is sent **byte-by-byte** (8 bits + overhead).
* There’s **no fixed limit** — it depends on how long the receiver keeps reading.
* Commonly used for **command-response** or **logging**, not large data streams.

---

## I²C (Inter-Integrated Circuit)

### Frame Format

Each transmission has:

```
| Start | Address (7/10 bit) | R/W bit | ACK | Data byte | ACK | ... | Stop |
```

* Data sent in **bytes (8 bits)**.
* Each byte followed by **ACK/NACK** from receiver.

---

### Speed

| Mode            | Max Clock Speed       |
| --------------- | --------------------- |
| Standard Mode   | 100 kHz               |
| Fast Mode       | 400 kHz               |
| Fast Mode Plus  | 1 MHz                 |
| High-Speed Mode | 3.4 MHz               |
| Ultra-Fast Mode | 5 MHz (one-direction) |

* **Speed limited by open-drain design** (shared bus with pull-ups).
* Ideal for **short-distance, low-speed sensors**.

---

### Data Amount

* Typically used for **control data**, not bulk streaming.
* Usually 1–32 bytes per transaction (some chips support burst reads up to 255 bytes).
* Max transaction length is **protocol-dependent**, not hardware-limited.

---

## SPI (Serial Peripheral Interface)

### Frame Format

SPI doesn’t define a fixed frame — it’s purely:

```
MOSI ↔ MISO synchronized with SCLK (CPOL/CPHA define timing)
```

* One byte = 8 clock cycles (or configurable to 16/32 bits in some MCUs).
* Full-duplex (send and receive simultaneously).

---

### Speed

| Mode                   | Typical Speed     |
| ---------------------- | ----------------- |
| Low-End Devices        | 1–5 MHz           |
| Flash Memory, Displays | 10–50 MHz         |
| High-Performance MCUs  | 100+ MHz possible |

SPI is **much faster** because:

* No ACK/NACK bits.
* Dedicated lines (no bus sharing).
* Continuous streaming possible.

---

### Data Amount

* Can stream **unlimited bytes** — depends on chip select and buffer size.
* Used for **high-speed data transfer** (displays, sensors, memory, ADC/DAC).

---

## Quick Comparison Summary

| Feature        | **UART**             | **I²C**                   | **SPI**                     |
| -------------- | -------------------- | ------------------------- | --------------------------- |
| Lines Used     | 2 (TX, RX)           | 2 (SCL, SDA)              | 4 (MISO, MOSI, SCLK, SS)    |
| Type           | Asynchronous         | Synchronous (half-duplex) | Synchronous (full-duplex)   |
| Master/Slave   | Peer-to-peer         | Multi-master possible     | Single master, multi-slave  |
| Data per frame | 8 bits + overhead    | 8 bits + ACK/NACK         | Configurable (8/16/32 bits) |
| Max Speed      | ~1 Mbps              | 400 kHz–5 MHz             | 50–100+ MHz                 |
| Typical Use    | Logging, Serial Comm | Sensors, EEPROM, RTC      | Displays, Flash, ADC/DAC    |
| Distance       | Long (meters)        | Short (few cm)            | Very short (on PCB)         |
| Throughput     | Low                  | Medium                    | Very High                   |
| Frame Format | Start/Data/Parity/Stop | Start/Addr/RW/ACK/Data/Stop   | CS + Data (per clock)    |


---

## Speed Perspective (approximate)

Let’s see how long it takes to send **1 KB (1024 bytes)** of data:

| Protocol          | Typical Speed | Time to send 1 KB |
| ----------------- | ------------- | ----------------- |
| UART @ 115200 bps | 0.115 Mbps    | ~71 ms            |
| I²C @ 400 kHz     | 0.4 Mbps      | ~20 ms            |
| SPI @ 10 MHz      | 10 Mbps       | ~0.8 ms           |

→ So SPI is around **25× faster than I²C** and **90× faster than UART** at those speeds.

---

## Rule of Thumb

| Application                       | Choose |
| --------------------------------- | ------ |
| Debugging, Serial Consoles        | UART   |
| Multiple slow sensors on same bus | I²C    |
| Fast ADCs, Displays, Memory chips | SPI    |

---
