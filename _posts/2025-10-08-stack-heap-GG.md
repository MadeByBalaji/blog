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

Let’s do a **full, clean, and crash-course explanation of stack and heap in C**, the way you can ace firmware interviews. I’ll keep it practical for embedded firmware.

---

## **1. What is Stack?**

* **Stack memory** is **automatic memory**.
* Used for: **local variables, function calls, return addresses**.
* Managed by **compiler**.
* LIFO (Last In, First Out) → last function called is first to return.
* **Size is usually small**, limited by OS / MCU.

**Example:**

```c
#include <stdio.h>

void func() {
    int a = 10; // stored in stack
    int b = 20; // stored in stack
    printf("%d %d\n", a, b);
}

int main() {
    func();
    return 0;
}
```

✅ Notes:

* Variables `a` and `b` exist **only during function execution**.
* Memory is automatically released when function exits.

---

### **Stack Pros & Cons**

| Pros                         | Cons                                         |
| ---------------------------- | -------------------------------------------- |
| Fast allocation/deallocation | Small size → can overflow (`stack overflow`) |
| No need to free manually     | Lifetime limited to function scope           |
| Managed by compiler          | Cannot resize dynamically                    |

---

## **2. What is Heap?**

* **Heap memory** is **dynamic memory**.
* Managed by the **programmer using `malloc` / `free`**.
* Used for: **dynamic data structures**, large arrays, buffers.
* Larger than stack but slower allocation.
* Lifetime **controlled manually**, exists until `free()` is called.

**Example:**

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *ptr = (int*)malloc(sizeof(int)); // allocate on heap
    if(ptr == NULL) {
        printf("Memory allocation failed\n");
        return 1;
    }
    *ptr = 100;
    printf("%d\n", *ptr);

    free(ptr); // release heap memory
    return 0;
}
```

✅ Notes:

* Heap memory persists **beyond function scope**.
* You **must free it manually**, or you get **memory leaks**.

---

### **Heap Pros & Cons**

| Pros                       | Cons                          |
| -------------------------- | ----------------------------- |
| Large memory pool          | Slower than stack             |
| Lifetime can be controlled | Programmer must free manually |
| Can allocate at runtime    | Fragmentation can occur       |

---

## **3. Stack vs Heap – Quick Comparison**

| Feature       | Stack                             | Heap                        |
| ------------- | --------------------------------- | --------------------------- |
| Allocation    | Automatic                         | Manual (`malloc`)           |
| Lifetime      | Function scope                    | Until `free()`              |
| Size          | Small                             | Large                       |
| Speed         | Fast                              | Slower                      |
| Memory Errors | Stack overflow                    | Memory leak / fragmentation |
| Storage       | Local variables, return addresses | Dynamic data, buffers       |

---

## **4. Common Interview Questions**

1. Difference between stack and heap.
2. What happens if stack overflows?
3. How to avoid memory leaks in heap?
4. When to use stack vs heap in firmware?
5. How does recursive function affect stack?

---

### **5. Firmware Tip**

* Prefer **stack** for small, temporary variables.
* Use **heap** for large buffers or structures whose size is not known at compile-time.
* In embedded, **avoid dynamic heap allocation in critical loops** because it can fragment memory over time.

---

Bro, if you want, I can make a **super easy diagram + code examples** showing **stack vs heap memory layout**, which helps you **visualize for interviews** and **never forget**.