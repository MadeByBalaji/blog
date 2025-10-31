---
title: pattern printing in c
description: pattern printing in C
date: 2025-10-08 15:21:00 -0530
categories: [Geeky Gossip]
tags: [pattern,problems,interview,revision,c]
image:
  path: /assets/img/blog/2025/PatternPrintc.png
  lqip: /assets/img/blog/2025/PatternPrintc.png
---

Let’s do a **quick crash revision on pattern printing in C**. These are the classics interviewers love to throw at firmware/C devs.

---

## 1. Right-Angle Triangle

```c
#include <stdio.h>
int main() {
    int n = 5;
    for(int i=1;i<=n;i++){
        for(int j=1;j<=i;j++){
            printf("* ");
        }
        printf("\n");
    }
}
```

Output:

```
* 
* * 
* * * 
* * * * 
* * * * * 
```

---

## 2. Inverted Triangle

```c
#include <stdio.h>
int main() {
    int n = 5;
    for(int i=n;i>=1;i--){
        for(int j=1;j<=i;j++){
            printf("* ");
        }
        printf("\n");
    }
}
```

Output:

```
* * * * * 
* * * * 
* * * 
* * 
* 
```

---

## 3. Pyramid

```c
#include <stdio.h>
int main() {
    int n=5;
    for(int i=1;i<=n;i++){
        for(int s=1;s<=n-i;s++) printf(" ");  // spaces
        for(int j=1;j<=2*i-1;j++) printf("*");
        printf("\n");
    }
}
```

Output:

```
    *    
   ***   
  *****  
 ******* 
*********
```

---

## 4. Diamond

```c
#include <stdio.h>
int main() {
    int n=5;
    // upper half
    for(int i=1;i<=n;i++){
        for(int s=1;s<=n-i;s++) printf(" ");
        for(int j=1;j<=2*i-1;j++) printf("*");
        printf("\n");
    }
    // lower half
    for(int i=n-1;i>=1;i--){
        for(int s=1;s<=n-i;s++) printf(" ");
        for(int j=1;j<=2*i-1;j++) printf("*");
        printf("\n");
    }
}
```

Output:

```
    *    
   ***   
  *****  
 ******* 
*********
 ******* 
  *****  
   ***   
    *    
```

---

## 5. Numbers Triangle

```c
#include <stdio.h>
int main() {
    int n=5;
    for(int i=1;i<=n;i++){
        for(int j=1;j<=i;j++){
            printf("%d ", j);
        }
        printf("\n");
    }
}
```

Output:

```
1 
1 2 
1 2 3 
1 2 3 4 
1 2 3 4 5 
```

---

Key takeaways for revision:

* **Outer loop → rows (lines).**
* **Inner loop(s) → spaces & symbols/numbers.**
* Think in terms of:

  1. Spaces before the symbol
  2. Printing the symbol (or number)

---