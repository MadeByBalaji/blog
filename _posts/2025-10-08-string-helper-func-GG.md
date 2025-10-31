---
title: String Helper Functions
description: String Helper Functions
date: 2025-10-08 15:21:00 -0530
categories: [Geeky Gossip]
tags: [protocol,interview,revision,string,c]
image:
  path: /assets/img/blog/2025/StringHelperFunction.png
  lqip: /assets/img/blog/2025/StringHelperFunction.png
---

let’s do a **quick recap of important C string helper functions** from `<string.h>`. These are the ones you’ll actually use a lot in firmware / interviews.

---

### **1. String Length**

```c
size_t strlen(const char *str);
```

Returns length of string (not counting `\0`).

```c
char s[] = "Hello";
printf("%zu\n", strlen(s));  // 5
```

---

### **2. Copying Strings**

```c
char *strcpy(char *dest, const char *src);
char *strncpy(char *dest, const char *src, size_t n);
```

 `strcpy` copies whole string, `strncpy` limits to `n` chars.

```c
char src[] = "World";
char dest[10];
strcpy(dest, src);   // dest = "World"
```

Be careful: `strcpy` can overflow buffer. Use `strncpy` for safety.

---

### **3. Concatenation**

```c
char *strcat(char *dest, const char *src);
char *strncat(char *dest, const char *src, size_t n);
```

Appends `src` to `dest`.

```c
char s[20] = "Hello ";
strcat(s, "World");  // s = "Hello World"
```

---

### **4. Comparison**

```c
int strcmp(const char *s1, const char *s2);
int strncmp(const char *s1, const char *s2, size_t n);
```

Returns `0` if equal, `<0` if s1<s2, `>0` if s1>s2.

```c
printf("%d\n", strcmp("abc","abc")); // 0
printf("%d\n", strcmp("abc","abd")); // -1
```

---

### **5. Search**

* **Find first occurrence of character**:

```c
char *strchr(const char *str, int c);
```

```c
char *p = strchr("hello", 'e'); // points to "ello"
```

* **Find last occurrence of character**:

```c
char *strrchr(const char *str, int c);
```

* **Find substring**:

```c
char *strstr(const char *haystack, const char *needle);
```

```c
char *p = strstr("hello world", "world"); // points to "world"
```

---

### **6. Tokenize**

```c
char *strtok(char *str, const char *delim);
```

Splits string into tokens.

```c
char s[] = "red,green,blue";
char *token = strtok(s, ",");
while (token != NULL) {
    printf("%s\n", token);
    token = strtok(NULL, ",");
}
```

Output:

```
red
green
blue
```

---

### **7. Memory Helpers**

These work on raw memory, not just strings:

```c
void *memcpy(void *dest, const void *src, size_t n);
void *memmove(void *dest, const void *src, size_t n);
void *memset(void *str, int c, size_t n);
int memcmp(const void *s1, const void *s2, size_t n);
```

* `memcpy` – fast copy (no overlap).
* `memmove` – safe copy (handles overlap).
* `memset` – fill memory with value.
* `memcmp` – compare memory blocks.

---

**Quick Tricks:**

* Use `strlen` + `strcpy`/`strncpy` to duplicate.
* Use `strtok` to parse UART strings / CSV.
* Use `memset` to clear structs (`memset(&myStruct, 0, sizeof(myStruct))`).
* Use `strstr` to detect commands (`if (strstr(rxBuffer, "START")) { ... }`).

---
