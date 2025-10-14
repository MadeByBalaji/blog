---
title: Relation between array and pointers in c
description: Relation between array and pointers in c
date: 2025-10-08 15:21:00 -0530
categories: [Geeky Gossip]
tags: [protocol,interview,revision]
image:
  path: /assets/img/blog/2025/3Protocol.png
  lqip: /assets/img/blog/2025/3Protocol.png
---

Arrays, pointers, and function pointers are *the* brain-bending but powerful parts of C. I‚Äôll give you a crisp **list of important things**, with small code examples and why they matter in real-world firmware/embedded dev.

---

### 1. **Array ‚Üî Pointer relationship**

* In most expressions, an array name ‚Äúdecays‚Äù to a pointer to its first element.

```c
int arr[] = {10, 20, 30};
int *p = arr;        // arr decays to &arr[0]
printf("%d\n", *(p+1)); // 20
```

‚ö° But note: `sizeof(arr)` is different from `sizeof(p)`.

```c
printf("%zu\n", sizeof(arr)); // 12 (3 * 4 bytes)
printf("%zu\n", sizeof(p));   // 8 on 64-bit machine
```

Ì†ΩÌ±â Embedded trick: `sizeof` is your friend to know array length at compile-time.

---

### 2. **Passing arrays to functions**

```c
void printArr(int *a, int n) {
    for(int i=0; i<n; i++) printf("%d ", a[i]);
}
int main() {
    int arr[5] = {1,2,3,4,5};
    printArr(arr, 5); // arr passed as pointer
}
```

‚ö° Why? Because array ‚Äúdecays‚Äù to pointer.
But compiler loses size info ‚Üí you **must pass length separately**.

---

### 3. **Pointer to whole array**

Difference between:

```c
int arr[5];
int *p = arr;       // pointer to int
int (*q)[5] = &arr; // pointer to entire array
```

* `p` increments by one int.
* `q` increments by 5 ints (entire block).
  Useful when dealing with multidimensional arrays.

---

### 4. **2D arrays vs pointers**

```c
int a[2][3] = {{1,2,3},{4,5,6}};
int (*p)[3] = a;  // pointer to array of 3 ints
printf("%d\n", p[1][2]); // 6
```

‚ö° In firmware, this is handy when storing lookup tables (e.g., PWM duty cycles, ADC calibration tables).

---

### 5. **Pointer arithmetic**

```c
int arr[] = {10,20,30,40};
int *p = arr;
printf("%d\n", *(p+2)); // 30
```

‚ö° Embedded case: walking through a buffer (UART receive buffer, DMA buffer, etc).

---

### 6. **Function pointers (Ì†ΩÌ¥• real firmware use)**

Declare:

```c
int add(int a, int b) { return a+b; }
int sub(int a, int b) { return a-b; }

int main() {
    int (*fp)(int,int); // function pointer
    fp = add;
    printf("%d\n", fp(3,4)); // 7
    fp = sub;
    printf("%d\n", fp(3,4)); // -1
}
```

‚ö° Use cases in firmware:

* Jump tables (replace huge `switch`).
* ISR callbacks (like HAL_UART_RxCpltCallback in STM32 HAL).
* State machine design.

---

### 7. **Array of function pointers**

Perfect for menu-driven systems or state machines:

```c
void stateA() { printf("A\n"); }
void stateB() { printf("B\n"); }

void (*states[2])() = {stateA, stateB};

int main() {
    states[0](); // A
    states[1](); // B
}
```

‚ö° This is gold in **RTOS task tables, command handlers, or protocol parsers**.

---

### 8. **Pointer to function returning pointer**

```c
int* fun(int *x) { return x; }
int* (*fp)(int*) = fun;
```

‚ö° Looks scary, but sometimes needed when working with library APIs or driver HAL layers.

---

### 9. **Const correctness with arrays & pointers**

```c
const int *p;   // pointer to const data (can‚Äôt change *p)
int *const q;   // const pointer (can‚Äôt change q itself)
```

‚ö° Used in firmware when you don‚Äôt want ISRs or tasks to corrupt lookup tables.

---

### 10. **Volatile with arrays/pointers**

```c
volatile uint32_t *reg = (uint32_t*)0x40021000; 
*reg = 1;  // directly writing to peripheral register
```

‚ö° **Must-know** in embedded: `volatile` stops compiler from optimizing out hardware register access.

---
