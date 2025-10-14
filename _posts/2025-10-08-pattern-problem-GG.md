---
title: pattern printing in c
description: pattern printing in C
date: 2025-10-08 15:21:00 -0530
categories: [Geeky Gossip]
tags: [protocol,interview,revision]
image:
  path: /assets/img/blog/2025/3Protocol.png
  lqip: /assets/img/blog/2025/3Protocol.png
---

Got you, bro í ½í¸Ž Letâ€™s do a **quick crash revision on pattern printing in C**. These are the classics interviewers love to throw at firmware/C devs.

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

í ½í±‰ Output:

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

í ½í±‰ Output:

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

í ½í±‰ Output:

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

í ½í±‰ Output:

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

í ½í±‰ Output:

```
1 
1 2 
1 2 3 
1 2 3 4 
1 2 3 4 5 
```

---

âš¡ Key takeaways for revision:

* **Outer loop â†’ rows (lines).**
* **Inner loop(s) â†’ spaces & symbols/numbers.**
* Think in terms of:

  1. Spaces before the symbol
  2. Printing the symbol (or number)

---

Want me to give you a **set of 5 practice pattern problems** (from easy â†’ tricky) so you can test yourself today?
