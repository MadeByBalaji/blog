---
title: Schedulers in RTOS
description: Schedulers in RTOS
date: 2025-10-08 15:21:00 -0530
categories: [Geeky Gossip]
tags: [protocol,interview,revision]
image:
  path: /assets/img/blog/2025/3Protocol.png
  lqip: /assets/img/blog/2025/3Protocol.png
---

Nice Bro, letâ€™s go deep into **Schedulers in RTOS**.
Think of scheduler as the **traffic police** of the CPU â€“ it decides **which task runs and when**.

---

## í ½í´¹ What is a Scheduler?

* In RTOS, multiple tasks exist, but **only one runs on CPU at a time**.
* The **scheduler** decides which task gets CPU based on priority, state, and algorithm.
* FreeRTOS uses a **priority-based preemptive scheduler** (but can be configured).

---

## í ½í´¹ Types of Schedulers in RTOS

### 1. **Cooperative Scheduling**

* A running task **must yield** (give up CPU) voluntarily.
* No preemption â€“ task runs until it finishes or calls `taskYIELD()`.
* Simple but risky: if a task **never yields**, others starve.

**Example (FreeRTOS with `configUSE_PREEMPTION=0`):**

```c
for(;;)
{
    // Do work
    taskYIELD(); // must call this to let others run
}
```

---

### 2. **Preemptive Scheduling**

* RTOS **forces context switch** if a higher-priority task becomes ready.
* Ensures real-time responsiveness.
* Default in FreeRTOS (`configUSE_PREEMPTION=1`).

---

### 3. **Round Robin Scheduling (within same priority)**

* If multiple tasks share **same priority**, FreeRTOS gives CPU in **time slices**.
* Controlled by `configUSE_TIME_SLICING`.

**Example:**

* Task A and Task B both priority 2.
* They take turns in running when time slice expires.

---

### 4. **Priority-Based Scheduling (Main type in FreeRTOS)**

* Always runs the **highest priority ready task**.
* If multiple with same priority â†’ round robin.

---

### 5. **Rate Monotonic Scheduling (RMS)**

* A fixed-priority algorithm:

  * **Shorter period task â†’ higher priority**.
* Common in hard real-time systems.
* FreeRTOS doesnâ€™t implement RMS directly, but you can assign priorities that way.

---

### 6. **Earliest Deadline First (EDF)**

* Dynamic priority: task with the **earliest deadline runs first**.
* Not built into FreeRTOS, but possible with custom scheduler.
* Used in **hard real-time** apps like medical devices, automotive.

---

## í ½í´¹ Summary Table

| Scheduler Type                | Preemption          | Who decides CPU use?          | Use Case                              |
| ----------------------------- | ------------------- | ----------------------------- | ------------------------------------- |
| Cooperative                   | No                  | Task itself                   | Simpler, non-critical apps            |
| Preemptive (FreeRTOS)         | Yes                 | Scheduler (priority)          | Most RTOS apps                        |
| Round Robin                   | Yes (same priority) | Scheduler (time slice)        | Fairness among same-level tasks       |
| Rate Monotonic (RMS)          | Yes                 | Fixed priority (period-based) | Hard real-time                        |
| Earliest Deadline First (EDF) | Yes                 | Dynamic deadline-based        | Hard real-time with varying deadlines |

---

í ½í±‰ In **FreeRTOS interviews**, they usually expect you to know:

* **Preemptive vs Cooperative**
* **Round robin for same priority tasks**
* How **time slicing** works

---

Do you want me to also show a **diagram of task states + scheduler decision-making flow** (Ready â†’ Running â†’ Blocked â†’ Suspended)? Thatâ€™ll lock this concept in your head for interviews.
