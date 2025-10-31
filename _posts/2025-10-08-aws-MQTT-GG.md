---
title: MQTT protocol steps
description: MQTT protocol steps
date: 2025-10-08 15:21:00 -0530
categories: [Geeky Gossip]
tags: [protocol,interview,revision,MQTT,aws]
image:
  path: /assets/img/blog/2025/3Protocol.png
  lqip: /assets/img/blog/2025/3Protocol.png
---

the **MQTT protocol steps** in a clean way. Think of MQTT as a **conversation between a client (device) and a broker (server)**.

---

## 1. **Connect**

* Client establishes a **TCP connection** with the broker (default port **1883**, or **8883** if TLS/SSL is used).
* Then sends an **MQTT CONNECT packet** with:

  * **Client ID** (unique name, e.g., `device123`).
  * Optional **username/password**.
  * **Keep Alive time** (heartbeat interval).
  * Optional **Will Message** (sent if client disconnects unexpectedly).

 Broker replies with **CONNACK** (Connection Acknowledgment).
If success → you’re “online”.

---

##  2. **Publish / Subscribe Setup**

* **Publish (PUB)**: Client sends a message to a **topic** (like a channel name).
  Example:
  Topic: `"sensor/temperature"`
  Message: `"25.5 C"`
* **Subscribe (SUB)**: Client tells broker what topics it wants to receive.
  Example: subscribe to `"device/123/cmd"` → broker forwards messages from that topic.

 Broker replies with **SUBACK** (subscription acknowledgment).

---

##  3. **Message Exchange**

Once subscribed:

* Other clients publish messages → broker forwards to subscribers.
* Client can also publish its own data.

Messages have **QoS (Quality of Service) levels**:

1. **QoS 0** – At most once (fire and forget).
2. **QoS 1** – At least once (broker confirms receipt).
3. **QoS 2** – Exactly once (more handshake, rare in small devices).

---

##  4. **Keep Alive / Ping**

* Client must send **PINGREQ** at intervals < keep-alive time (set during CONNECT).
* Broker replies with **PINGRESP**.
* If broker doesn’t receive ping or messages → assumes client is dead → may send Will Message.

---

##  5. **Disconnect**

* Client can send a **DISCONNECT packet** before closing TCP.
* If device dies suddenly (no DISCONNECT), broker uses keep-alive timeout to detect.

---

##  Sequence in Practice

Here’s a normal MQTT session:

1. **TCP connect** → Broker.
2. **CONNECT** → Broker.
3. **CONNACK** ← Broker.
4. **SUBSCRIBE** → `"device/123/cmd"`.
5. **SUBACK** ← Broker.
6. **PUBLISH** → `"device/123/data" : "Temp=25.3"`.
7. **PINGREQ** ↔ **PINGRESP** (every keep-alive).
8. **DISCONNECT** → Close connection cleanly.

---

## Visual Example (Sensor Device)

```text
[Device] --CONNECT--> [Broker]
[Broker] <--CONNACK-- [Device]

[Device] --SUBSCRIBE "cmd"--> [Broker]
[Broker] <--SUBACK------------- [Device]

[Device] --PUBLISH "data:25C"--> [Broker]
[Broker] --FORWARD "data:25C"--> [Subscribers]

[Device] --PINGREQ--> [Broker]
[Broker] <--PINGRESP-- [Device]

[Device] --DISCONNECT--> [Broker]
```

---

Bro, if you understand this flow, you can explain MQTT protocol **step by step in interviews**.