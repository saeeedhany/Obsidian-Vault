
# C String Library Functions Explained

This document provides a clean and detailed explanation of common string library functions in C.

## Including the String Library

To use string functions in C, include the `string.h` header:

```c
#include <string.h>
```

## 1. strcpy(dest, src)

**Purpose:** Copies the content of `src` into `dest`.

**Syntax:**
```c
char *strcpy(char *dest, const char *src);
```

**Notes:**
- `dest` must be large enough to hold the copied string.
- Copies the null terminator (`\0`) as well.

**Example:**
```c
char src[] = "Hello";
char dest[10];
strcpy(dest, src);
printf("%s\n", dest); // Output: Hello
```

## 2. strlen(str)

**Purpose:** Returns the length of the string (excluding the null terminator).

**Syntax:**
```c
size_t strlen(const char *str);
```

**Example:**
```c
char word[] = "World";
printf("%lu\n", strlen(word)); // Output: 5
```

## 3. strcat(dest, src)

**Purpose:** Appends `src` to the end of `dest`.

**Syntax:**
```c
char *strcat(char *dest, const char *src);
```

**Notes:**
- `dest` must be large enough to contain the resulting string.

**Example:**
```c
char dest[20] = "Hello, ";
char src[] = "world!";
strcat(dest, src);
printf("%s\n", dest); // Output: Hello, world!
```

## 4. strncat(dest, src, n)

**Purpose:** Appends the first `n` characters of `src` to `dest`.

**Syntax:**
```c
char *strncat(char *dest, const char *src, size_t n);
```

**Example:**
```c
char dest[20] = "Hello ";
char src[] = "Universe";
strncat(dest, src, 3);
printf("%s\n", dest); // Output: Hello Uni
```

## 5. strncmp(str1, str2, n)

**Purpose:** Compares the first `n` characters of two strings.

**Syntax:**
```c
int strncmp(const char *str1, const char *str2, size_t n);
```

**Return Values:**
- `0` if strings are equal.
- `< 0` if `str1` is less than `str2`.
- `> 0` if `str1` is greater than `str2`.

**Example:**
```c
char a[] = "apple";
char b[] = "apricot";
int result = strncmp(a, b, 2);
printf("%d\n", result); // Output: 0 (since "ap" == "ap")
```

## 6. strcmp(str1, str2)

**Purpose:** Compares two strings entirely.

**Syntax:**
```c
int strcmp(const char *str1, const char *str2);
```

**Example:**
```c
char a[] = "cat";
char b[] = "car";
printf("%d\n", strcmp(a, b)); // Output: > 0 since 't' > 'r'
```

## General Notes

- These functions work with `char` arrays (null-terminated strings).
- In sensitive situations, prefer `strncpy` and `strncat` over `strcpy` and `strcat` for safety.
