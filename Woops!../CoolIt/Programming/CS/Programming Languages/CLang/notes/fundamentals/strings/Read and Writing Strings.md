# C String Input/Output Functions Guide

## Output Functions

### printf

- **Purpose**: Formats and prints data to stdout (screen)
- **Syntax**: `printf(format_string, arg1, arg2, ...)`
- **Features**:
    - Uses format specifiers (%s, %d, %f, etc.)
    - Combines text and variables
    - Doesn't add a newline automatically
    - Requires stdio.h
- **Example**: `printf("Hello %s, you are %d years old", name, age);`

### puts

- **Purpose**: Outputs a string to stdout
- **Syntax**: `puts(string);`
- **Features**:
    - Automatically adds a newline
    - Cannot format multiple variables
    - Slightly faster than printf for simple string output
    - Simpler syntax than printf
- **Example**: `puts("Hello world");`

### putchar

- **Purpose**: Outputs a single character to stdout
- **Syntax**: `putchar(character);`
- **Features**:
    - Simple syntax
    - Often used in loops to output one character at a time
    - Returns the character written, or EOF on error
- **Example**: `putchar('A');` or `putchar(c);`

#### Using putchar for printing strings

Although putchar is designed to print a single character, you can use it in a loop to print entire strings:

```c
void print_string_with_putchar(const char *str) {
    while (*str != '\0') {
        putchar(*str);
        str++;
    }
}
```

Or using array notation:

```c
const char *message = "Hello world";
for (int i = 0; message[i] != '\0'; i++) {
    putchar(message[i]);
}
```

**Advantages of using putchar for strings**:

1. Complete control over each character
2. Ability to process each character during printing
3. Efficient when combined with other character-level operations

## Input Functions

### gets (DEPRECATED)

- **Purpose**: Reads a line from stdin until newline/EOF
- **Syntax**: `gets(buffer);`
- **Features**:
    - No buffer size checking - DANGEROUS!
    - Prone to buffer overflow attacks
    - Deprecated in modern C - avoid using
- **Example**: `gets(name);`

### scanf

- **Purpose**: Reads formatted input from stdin
- **Syntax**: `scanf(format_string, &var1, &var2, ...)`
- **Features**:
    - Uses format specifiers like %s for strings
    - Stops reading at whitespace for %s
    - Limited buffer overflow protection unless field width is specified
- **Example**: `scanf("%s %d", name, &age);`

### getchar

- **Purpose**: Reads a single character from stdin
- **Syntax**: `c = getchar();`
- **Features**:
    - Returns the ASCII value of the character read (as int)
    - Returns EOF when reaching the end of input
    - Found in stdio.h
- **Example**: `int c = getchar();`

#### Using getchar to read strings

You can use getchar in a loop to read entire strings:

```c
char string[100];
int c;
int i = 0;

while ((c = getchar()) != '\n' && c != EOF && i < 99) {
    string[i++] = c;
}
string[i] = '\0';  // Add string terminator
```

## Understanding EOF (End Of File)

- **Definition**: EOF stands for "End Of File" - a constant defined in stdio.h
- **Value**: Usually -1 in most C systems
- **Purpose**: Indicates that a read operation has reached the end of the file or input stream
- **Usage**: Used with input functions like getchar(), fgetc(), fscanf()

**When you encounter EOF**:

1. When reading a file: When you reach the end of the file
2. When reading from keyboard: When the user enters a special key combination:
    - Windows: `Ctrl+Z` followed by `Enter`
    - Unix/Linux: `Ctrl+D`

**Example of using EOF**:

```c
int c;
while ((c = getchar()) != EOF) {
    putchar(c);  // Echo back the input
}
```

**Note**: Always use an `int` variable (not `char`) to store getchar() results because:

1. getchar() returns an int
2. We need to distinguish between EOF (-1) and regular characters
3. A char variable may not be able to differentiate EOF from some characters

## Improving Input Safety

Instead of gets, use these safer alternatives:

- `fgets(buffer, size, stdin)` - reads with size limit
    - Example: `fgets(name, 50, stdin);`
    - Keeps the newline character \n in the string

For safer scanf usage:

- Always specify maximum field width: `scanf("%99s", buffer)`
- Check return values to verify successful input
- Consider combining with fgets for line-based input
- Use `%[^\n]` to read a whole line including spaces: `scanf("%99[^\n]", buffer);`

## Practical Examples

### Safe input handling:

```c
#include <stdio.h>
#include <string.h>

int main() {
    char name[50];
    int age;
    
    // Safe example using fgets
    printf("Enter your name: ");
    fgets(name, sizeof(name), stdin);
    // Remove the newline character
    name[strcspn(name, "\n")] = '\0';
    
    // Safe example using scanf with width limiter
    printf("Enter your age: ");
    scanf("%2d", &age);
    
    // Output using printf
    printf("Hello %s, you are %d years old\n", name, age);
    
    return 0;
}
```

### String character conversion:

```c
#include <stdio.h>
#include <ctype.h>

int main() {
    int c;
    
    printf("Enter text (will be converted to uppercase):\n");
    
    while ((c = getchar()) != '\n' && c != EOF) {
        putchar(toupper(c));
    }
    
    return 0;
}
```

### Clearing the input buffer:

```c
void clear_input_buffer() {
    int c;
    while ((c = getchar()) != '\n' && c != EOF);
}
```

### Reading a file character by character:

```c
#include <stdio.h>

int main() {
    FILE *file;
    int c;
    
    file = fopen("example.txt", "r");
    if (file == NULL) {
        printf("Cannot open file!\n");
        return 1;
    }
    
    while ((c = fgetc(file)) != EOF) {
        putchar(c);
    }
    
    fclose(file);
    return 0;
}
```

## Best Practices

1. **Always check buffer limits** when reading strings
2. **Never use gets()** - it's unsafe and deprecated
3. **Always use field width limiters** with scanf string inputs
4. **Check return values** of input functions to verify success
5. **Use int (not char)** for storing getchar() results
6. **Clear input buffer** after using scanf to prevent unexpected behavior
7. For general-purpose, safe string input, **prefer fgets** over other methods

#strings
