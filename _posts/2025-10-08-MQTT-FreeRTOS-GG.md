---
title: How MQTT is used in FreeRTOS
description: How MQTT is used in FreeRTOS
date: 2025-10-08 15:21:00 -0530
categories: [Geeky Gossip]
tags: [protocol,interview,revision,mqtt]
image:
  path: /assets/img/blog/2025/howMQTTinFreeRTOS.png
  lqip: /assets/img/blog/2025/howMQTTinFreeRTOS.png
---

let’s walk through **how MQTT is typically implemented in FreeRTOS-based systems** (IoT devices, embedded controllers, etc.). This is a very **common interview + real project scenario** because MQTT is a lightweight publish/subscribe protocol and FreeRTOS is widely used in IoT stacks.

---

## **Basic Concept**

* **MQTT** = publish/subscribe protocol over TCP/IP.
* Needs:

  1. **TCP/IP stack** (like FreeRTOS+TCP or lwIP).
  2. **MQTT client library** (e.g., AWS IoT Device SDK, Eclipse Paho, FreeRTOS coreMQTT).
  3. **FreeRTOS tasks** to handle **networking, MQTT keep-alive, and application logic**.

---

## **Typical FreeRTOS Architecture for MQTT**

1. **Network Layer**

   * A task handles the TCP/IP connection to the broker.
   * Keep-alive packets are maintained (PINGREQ / PINGRESP).

2. **MQTT Task**

   * Runs the MQTT client library.
   * Handles **subscribe**, **publish**, and **callback dispatch**.

3. **Application Tasks**

   * Example: Sensor task publishes data.
   * Example: Control task subscribes to commands.

---

## **Example Flow**

1. **Initialization**

   * Bring up network (Wi-Fi/Ethernet).
   * Create MQTT client and connect to broker.

2. **Subscription**

   * Subscribe to topics (e.g., `"device/123/cmd"`).

3. **Publishing**

   * Application task posts messages (e.g., `"device/123/data"`).

4. **Message Handling**

   * Incoming messages are pushed to a FreeRTOS **queue** or trigger a **callback**.

---

## **Pseudo-Code in FreeRTOS Style**

```c
void mqttTask(void *pvParameters) {
    MQTTClient_t client;
    Network_t network;

    // 1. Connect to broker
    NetworkInit(&network);
    NetworkConnect(&network, "broker.hivemq.com", 1883);
    MQTTClientInit(&client, &network);

    // 2. Connect with client ID
    MQTTPacket_connectData connectData = MQTTPacket_connectData_initializer;
    connectData.clientID.cstring = "device123";
    MQTTConnect(&client, &connectData);

    // 3. Subscribe
    MQTTSubscribe(&client, "device/123/cmd", QOS1, messageHandler);

    // 4. Loop for processing
    while (1) {
        // Yield to handle incoming/outgoing packets
        MQTTYield(&client, 1000);

        // Example: Publish sensor data
        MQTTMessage msg;
        char payload[32];
        sprintf(payload, "Temp=%d", getTemp());

        msg.qos = QOS1;
        msg.retained = 0;
        msg.payload = payload;
        msg.payloadlen = strlen(payload);

        MQTTPublish(&client, "device/123/data", &msg);

        vTaskDelay(pdMS_TO_TICKS(5000)); // publish every 5 sec
    }
}

void messageHandler(MessageData *md) {
    MQTTMessage *msg = md->message;
    printf("Received: %.*s\n", msg->payloadlen, (char *)msg->payload);
    // Process command here
}
```

---

## **FreeRTOS Integration Points**

* **Tasks**: Separate tasks for MQTT, sensors, actuators.
* **Queues/Semaphores**: For inter-task communication (e.g., sensor task → MQTT task).
* **Memory**: Be careful with stack sizes (MQTT libraries often need bigger stacks).
* **Watchdog**: MQTT keep-alive ensures broker connection stays alive; use WDT for robustness.

---

## **Real-World Example**

* **AWS IoT + FreeRTOS** → uses `coreMQTT` library (optimized for embedded).
* **Eclipse Paho Embedded C** → simple, portable, widely used in smaller MCUs.
* **lwIP + FreeRTOS** → common for STM32, ESP32, NXP, etc.

---
