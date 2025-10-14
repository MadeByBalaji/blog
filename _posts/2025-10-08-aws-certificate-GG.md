---
title: SPI modes
description: Let’s break down SPI modes slowly and cleanly from physical signals, timing, interpretation, real MCU usage.
date: 2025-10-08 15:21:00 -0530
categories: [Geeky Gossip]
tags: [protocol,interview,revision]
image:
  path: /assets/img/blog/2025/3Protocol.png
  lqip: /assets/img/blog/2025/3Protocol.png
---

Ah got it — you were asking about **AWS IoT Greengrass + MQTT** earlier, and I only explained the service flow but skipped the **certificate** part. Let’s cover that clearly:

---

### Why certificates are needed

* MQTT itself can run plain (no security) or over TLS.
* In **AWS IoT Core and Greengrass**, **all device communication is secured** using **X.509 certificates**.
* These certificates are used for **authentication** (who you are) and **encryption** (secure channel).
* Without a certificate, your device cannot connect to AWS IoT Core using MQTT.

---

### What you need for MQTT with AWS IoT

1. **AWS IoT Core (service)**

   * Manages MQTT broker in the cloud.

2. **X.509 Certificates + Keys**

   * Each device (IoT thing) needs:

     * A **device certificate** (X.509)
     * A **private key**
     * AWS **root CA certificate** (to verify AWS endpoint)
   * These are provisioned in the AWS console or via CLI.

3. **IoT Policy**

   * Attached to the certificate. Defines what MQTT actions (`connect`, `publish`, `subscribe`) the device can do.

4. **Greengrass Core** (optional if edge needed)

   * If you’re running Greengrass Core on a device, it too needs its own **certificate + private key** to talk with AWS IoT Core.

---

### Flow in short

* Device → connects over MQTT to AWS IoT endpoint.
* During TLS handshake:

  * Device sends its **certificate**.
  * AWS verifies it against its registry.
* If valid + policy allows → connection established.

---

✅ So the missing piece: **You always need an AWS IoT certificate (X.509) and IoT policy attached to it to use MQTT with AWS IoT Core or Greengrass.**

---

Do you want me to show you **step-by-step how to generate and attach certificates for a device in AWS IoT**, or just a high-level summary of the flow is enough?
